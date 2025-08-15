---
title: Sichern und Rollback von Dateisystem, Medien und Datenbank
description: Führen Sie diese Schritte aus, um Ihre Adobe Commerce-Anwendung zu sichern und wiederherzustellen.
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Sichern und Rollback von Dateisystem, Medien und Datenbank

Mit diesem Befehl können Sie Folgendes sichern:

* Das Dateisystem (ohne `var`- und `pub/static`)
* Das `pub/media`
* Die Datenbank

Backups werden im `var/backups` Verzeichnis gespeichert und können jederzeit mit dem Befehl [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) wiederhergestellt werden.

Nach dem Sichern können Sie später [Rollback](#rollback).

>[!TIP]
>
>Informationen zu Adobe Commerce in Cloud-Infrastrukturprojekten finden Sie unter [Snapshots und Backup](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) im _Cloud-Handbuch_.

## Aktivieren von Backups

Die Sicherungsfunktion ist standardmäßig deaktiviert. Geben Sie zum Aktivieren den folgenden CLI-Befehl ein:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Hinweis zu veralteten Versionen:**
>&#x200B;>Die Backup-Funktion ist seit 2.1.16, 2.2.7 und 2.3.0 veraltet. Wir empfehlen, zusätzliche Backup-Technologien und binäre Backup-Tools (wie Percona XtraBackup) zu untersuchen.

## Festlegen des Limits für geöffnete Dateien

Ein Rollback zu einem vorherigen Backup kann im Hintergrund fehlschlagen, was dazu führt, dass mit dem [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files)-Befehl unvollständige Daten in das Dateisystem oder die Datenbank geschrieben werden.

Manchmal führt eine lange Abfragezeichenfolge dazu, dass dem zugewiesenen Speicherplatz des Benutzers aufgrund zu vieler rekursiver Aufrufe der Speicher ausgeht.

## So legen Sie geöffnete Dateien `ulimit`

Es wird empfohlen, den [`ulimit`](https://ss64.com/bash/ulimit.html) „Offene Dateien“ für den Dateisystembenutzer auf einen Wert von `65536` oder mehr festzulegen.

Sie können dies entweder über die Befehlszeile oder eine dauerhafte Einstellung für den Benutzer festlegen, indem Sie sein Shell-Skript bearbeiten.

Wechseln Sie, bevor Sie fortfahren, zum [Dateisystembesitzer](../prerequisites/file-system/overview.md), falls Sie dies noch nicht getan haben.

Befehl:

```bash
ulimit -s 65536
```

Sie können dies bei Bedarf in einen größeren Wert ändern.

>[!NOTE]
>
>Die Syntax für offene Dateien `ulimit` hängt von der verwendeten UNIX-Shell ab. Die vorherige Einstellung sollte mit CentOS und Ubuntu mit der Bash-Shell funktionieren. Für macOS ist die richtige Einstellung jedoch `ulimit -S 65532`. Lesen Sie eine Manpage oder Betriebssystemreferenz, um weitere Informationen zu erhalten.

Um optional den Wert in der Bash-Shell des Benutzers festzulegen:

1. Wechseln Sie, falls noch nicht geschehen, zum [Dateisystembesitzer](../prerequisites/file-system/overview.md).
1. Öffnen Sie `/home/<username>/.bashrc` in einem Texteditor.
1. Fügen Sie die folgende Zeile hinzu:

   ```bash
   ulimit -s 65536
   ```

1. Speichern Sie Ihre Änderungen in `.bashrc` und beenden Sie den Texteditor.

>[!WARNING]
>
>Es wird empfohlen, in der [`pcre.recursion_limit`-Datei keinen Wert für ](https://www.php.net/manual/en/pcre.configuration.php)`php.ini` festzulegen, da dies zu unvollständigen Rollbacks ohne Fehlermeldung führen kann.

## Sichern

Befehlsverwendung:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

Der Befehl führt die folgenden Aufgaben aus:

1. Versetzt den Speicher in den Wartungsmodus.
1. Führt eine der folgenden Befehlsoptionen aus.

   | Option | Bedeutung | Name und Speicherort der Sicherungsdatei |
   |--- |--- |--- |
   | `--code` | Sichert das Dateisystem (ohne var- und pub/static-Verzeichnisse). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Sichern Sie das Pub/Media-Verzeichnis. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Sichern Sie die Datenbank. | `var/backups/<timestamp>/_db.sql` |

1. Entfernt den Speicher aus dem Wartungsmodus.

Um beispielsweise das Dateisystem und die Datenbank zu sichern,

```bash
bin/magento setup:backup --code --db
```

Meldungen ähnlich der folgenden werden angezeigt:

```
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## Rollback

In diesem Abschnitt wird beschrieben, wie Sie ein Backup wiederherstellen, das Sie zuvor erstellt haben. Sie müssen den Dateinamen der wiederherzustellenden Sicherungsdatei kennen.

Um den Namen Ihrer Backups zu finden, geben Sie Folgendes ein:

```bash
bin/magento info:backups:list
```

Die erste Zeichenfolge im Namen der Sicherungsdatei ist der Zeitstempel.

Um zu einer vorherigen Sicherung zurückzukehren, geben Sie Folgendes ein:

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

Um beispielsweise ein Medienbackup mit dem Namen `1440611839_filesystem_media.tgz` wiederherzustellen, geben Sie Folgendes ein

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Meldungen ähnlich der folgenden werden angezeigt:

```
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
