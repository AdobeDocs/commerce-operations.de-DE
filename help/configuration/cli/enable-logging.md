---
title: Protokollierung aktivieren
description: Erfahren Sie, wie Sie Protokollierungstypen aktivieren und deaktivieren.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Protokollierung aktivieren

{{file-system-owner}}

## Debug-Protokollierung

Standardmäßig schreibt Commerce in das Debug-Protokoll (`<install_directory>/var/log/debug.log`), wenn sie sich im Standard- oder Entwicklungsmodus befindet, jedoch nicht, wenn sie sich im Produktionsmodus befindet. Verwenden Sie die `bin/magento setup:config:set --enable-debug-logging` -Befehl, um den Standardwert zu ändern.

>[!INFO]
>
>Ab Commerce 2.3.1 können Sie die `bin/magento config:set dev/debug/debug_logging` -Befehl zum Aktivieren oder Deaktivieren der Debug-Protokollierung für den aktuellen Modus.

### So aktivieren Sie die Debug-Protokollierung

1. Verwenden Sie die `setup:config:set` -Befehl, um die Debug-Protokollierung für den aktuellen Modus zu aktivieren.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```

### So deaktivieren Sie die Debug-Protokollierung

1. Verwenden Sie die `setup:config:set` -Befehl, um die Debug-Protokollierung für den aktuellen Modus zu deaktivieren.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```

## Datenbankprotokollierung

Standardmäßig schreibt Commerce die Aktivitätsprotokolle der Datenbank in die `<install-dir>/var/debug/db.log` -Datei.

### Aktivieren der Datenbankprotokollierung

1. Verwenden Sie die `dev:query-log` -Befehl zum Aktivieren oder Deaktivieren der Datenbankprotokollierung.

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```

## Cron-Protokollierung

Mit Version 2.3.1 erstellt Commerce jetzt eine separate `cron` log. \
Der Handel hat die Cron-Protokollierung vor kurzem ausführlicher gestaltet, was zwar mehr Informationen lieferte, aber die `system.log` beträchtlich.
Verschieben `cron` Informationen in ein dediziertes Protokoll vereinfachen das Lesen beider Protokolle.

Standardmäßig schreibt Commerce `cron` Informationen zum `<install-directory>/var/log/cron.log` -Datei.

## Syslog-Protokollierung

Standardmäßig schreibt Commerce _syslog_ Protokolle zum Betriebssystem `syslog` -Datei.
Ab Commerce 2.3.1 müssen Sie die `magento` -Befehl, um das syslog zu aktivieren oder zu deaktivieren.
Die Einstellung in Admin wurde entfernt.

### Aktivieren der syslog-Protokollierung

Protokollierung in `syslog` ist standardmäßig deaktiviert.

1. Verwenden Sie die `setup:config:set` -Befehl zum Ändern der `dev/syslog/syslog_logging` Datenbankwert zu `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```

### So deaktivieren Sie die syslog-Protokollierung

1. Verwenden Sie die `setup:config:set` -Befehl zum Ändern der `dev/syslog/syslog_logging` Datenbankwert zu `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```
