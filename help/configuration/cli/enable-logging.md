---
title: Protokollierung aktivieren
description: Erfahren Sie, wie Sie Protokollierungstypen aktivieren und deaktivieren.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 0%

---

# Protokollierung aktivieren

{{file-system-owner}}

## Debug-Protokollierung

Standardmäßig schreibt Commerce in das Debug-Protokoll (`<install_directory>/var/log/debug.log`), wenn es sich im Standard- oder Entwicklungsmodus befindet, jedoch nicht, wenn es sich im Produktionsmodus befindet. Verwenden Sie den Befehl `bin/magento setup:config:set --enable-debug-logging` , um den Standardwert zu ändern.

>[!INFO]
>
>Ab Commerce 2.3.1 können Sie den Befehl `bin/magento config:set dev/debug/debug_logging` nicht mehr verwenden, um die Debug-Protokollierung für den aktuellen Modus zu aktivieren oder zu deaktivieren.

### So aktivieren Sie die Debug-Protokollierung

1. Verwenden Sie den Befehl `setup:config:set` , um die Debug-Protokollierung für den aktuellen Modus zu aktivieren.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```

### So deaktivieren Sie die Debug-Protokollierung

1. Verwenden Sie den Befehl `setup:config:set` , um die Debug-Protokollierung für den aktuellen Modus zu deaktivieren.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```

## Datenbankprotokollierung

Standardmäßig schreibt Commerce Datenbankaktivitätsprotokolle in die Datei &quot;`<install-dir>/var/debug/db.log`&quot;.

### Aktivieren der Datenbankprotokollierung

1. Verwenden Sie den Befehl `dev:query-log` , um die Datenbankprotokollierung zu aktivieren oder zu deaktivieren.

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

Mit Version 2.3.1 erstellt Commerce jetzt ein separates `cron` -Protokoll. \
Commerce hat die Cron-Protokollierung vor kurzem ausführlicher gestaltet, wodurch zwar mehr Informationen bereitgestellt, die `system.log` jedoch erheblich verlängert wurde.
Das Verschieben von `cron` -Informationen in ein dediziertes Protokoll erleichtert das Lesen beider Protokolle.

Standardmäßig schreibt Commerce `cron` -Informationen in die Datei `<install-directory>/var/log/cron.log`.

## Syslog-Protokollierung

Standardmäßig schreibt Commerce _syslog_-Protokolle in die Betriebssystemdatei `syslog`.
Ab Commerce 2.3.1 müssen Sie den Befehl `magento` verwenden, um das syslog zu aktivieren oder zu deaktivieren.
Die Einstellung in Admin wurde entfernt.

### Aktivieren der syslog-Protokollierung

Die Protokollierung bei `syslog` ist standardmäßig deaktiviert.

1. Verwenden Sie den Befehl `setup:config:set` , um den Datenbankwert `dev/syslog/syslog_logging` in `true` zu ändern.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```

### So deaktivieren Sie die syslog-Protokollierung

1. Verwenden Sie den Befehl `setup:config:set` , um den Datenbankwert `dev/syslog/syslog_logging` in `false` zu ändern.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```
