---
title: Remote Storage konfigurieren
description: Erfahren Sie, wie Sie das Remote-Speichermodul für die lokale Commerce-Anwendung konfigurieren.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 419a21604d1fda0a76dd0375ae2340fd6e59ec89
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Remote Storage konfigurieren

Das Remote-Speichermodul bietet die Möglichkeit, Mediendateien zu speichern und Importe und Exporte mithilfe eines Speicherdienstes wie AWS S3 in einem beständigen Remote-Speicher-Container zu planen.

Standardmäßig speichert die Adobe Commerce-Anwendung Mediendateien im selben Dateisystem, das die Anwendung enthält. Dies ist bei komplexen Konfigurationen mit mehreren Servern ineffizient und kann bei der Freigabe von Ressourcen zu einer beeinträchtigten Leistung führen. Mit dem Remote-Speichermodul können Sie Mediendateien im Ordner &quot;`pub/media`&quot;speichern und Dateien im Ordner &quot;`var`&quot;des Remote-Objektspeichers importieren/exportieren, um von der serverseitigen Bildgröße zu profitieren.

>[!BEGINSHADEBOX]

Der Remote-Speicher _und_ der Datenbank können nicht gleichzeitig aktiviert werden. Sie müssen den Datenbankspeicher deaktivieren, bevor Sie den Remote-Speicher aktivieren.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Die Aktivierung des Remote-Speichers kann sich auf Ihr bestehendes Entwicklungs-Erlebnis auswirken. Beispielsweise funktionieren bestimmte PHP-Dateifunktionen möglicherweise nicht erwartungsgemäß. Die Verwendung von Commerce Framework für Dateivorgänge muss erzwungen werden. Die Liste der unzulässigen nativen PHP-Funktionen ist im Repository [magento-coding-standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php) verfügbar.

>[!ENDSHADEBOX]

>[!INFO]
>
>- Remote-Speicher ist nur für Commerce Version 2.4.2 und höher verfügbar. Siehe Versionshinweise zu [2.4.2](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/magento-open-source/2-4-2).
>
>- Das Remote-Speichermodul bietet in Adobe Commerce in der Cloud-Infrastruktur _begrenzte_ Unterstützung. Adobe kann keine vollständige Fehlerbehebung für den Speicheradapterdienst von Drittanbietern durchführen. Eine Anleitung zur Implementierung von Remote-Speicher für Cloud-Projekte finden Sie unter [Konfigurieren von Remote-Speicher für Commerce in Cloud-Infrastruktur](cloud-support.md) .

![Schemabild](../../assets/configuration/remote-storage-schema.png)

## Remote-Speicheroptionen

Sie können den Remote-Speicher mit der Option `remote-storage` mit dem Befehl [`setup` CLI command](../../installation/tutorials/deployment.md) konfigurieren. Die Option `remote-storage` verwendet die folgende Syntax:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

Der `parameter-name` bezieht sich auf den Namen des spezifischen Remote-Speicherparameters. In der folgenden Tabelle sind die Parameter aufgeführt, die für die Konfiguration des Remote-Speichers verfügbar sind:

| Befehlszeilenparameter | Parametername | Beschreibung | Standardwert |
|--- |--- |--- |--- |
| `remote-storage-driver` | Treiber | Adaptername<br>Mögliche Werte:<br>**file**: Deaktiviert den Remote-Speicher und verwendet das lokale Dateisystem <br>**aws-s3**: Verwenden Sie den [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | Keine |
| `remote-storage-bucket` | Bucket | Objektspeicherung oder Containername | Keine |
| `remote-storage-prefix` | prefix | Optionales Präfix (Speicherort innerhalb des Objektspeichers) | leer |
| `remote-storage-region` | region | Regionsname | Keine |
| `remote-storage-key` | Zugriffsschlüssel | Optionaler Zugriffsschlüssel | leer |
| `remote-storage-secret` | geheimer Schlüssel | Optionaler geheimer Schlüssel | leer |

### Speicheradapter

Der standardmäßige Speicherort befindet sich im lokalen Dateisystem. Mit einem _Speicheradapter_ können Sie eine Verbindung zu einem Speicherdienst herstellen und Ihre Dateien an einer beliebigen Stelle speichern. [!DNL Commerce] unterstützt die Konfiguration der folgenden Speicherdienste:

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Remote-Speicher aktivieren

Sie können den Remote-Speicher während einer Adobe Commerce-Installation installieren oder einer bestehenden Commerce-Instanz Remote-Speicher hinzufügen. In den folgenden Beispielen werden die einzelnen Methoden anhand eines Satzes von `remote-storage` Parametern mit Commerce `setup`-CLI-Befehlen veranschaulicht. Minimal müssen Sie den Speicher `driver`, `bucket` und `region` bereitstellen.

- Beispiel: Installieren von Commerce mit Remote-Speicher

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- Beispiel: Remote-Speicher auf vorhandenem Commerce aktivieren

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>Informationen zu Adobe Commerce in der Cloud-Infrastruktur finden Sie unter [Konfigurieren des Remote-Speichers für Commerce in der Cloud-Infrastruktur](cloud-support.md).

## Migrieren von Inhalten

Nachdem Sie den Remote-Speicher für einen bestimmten Adapter aktiviert haben, können Sie mithilfe der CLI vorhandene _media_-Dateien in den Remote-Speicher migrieren.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Der Synchronisierungsbefehl migriert nur Dateien im Ordner `pub/media`, nicht jedoch die Import-/Exportdateien im Verzeichnis `var`. __ Siehe [Geplanter Import/Export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html) im _Commerce 2.4-Benutzerhandbuch_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
