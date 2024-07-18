---
title: Führen Sie die Hilfsprogramme aus
description: Fehlerbehebung für Ihr Commerce-Projekt mithilfe des integrierten Support-Dienstprogramms.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Führen Sie die Hilfsprogramme aus

{{ee-only}}

{{file-system-owner}}

Die Adobe Commerce-Support-Dienstprogramme - auch als [Datenerfassung](https://docs.magento.com/user-guide/system/support-data-collector.html) bezeichnet - ermöglichen es Benutzern, Informationen zur Fehlerbehebung zu Ihrem System zu erfassen, die von unserem Supportteam verwendet werden können.

Adobe Commerce verwendet diese Sicherungen, auch _Dumps_ genannt, um Probleme zu analysieren, die Zugriff auf Ihren Code erfordern. Ein typisches Szenario sieht wie folgt aus:

1. Sie haben ein Problem mit Ihrem Commerce-Store und wenden sich an den Adobe Commerce-Support.
1. Der Support legt fest, dass er Ihren Code oder Ihre Datenbank sehen muss, um das Problem zu reproduzieren.
1. Sie sichern den Code in einer `.tar.gz` -Datei.

   Dieses Backup_schließt Ihre Mediendateien aus, um den Prozess zu beschleunigen und zu einer wesentlich kleineren Datei zu führen.

1. Sie sichern die Datenbank in einer `.tar.gz` -Datei.

   Standardmäßig werden vertrauliche Daten beim Erstellen der Sicherung gehasht.

1. Sie laden Ihre Sicherungen in einen Dateifreigabedienst hoch.
1. Der Support analysiert Ihre Probleme, ohne dass sich dies auf Ihre Entwicklungs- oder Produktionsumgebung auswirkt.

Die Ausführung der Dienstprogramme kann mehrere Minuten dauern.

## Codesicherung erstellen

Dieser Befehl sichert den Code und komprimiert ihn im Format `tar.gz`.

{{tip-backup-command}}

Befehlsoptionen:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Dabei gilt:

- **`--name`** gibt den Dateinamen der Dump-Datei an (optional). Wenn Sie diesen Parameter weglassen, wird die Dump-Datei mit dem Zeitstempel und dem Datumsstempel versehen.
- **`-o|--output=<path>`** ist der absolute Dateisystempfad zum Speichern der Sicherung (erforderlich).
- **`-l|--logs`** enthält Protokolldateien (optional).

So erstellen Sie beispielsweise eine Codesicherung mit dem Namen `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Stellen Sie nach Abschluss des Befehls die Codesicherung für den Adobe Commerce-Support bereit.

## Datenbanksicherung erstellen

Mit diesem Befehl wird die Commerce-Datenbank gesichert und im `tar.gz`-Format komprimiert.

{{tip-backup-command}}

Befehlsoptionen:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Dabei gilt:

- **`--name`** gibt den Dateinamen der Dump-Datei an (optional). Wenn Sie diesen Parameter weglassen, wird die Dump-Datei mit dem Zeitstempel und dem Datumsstempel versehen.
- **`-o|--output=<path>` ist der absolute Dateisystempfad zum Speichern der Sicherung (erforderlich).
- **`-l|--logs`** enthält Protokolldateien (optional).
- **`-i|--ignore-sanitize`** bedeutet, dass Daten beibehalten werden. Lassen Sie die Markierung weg, um beim Erstellen der Sicherung gespeicherte vertrauliche Daten in der Datenbank zu hash-Daten zu speichern (optional).

Sensible Daten umfassen Kundeninformationen aus den folgenden Datenbanktabellen:

```
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

Stellen Sie nach Abschluss des Befehls die Datenbanksicherung für den Adobe Commerce-Support bereit.

## Fehlerbehebung: Anzeigeprogramme und Pfade

Wir stellen Befehle bereit, die Pfade zu Dienstprogrammen anzeigen, die für die Datenerfassung und die Befehlszeile erforderlich sind. Sie können diese Befehle beispielsweise verwenden, wenn Fehler wie die folgende in der Admin- oder Befehlszeile angezeigt werden:

```
Utility lsof not found
```

Führen Sie die folgenden Befehle in der angezeigten Reihenfolge aus, um die Pfade zu den von den Support-Dienstprogrammen und dem Data Collector verwendeten Anwendungen anzuzeigen:

1. Wechseln Sie zum Installationsverzeichnis von Commerce.

   Beispiel: `cd /var/www/magento2`

   >[!INFO]
   >
   >Die Befehle werden im Installationsverzeichnis ordnungsgemäß mit _nur_ ausgeführt.

1. `bin/magento support:utility:paths` erstellt `<magento_root>/var/support/Paths.php`, in dem die Pfade zu allen vom Dienstprogramm verwendeten Anwendungen aufgelistet werden.
1. `bin/magento support:utility:check` zeigt die Dateisystempfade an.

Ein Beispiel:

```
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

Um Probleme beim Ausführen der Tools zu beheben, stellen Sie sicher, dass diese Anwendungen installiert sind und sich in der Umgebungsvariablen &quot;`$PATH`&quot; des Webserver-Benutzers befinden.
