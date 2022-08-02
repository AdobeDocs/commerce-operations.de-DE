---
title: Remote Storage konfigurieren
description: Erfahren Sie, wie Sie das Remote-Speichermodul für die lokale Commerce-Anwendung konfigurieren.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Remote Storage konfigurieren

Das Remote-Speichermodul bietet die Möglichkeit, Mediendateien zu speichern und Importe/Exporte mithilfe eines Speicherdienstes wie AWS S3 in einem beständigen Remote-Speicher-Container zu planen. Standardmäßig wird die [!DNL Commerce] -Anwendung speichert Mediendateien im selben Dateisystem, das die Anwendung enthält. Dies ist bei komplexen Konfigurationen mit mehreren Servern ineffizient und kann bei der Freigabe von Ressourcen zu einer beeinträchtigten Leistung führen. Mit dem Remote Storage-Modul können Sie Mediendateien im `pub/media` Ordner- und Import-/Exportdateien im `var` Verzeichnis des Remote-Objektspeichers, um die serverseitige Bildgröße zu nutzen.

>[!INFO]
>
>Remote-Speicher ist nur in Version 2.4.2 und höher verfügbar. Siehe [2.4.2 - Versionshinweise](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-2.html).

>[!INFO]
>
>Das Remote-Speichermodul verfügt über _begrenzt_ Unterstützung von Adobe Commerce für Cloud-Infrastruktur. Adobe kann keine vollständige Fehlerbehebung beim Speicheradapterdienst von Drittanbietern durchführen.

![Schemabild](../../assets/configuration/remote-storage-schema.png)

## Remote-Speicheroptionen

Sie können den Remote-Speicher mit dem `remote-storage` mit der Option [`setup` CLI, Befehl][setup]. Die `remote-storage` -Option verwendet die folgende Syntax:

```text
--remote-storage-<parameter-name>="<parameter-value>"
```

Die `parameter-name` bezieht sich auf den spezifischen Parameternamen des Remote-Speichers. In der folgenden Tabelle sind die Parameter aufgeführt, die für die Konfiguration des Remote-Speichers verfügbar sind:

| Befehlszeilenparameter | Parametername | Beschreibung | Standardwert |
|--- |--- |--- |--- |
| `remote-storage-driver` | Treiber | Adaptername<br>Mögliche Werte:<br>**file**: Deaktiviert Remote-Speicher und verwendet das lokale Dateisystem <br>**aws-s3**: Verwenden Sie die [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md) | Keine |
| `remote-storage-bucket` | Behälter | Objektspeicherung oder Containername | Keine |
| `remote-storage-prefix` | prefix | Optionales Präfix (Speicherort innerhalb des Objektspeichers) | leer |
| `remote-storage-region` | region | Regionsname | Keine |
| `remote-storage-key` | Zugriffsschlüssel | Optionaler Zugriffsschlüssel | leer |
| `remote-storage-secret` | geheimer Schlüssel | Optionaler geheimer Schlüssel | leer |

### Speicheradapter

Der standardmäßige Speicherort befindet sich im lokalen Dateisystem. A _Speicheradapter_ ermöglicht Ihnen, eine Verbindung zu einem Speicherdienst herzustellen und Ihre Dateien überall zu speichern. [!DNL Commerce] unterstützt die Konfiguration der folgenden Speicherdienste:

- [Amazon Simple Storage Service (Amazon S3)](remote-storage-aws-s3.md)

## Remote-Speicher aktivieren

Sie können den Remote-Speicher während einer neuen [!DNL Commerce] Installation oder Hinzufügen zu einer vorhandenen Commerce-Instanz mithilfe von `remote-storage` Name-Wert-Paare von Parametern mit `setup` CLI-Befehle. Minimal müssen Sie den Speicher bereitstellen `driver`, `bucket`und `region`.

Die folgenden Beispiele ermöglichen den Remote-Speicher mit einem AWS S3-Speicheradapter in den USA:

- Neu installieren [!DNL Commerce] mit Remote-Speicher

   ```bash
   bin/magento setup:install --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

- Remote-Speicher auf bereits vorhandene aktivieren [!DNL Commerce]

   ```bash
   bin/magento setup:config:set --remote-storage-driver="aws-s3" --remote-storage-bucket="myBucket" --remote-storage-region="us-east-1"
   ```

## Einschränkungen

Sie können nicht gleichzeitig sowohl Remote-Speicher als auch Datenbankspeicher aktivieren. Deaktivieren Sie den Datenbankspeicher, wenn Sie Remote-Speicher verwenden.

```bash
bin/magento config:set system/media_storage_configuration/media_database 0
```

Die Aktivierung des Remote-Speichers kann sich auf Ihr bestehendes Entwicklungs-Erlebnis auswirken. Beispielsweise funktionieren bestimmte PHP-Dateifunktionen möglicherweise nicht erwartungsgemäß. Die Verwendung von Commerce Framework für Dateivorgänge muss erzwungen werden.

Die Liste der verbotenen nativen PHP-Funktionen ist in verfügbar. [Magento Coding Standard] Repository.

## Migrieren von Inhalten

Nachdem Sie den Remote-Speicher für einen bestimmten Adapter aktiviert haben, können Sie die CLI verwenden, um vorhandene _media_ Dateien in den Remote-Speicher.

```bash
./magento2ce/bin/magento remote-storage:sync
```

>[!INFO]
>
>Der Synchronisierungsbefehl migriert nur Dateien im `pub/media` Verzeichnis, _not_ die Import-/Exportdateien im `var` Verzeichnis. Siehe [Geplanter Import/Export][import-export] im _Benutzerhandbuch für Commerce 2.4_.

<!-- link definitions -->

[import-export]: https://docs.magento.com/user-guide/system/data-scheduled-import-export.html
[nginx-module]: http://nginx.org/en/docs/http/ngx_http_image_filter_module.html
[Magento Coding Standard]: https://github.com/magento/magento-coding-standard/blob/develop/Magento2/Sniffs/Functions/DiscouragedFunctionSniff.php
[setup]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html#instgde-cli-subcommands-configphp
