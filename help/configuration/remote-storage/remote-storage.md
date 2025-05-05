---
title: Konfigurieren des Remote-Speichers
description: Erfahren Sie, wie Sie das Remote-Speichermodul für die lokale Commerce-Anwendung konfigurieren.
feature: Configuration, Storage
exl-id: 0428f889-46b0-44c9-8bd9-98c1be797011
source-git-commit: 419a21604d1fda0a76dd0375ae2340fd6e59ec89
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Konfigurieren des Remote-Speichers

Das Remote-Speichermodul bietet die Möglichkeit, Mediendateien zu speichern und Importe und Exporte in einem persistenten Remote-Speicher-Container mithilfe eines Speicher-Services wie AWS S3 zu planen.

Standardmäßig speichert die Adobe Commerce-Anwendung Mediendateien im selben Dateisystem, das die Anwendung enthält. Dies ist für komplexe Multi-Server-Konfigurationen ineffizient und kann bei der gemeinsamen Nutzung von Ressourcen zu Leistungseinbußen führen. Mit dem Remote-Speichermodul können Sie Mediendateien im `pub/media`-Verzeichnis speichern und Dateien im `var`-Verzeichnis des Remote-Objektspeichers importieren/exportieren, um die Server-seitige Bildgrößenanpassung zu nutzen.

>[!BEGINSHADEBOX]

Sie können nicht gleichzeitig sowohl _- als auch_ aktivieren. Sie müssen den Datenbankspeicher deaktivieren, bevor Sie die Remote-Speicherung aktivieren.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Die Aktivierung von Remote-Speicher kann sich auf Ihre bestehende Entwicklungsumgebung auswirken. Beispielsweise funktionieren bestimmte PHP-Dateifunktionen möglicherweise nicht wie erwartet. Die Verwendung von Commerce Framework für Dateivorgänge muss erzwungen werden. Die Liste der unzulässigen nativen PHP-Funktionen ist im Repository [magento-coding-standard](https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php) verfügbar.

>[!ENDSHADEBOX]

>[!INFO]
>
>- Der Remote-Speicher ist nur für Commerce Version 2.4.2 und höher verfügbar. Siehe Versionshinweise zu [2.4.2](https://experienceleague.adobe.com/de/docs/commerce-operations/release/notes/magento-open-source/2-4-2).
>
>- Das Remote-Speichermodul bietet _(begrenzte_ Unterstützung für Adobe Commerce in Cloud-Infrastrukturen. Adobe kann den Speicheradapterdienst eines Drittanbieters nicht vollständig beheben. Siehe [Konfigurieren von Remote-Speicher für Commerce auf Cloud-](cloud-support.md)) für Anleitungen zur Implementierung von Remote-Speicher für Cloud-Projekte.

![Schemabild](../../assets/configuration/remote-storage-schema.png)

## Remote-Speicheroptionen

Sie können die Remote-Datenspeicherung mithilfe der `remote-storage`-Option mit dem [`setup` CLI-Befehl konfigurieren](../../installation/tutorials/deployment.md). Die Option `remote-storage` verwendet die folgende Syntax:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

Die `parameter-name` bezieht sich auf den spezifischen Namen des Remotespeicherparameters. In der folgenden Tabelle sind die Parameter aufgeführt, die für die Konfiguration des Remote-Speichers verfügbar sind:

| Befehlszeilenparameter | Parametername | Beschreibung | Standardwert |
|--- |--- |--- |--- |
| `remote-storage-driver` | Chauffeur | Adaptername<br>Mögliche Werte:<br>**file**: Deaktiviert den Remotespeicher und verwendet das lokale Dateisystem <br>**aws-s3**: Verwenden Sie den [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | Keine |
| `remote-storage-bucket` | Eimer | Objektspeicher- oder Container-Name | Keine |
| `remote-storage-prefix` | Vorsilbe | Optionales Präfix (Speicherort innerhalb des Objektspeichers) | leer |
| `remote-storage-region` | Region | Name der Region | Keine |
| `remote-storage-key` | Zugriffsschlüssel | Optionaler Zugriffsschlüssel | leer |
| `remote-storage-secret` | Geheimer Schlüssel | Optionaler geheimer Schlüssel | leer |

### Speicheradapter

Der standardmäßige Speicherort befindet sich im lokalen Dateisystem. Ein _Speicheradapter_ ermöglicht Ihnen, eine Verbindung zu einem Speicherdienst herzustellen und Ihre Dateien überall zu speichern. [!DNL Commerce] unterstützt die Konfiguration der folgenden Speicher-Services:

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Remote-Speicherung aktivieren

Sie können während einer Adobe Commerce-Installation Remote-Speicher installieren oder Remote-Speicher zu einer bestehenden Commerce-Instanz hinzufügen. In den folgenden Beispielen wird jede Methode mit einem Satz `remote-storage` Parametern mit Commerce `setup` CLI-Befehlen veranschaulicht. Sie müssen mindestens die `driver`, `bucket` und `region` bereitstellen.

- Beispiel: Installieren von Commerce mit Remote-Speicher

  ```bash
  bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

- Beispiel: Aktivieren von Remote-Speicher auf vorhandenem Commerce

  ```bash
  bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
  ```

>[!TIP]
>
>Informationen zu Adobe Commerce in Cloud-Infrastrukturen finden Sie unter [Konfigurieren von Remote-Speicher für Commerce in Cloud-Infrastrukturen](cloud-support.md).

## Migrieren von Inhalten

Nachdem Sie den Remotespeicher für einen bestimmten Adapter aktiviert haben, können Sie über die CLI vorhandene _media_-Dateien zum Remotespeicher migrieren.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Mit dem Befehl „sync“ werden nur Dateien im `pub/media`-Verzeichnis migriert _nicht_ Import/Export-Dateien im `var`-Verzeichnis. Siehe [Geplanter Import/Export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-scheduled-import-export.html?lang=de) im _Benutzerhandbuch zu Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
