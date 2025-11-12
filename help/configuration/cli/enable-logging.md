---
title: Protokollierung aktivieren
description: Erfahren Sie, wie Sie verschiedene Arten der Protokollierung in Adobe Commerce aktivieren und deaktivieren. Entdecken Sie Protokollierungskonfigurations- und -verwaltungsmethoden.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: aff705cefcd4de38d17cad41628bc8dbd6d630cb
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Protokollierung aktivieren

{{file-system-owner}}

## Debug-Protokollierung

Standardmäßig schreibt Commerce in das Debug-Protokoll (`<install_directory>/var/log/debug.log`), wenn es sich im Standard- oder Entwicklungsmodus befindet, aber nicht, wenn es sich im Produktionsmodus befindet. Mit dem Befehl `bin/magento setup:config:set --enable-debug-logging` können Sie den Standardwert ändern.

>[!INFO]
>
>Ab Commerce 2.3.1 können Sie den Befehl `bin/magento config:set dev/debug/debug_logging` nicht mehr verwenden, um die Debugging-Protokollierung für den aktuellen Modus zu aktivieren oder zu deaktivieren.

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

Standardmäßig schreibt Commerce Datenbankaktivitätsprotokolle in die `<install-dir>/var/debug/db.log`.

### Speicherort der Abfrageprotokollierung

Wenn die Datenbankprotokollierung aktiviert ist, speichert Commerce Abfrageprotokolle am folgenden Speicherort:

- **Abfrageprotokolldatei**: `<install-directory>/var/debug/db.log`
- **Protokollordner**: `<install-directory>/var/debug/`

Das Abfrageprotokoll enthält:
- Von der Anwendung ausgeführte SQL-Abfragen
- Ausführungszeiten der Abfrage
- Abfrageparameter und Bindungen
- Informationen zur Datenbankverbindung

>[!NOTE]
>
>Die Abfrageprotokolldatei kann in Umgebungen mit hohem Traffic schnell groß werden. Überwachen Sie den Speicherplatz und erwägen Sie die Implementierung einer Protokollrotation oder eine regelmäßige Bereinigung der Abfrageprotokolldatei.

### So aktivieren Sie die Datenbankprotokollierung

1. Verwenden Sie den `dev:query-log`-Befehl, um die Datenbankprotokollierung zu aktivieren oder zu deaktivieren.

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

### So zeigen Sie Abfrageprotokolle an

Sie können die Abfrageprotokolle mit Standardbefehlen zur Dateianzeige anzeigen:

```bash
# View the entire query log
cat var/debug/db.log

# View the last 100 lines of the query log
tail -n 100 var/debug/db.log

# Monitor the query log in real-time
tail -f var/debug/db.log

# Search for specific queries
grep "SELECT" var/debug/db.log
```

## Cron-Protokollierung

Mit Version 2.3.1 erstellt Commerce jetzt ein separates `cron`. \
Commerce hat kürzlich die Cron-Protokollierung ausführlicher gemacht, was mehr Informationen lieferte, aber die `system.log` erheblich verlängerte.
Das Verschieben `cron` Informationen in ein dediziertes Protokoll erleichtert die Lesbarkeit beider Protokolle.

Standardmäßig schreibt Commerce `cron` Informationen in die `<install-directory>/var/log/cron.log`.

## Syslog-Protokollierung

Standardmäßig schreibt Commerce _syslog_-Protokolle in die `syslog`.
Ab Commerce 2.3.1 müssen Sie den Befehl `magento` verwenden, um syslog zu aktivieren oder zu deaktivieren.
Die Einstellung in „Admin“ wurde entfernt.

### So aktivieren Sie die Syslog-Protokollierung

Die Protokollierung in `syslog` ist standardmäßig deaktiviert.

1. Ändern Sie mit dem Befehl `setup:config:set` den `dev/syslog/syslog_logging` Datenbankwert in `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```

### So deaktivieren Sie die Syslog-Protokollierung

1. Ändern Sie mit dem Befehl `setup:config:set` den `dev/syslog/syslog_logging` Datenbankwert in `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Leeren Sie den Cache.

   ```bash
   bin/magento cache:flush
   ```
