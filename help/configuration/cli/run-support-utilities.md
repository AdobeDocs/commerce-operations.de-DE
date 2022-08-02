---
title: Führen Sie die Hilfsprogramme aus
description: Fehlerbehebung für Ihr Commerce-Projekt mithilfe des integrierten Support-Dienstprogramms.
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Führen Sie die Hilfsprogramme aus

{{ee-only}}

{{file-system-owner}}

Die Adobe Commerce-Support-Dienstprogramme, auch als [Datenerfassung](https://docs.magento.com/user-guide/system/support-data-collector.html)- Benutzern die Möglichkeit geben, Informationen zur Fehlerbehebung über Ihr System zu sammeln, die von unserem Support-Team verwendet werden können.

Adobe Commerce verwendet diese Sicherungen, auch als _Dumps_, um Probleme zu analysieren, die Zugriff auf Ihren Code erfordern. Ein typisches Szenario sieht wie folgt aus:

1. Sie haben ein Problem mit Ihrem Commerce-Store und wenden sich an den Adobe Commerce-Support.
1. Der Support legt fest, dass er Ihren Code oder Ihre Datenbank sehen muss, um das Problem zu reproduzieren.
1. Sie sichern den Code in einem `.tar.gz` -Datei.

   Dieses Backup_schließt Ihre Mediendateien aus, um den Prozess zu beschleunigen und zu einer wesentlich kleineren Datei zu führen.

1. Sie sichern die Datenbank in einem `.tar.gz` -Datei.

   Standardmäßig werden vertrauliche Daten beim Erstellen der Sicherung gehasht.

1. Sie laden Ihre Sicherungen in einen Dateifreigabedienst hoch.
1. Der Support analysiert Ihre Probleme, ohne dass sich dies auf Ihre Entwicklungs- oder Produktionsumgebung auswirkt.

Die Ausführung der Dienstprogramme kann mehrere Minuten dauern.

## Codesicherung erstellen

Dieser Befehl sichert den Code und komprimiert ihn in `tar.gz` Format.

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

Dieser Befehl sichert die Commerce-Datenbank und komprimiert sie in `tar.gz` Format.

{{tip-backup-command}}

Befehlsoptionen:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Dabei gilt:

- **`--name`** gibt den Dateinamen der Dump-Datei an (optional). Wenn Sie diesen Parameter weglassen, wird die Dump-Datei mit dem Zeitstempel und dem Datumsstempel versehen.
- **`-o|--output=<path>` ist der absolute Dateisystempfad zum Speichern der Sicherung (erforderlich).
- **`-l|--logs`** enthält Protokolldateien (optional).
- **`-i|--ignore-sanitize`** bedeutet, dass Daten beibehalten werden; Setzen Sie das Flag beim Erstellen der Sicherung auf die in der Datenbank gespeicherten Hash-vertraulichen Daten (optional).

Sensible Daten umfassen Kundeninformationen aus den folgenden Datenbanktabellen:

```terminal
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

## Fehlerbehebung: Anzeigen von Dienstprogrammen und Pfaden

Wir stellen Befehle bereit, die Pfade zu Dienstprogrammen anzeigen, die für die Datenerfassung und die Befehlszeile erforderlich sind. Sie können diese Befehle beispielsweise verwenden, wenn Fehler wie die folgende in der Admin- oder Befehlszeile angezeigt werden:

```terminal
Utility lsof not found
```

Führen Sie die folgenden Befehle in der angezeigten Reihenfolge aus, um die Pfade zu den von den Support-Dienstprogrammen und dem Data Collector verwendeten Anwendungen anzuzeigen:

1. Wechseln Sie zum Installationsverzeichnis für Commerce.

   Beispiel: `cd /var/www/magento2`

   >[!INFO]
   >
   >Die Befehle werden ordnungsgemäß ausgeführt _only_ aus dem Installationsverzeichnis.

1. `bin/magento support:utility:paths` erstellt `<magento_root>/var/support/Paths.php`, der die Pfade zu allen vom Dienstprogramm verwendeten Anwendungen auflistet.
1. `bin/magento support:utility:check` zeigt die Dateisystempfade an.

Beispiel:

```terminal
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

Um Probleme bei der Ausführung der Tools zu beheben, stellen Sie sicher, dass diese Anwendungen installiert sind und sich in der `$PATH` Umgebungsvariable.
