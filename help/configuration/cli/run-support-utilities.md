---
title: Ausführen der Support-Dienstprogramme
description: Erfahren Sie, wie Sie Support-Dienstprogramme zur Fehlerbehebung in Ihrem Adobe Commerce-Projekt ausführen. Entdecken Sie integrierte Diagnose- und Support-Tools.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Ausführen der Support-Dienstprogramme

{{ee-only}}

{{file-system-owner}}

Mit den Adobe Commerce-Support-Dienstprogrammen (auch als [Datenerfassung](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/tools/support#data-collector) bezeichnet) können Benutzende Informationen zur Fehlerbehebung in Ihrem System sammeln, die von unserem Support-Team verwendet werden können.

Adobe Commerce verwendet diese Sicherungskopien, auch als &quot;_&quot; bezeichnet_, um Probleme zu analysieren, die Zugriff auf Ihren Code erfordern. Es folgt ein typisches Szenario:

1. Sie haben ein Problem mit Ihrem Commerce-Store und wenden sich an den Adobe Commerce-Support.
1. Der Support entscheidet, ob der Code oder die Datenbank angezeigt werden müssen, um das Problem zu reproduzieren.
1. Sie sichern den Code in einer `.tar.gz`.

   Durch dieses Backup werden Ihre Mediendateien _ausgeschlossen, um den Vorgang zu beschleunigen und eine wesentlich kleinere Datei zu erhalten.

1. Sie sichern die Datenbank in einer `.tar.gz`.

   Standardmäßig werden vertrauliche Daten bei der Sicherung in Hash-Werte umgewandelt.

1. Sie laden Ihre Backups in einen Dateifreigabedienst hoch.
1. Der Support analysiert Ihre Probleme, ohne Ihre Entwicklungs- oder Produktionsumgebung zu beeinträchtigen.

Es kann mehrere Minuten dauern, bis die Dienstprogramme abgeschlossen sind.

## Erstellen eines Code-Backups

Mit diesem Befehl wird Code gesichert und im `tar.gz` komprimiert.

{{tip-backup-command}}

Befehlsoptionen:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Dabei gilt:

- **`--name`** gibt den Namen der Dumpdatei an (optional). Wenn Sie diesen Parameter weglassen, wird die Dump-Datei mit einem Zeit- und Datumsstempel versehen.
- **`-o|--output=<path>`** ist der absolute Dateisystempfad zum Speichern des Backups (erforderlich).
- **`-l|--logs`** enthält Protokolldateien (optional).

So erstellen Sie beispielsweise eine Code-Sicherung mit dem Namen `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Stellen Sie nach Abschluss des Befehls den Code-Backup für den Adobe Commerce-Support bereit.

## Erstellen einer Datenbanksicherung

Mit diesem Befehl wird die Commerce-Datenbank gesichert und im `tar.gz` komprimiert.

{{tip-backup-command}}

Befehlsoptionen:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Dabei gilt:

- **`--name`** gibt den Namen der Dumpdatei an (optional). Wenn Sie diesen Parameter weglassen, wird die Dump-Datei mit einem Zeit- und Datumsstempel versehen.
- **`-o|--output=<path>` ist der absolute Dateisystempfad zum Speichern der Sicherung (erforderlich).
- **`-l|--logs`** enthält Protokolldateien (optional).
- **`-i|--ignore-sanitize`** bedeutet, dass die Daten beibehalten werden. Lassen Sie die Markierung weg, um sensible Daten, die in der Datenbank gespeichert sind, beim Erstellen des Backups zu hashen (optional).

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

## Fehlerbehebung: Anzeigen von Dienstprogrammen und Pfaden

Wir stellen Befehle bereit, die Pfade zu Dienstprogrammen anzeigen, die vom Data Collector und der Befehlszeile benötigt werden. Sie können diese Befehle beispielsweise verwenden, wenn Fehler wie die folgenden in der Admin oder in der Befehlszeile angezeigt werden:

```
Utility lsof not found
```

Führen Sie die folgenden Befehle in der angegebenen Reihenfolge aus, um die Pfade zu den Anwendungen anzuzeigen, die von den Support-Dienstprogrammen und der Datenerfassung verwendet werden:

1. Wechseln Sie in das Commerce-Installationsverzeichnis.

   Beispiel: `cd /var/www/magento2`

   >[!INFO]
   >
   >Die Befehle werden _ordnungsgemäß_ Ihrem Installationsverzeichnis ausgeführt.

1. `bin/magento support:utility:paths` erstellt `<magento_root>/var/support/Paths.php`, in dem die Pfade zu allen vom Dienstprogramm verwendeten Anwendungen aufgelistet werden.
1. `bin/magento support:utility:check` zeigt die Dateisystempfade an.

Es folgt ein Beispiel:

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

Um Probleme beim Ausführen der Tools zu beheben, stellen Sie sicher, dass diese Programme installiert sind und sich in der `$PATH`-Umgebungsvariablen des Webserverbenutzers befinden.
