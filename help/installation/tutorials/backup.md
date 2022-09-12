---
title: Backup und Rollback des Dateisystems, der Medien und der Datenbank
description: Führen Sie diese Schritte aus, um Ihre Adobe Commerce- oder Magento Open Source-Anwendung zu sichern und wiederherzustellen.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---


# Backup und Rollback des Dateisystems, der Medien und der Datenbank

Mit diesem Befehl können Sie Folgendes sichern:

* Dateisystem (außer `var` und `pub/static` Verzeichnissen)
* Die `pub/media` directory
* Die Datenbank

Backups werden im `var/backups` und kann jederzeit mithilfe der [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) Befehl.

Nach dem Sichern können Sie [Rollback](#rollback) später.

>[!TIP]
>
>Informationen zu Adobe Commerce zu Cloud-Infrastrukturprojekten finden Sie unter [Snapshots und Backup-Verwaltung](https://devdocs.magento.com/cloud/project/project-webint-snap.html) im _Cloud-Handbuch_.

## Sicherungen aktivieren

Die Sicherungsfunktion ist standardmäßig deaktiviert. Geben Sie zum Aktivieren den folgenden CLI-Befehl ein:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Hinweis zur Einstellung:**
>Die Sicherungsfunktion ist ab Version 2.1.16, 2.2.7 und 2.3.0 veraltet. Wir empfehlen, zusätzliche Sicherungstechnologien und Binär-Backup-Tools (wie Percona XtraBackup) zu untersuchen.

## Legen Sie die Grenze für geöffnete Dateien fest

Ein Rollback zu einer vorherigen Sicherung kann still fehlschlagen, was dazu führt, dass unvollständige Daten mithilfe der [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) Befehl.

Manchmal führt eine lange Abfragezeichenfolge dazu, dass der zugewiesene Arbeitsspeicher des Benutzers aufgrund zu vieler rekursiver Aufrufe nicht mehr genügend Arbeitsspeicher hat.

## Festlegen offener Dateien `ulimit`

Es wird empfohlen, die geöffneten Dateien festzulegen [`ulimit`](https://ss64.com/bash/ulimit.html) für den Dateisystembenutzer auf den Wert `65536` oder mehr.

Sie können dies entweder über die Befehlszeile tun oder durch Bearbeiten des Shell-Skripts zu einer dauerhaften Einstellung für den Benutzer machen.

Bevor Sie fortfahren, wechseln Sie zu [Dateisysteminhaber](../prerequisites/file-system/overview.md).

Befehl:

```bash
ulimit -s 65536
```

Sie können dies bei Bedarf in einen größeren Wert ändern.

>[!NOTE]
>
>Die Syntax für geöffnete Dateien `ulimit` hängt von der verwendeten UNIX-Shell ab. Die vorherige Einstellung sollte mit CentOS und Ubuntu mit der Bash-Shell funktionieren. Für macOS ist die richtige Einstellung jedoch `ulimit -S 65532`. Weitere Informationen finden Sie auf einer Manpage oder in der Betriebssystemreferenz.

So legen Sie optional den Wert in der Bash-Shell des Benutzers fest:

1. Wenn Sie dies noch nicht getan haben, wechseln Sie zum [Dateisysteminhaber](../prerequisites/file-system/overview.md).
1. Öffnen `/home/<username>/.bashrc` in einem Texteditor.
1. Fügen Sie die folgende Zeile hinzu:

   ```bash
   ulimit -s 65536
   ```

1. Speichern Sie Ihre Änderungen in `.bashrc` und beenden Sie den Texteditor.

>[!WARNING]
>
>Es wird empfohlen, die Festlegung eines Werts für [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) im `php.ini` -Datei, da dies zu unvollständigen Rollbacks ohne Fehlermeldung führen kann.

## Sichern

Befehlsverwendung:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

Der Befehl führt die folgenden Aufgaben aus:

1. Setzt den Speicher in den Wartungsmodus.
1. Führt eine der folgenden Befehlsoptionen aus.

   | Option | Bedeutung | Name und Speicherort der Sicherungsdatei |
   |--- |--- |--- |
   | `--code` | Sichert das Dateisystem (außer var- und pub/static-Verzeichnissen). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Sichern Sie das Verzeichnis &quot;pub/media&quot;. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Sichern Sie die Datenbank. | `var/backups/<timestamp>/_db.sql` |

1. Der Speicher wird aus dem Wartungsmodus entfernt.

Um beispielsweise das Dateisystem und die Datenbank zu sichern,

```bash
bin/magento setup:backup --code --db
```

Meldungen, die der folgenden Anzeige ähneln:

```terminal
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

In diesem Abschnitt wird beschrieben, wie Sie zu einem zuvor erstellten Backup zurückkehren. Sie müssen den Dateinamen der wiederherzustellenden Sicherungsdatei kennen.

Geben Sie Folgendes ein, um den Namen Ihrer Sicherungen zu ermitteln:

```bash
bin/magento info:backups:list
```

Die erste Zeichenfolge im Namen der Sicherungsdatei ist der Zeitstempel.

Um zu einer vorherigen Sicherung zurückzukehren, geben Sie Folgendes ein:

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

So stellen Sie beispielsweise eine Mediensicherung mit dem Namen `1440611839_filesystem_media.tgz`, eingeben

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Meldungen, die der folgenden Anzeige ähneln:

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
