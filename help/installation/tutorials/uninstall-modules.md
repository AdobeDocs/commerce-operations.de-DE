---
title: Module deinstallieren
description: Führen Sie die folgenden Schritte aus, um ein Adobe Commerce-Modul zu deinstallieren.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Module deinstallieren

In diesem Abschnitt wird beschrieben, wie Sie ein oder mehrere Module deinstallieren. Während der Deinstallation können Sie optional den Code der Module, das Datenbankschema und die Datenbankdaten entfernen. Sie können zuerst Sicherungskopien erstellen, damit Sie die Daten später wiederherstellen können.

Sie sollten ein Modul nur deinstallieren, wenn Sie sicher sind, dass Sie es nicht verwenden werden. Anstatt ein Modul zu deinstallieren, können Sie es deaktivieren, wie in [Module aktivieren oder deaktivieren](manage-modules.md) beschrieben.

>[!NOTE]
>
>Dieser Befehl prüft, ob nur in der `composer.json` deklarierte Abhängigkeiten vorhanden sind. Wenn Sie ein Modul deinstallieren, das _nicht_ in der `composer.json` definiert ist, wird das Modul mit diesem Befehl deinstalliert, ohne auf Abhängigkeiten zu prüfen. Dieser Befehl entfernt _jedoch_ den Code des Moduls aus dem Dateisystem. Sie müssen Dateisystem-Tools verwenden, um den Code des Moduls zu entfernen (z. B. `rm -rf <path to module>`). Alternativ können Sie Nicht-Composer[Module ](manage-modules.md)deaktivieren).

Befehlsverwendung:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Dabei gibt `{ModuleName}` den Modulnamen im `<VendorName>_<ModuleName>` an. Beispielsweise lautet der Name des Kundenmoduls `Magento_Customer`. Um eine Liste der Modulnamen zu erhalten, geben Sie `magento module:status` ein

Der Befehl zum Deinstallieren des Moduls führt die folgenden Aufgaben aus:

1. Überprüft, ob die angegebenen Module in der Code-Basis vorhanden sind und ob es sich um Pakete handelt, die vom Composer installiert werden.

   Dieser Befehl funktioniert _mit Modulen_ die als Composer-Pakete definiert sind.

1. Sucht mit anderen Modulen nach Abhängigkeiten und beendet den Befehl, wenn nicht erfüllte Abhängigkeiten vorliegen.

   Um dies zu umgehen, können Sie entweder alle Module gleichzeitig deinstallieren oder die abhängigen Module zuerst deinstallieren.

1. Fordert zur Bestätigung des Vorgangs auf.
1. Versetzt den Speicher in den Wartungsmodus.
1. Verarbeitet die folgenden Befehlsoptionen.

   | Option | Bedeutung | Name und Speicherort der Sicherungsdatei |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Sichert das Dateisystem (ohne `var`- und `pub/static`). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Sichert das Pub/Media-Verzeichnis. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Sichert die Datenbank | `var/backups/<timestamp>_db.gz` |

1. Wenn `--remove-data` angegeben ist, entfernen Sie das Datenbankschema und die Daten, die in den `Uninstall` des Moduls definiert sind.

   Ruft für jedes zu deinstallierende angegebene Modul die `uninstall`-Methode in ihrer `Uninstall` auf. Diese Klasse muss von [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php) erben.

1. Entfernt die angegebenen Module aus der `setup_module`.
1. Entfernt die angegebenen Module aus der Modulliste in der [Bereitstellungskonfiguration](../../configuration/reference/deployment-files.md).
1. Entfernt Code mithilfe von `composer remove` aus der Codebasis.

   >[!NOTE]
   >
   >Bei der Deinstallation eines Moduls _immer_ wird `composer remove` ausgeführt. Die Option `--remove-data` entfernt Datenbankdaten und Schemata, die durch die `Uninstall` des Moduls definiert sind.

1. Löscht den Cache.
1. Aktualisiert generierte Klassen.
1. Wenn `--clear-static-content` angegeben ist, bereinigt [generierte statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md).
1. Entfernt den Speicher aus dem Wartungsmodus.

Wenn Sie beispielsweise versuchen, ein Modul zu deinstallieren, von dem ein anderes Modul abhängig ist, wird die folgende Meldung angezeigt:

```
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Eine Alternative besteht darin, beide Module zu deinstallieren, nachdem das Moduldateisystem, die `pub/media`-Dateien und die Datenbanktabellen gesichert wurden _jedoch_ das Datenbankschema oder die Daten des Moduls entfernt wurden:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Meldungen ähnlich der folgenden werden angezeigt:

```
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Fehler werden angezeigt, wenn Sie versuchen, ein Modul mit einer Abhängigkeit von einem anderen Modul zu deinstallieren. In diesem Fall können Sie nicht ein Modul deinstallieren; Sie müssen beide deinstallieren.

## Zurücksetzen des Dateisystems, der Datenbank oder der Mediendateien

Verwenden Sie den folgenden Befehl, um die Code-Basis in den Zustand wiederherzustellen, in dem Sie sie gesichert haben:

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Dabei ist `<filename>` der Name der Sicherungsdatei im `<app_root>/var/backups`. Um eine Liste der Backup-Dateien anzuzeigen, geben Sie `magento info:backups:list` ein

>[!WARNING]
>
>Dieser Befehl löscht die angegebenen Dateien oder die Datenbank, bevor sie wiederhergestellt werden. Beispielsweise löscht die Option `--media-file` Medien-Assets unter dem `pub/media`-Verzeichnis, bevor sie aus der angegebenen Rollback-Datei wiederhergestellt werden. Vergewissern Sie sich, dass Sie das Dateisystem oder die Datenbank, das bzw. die Sie beibehalten möchten, nicht geändert haben, bevor Sie diesen Befehl verwenden.

>[!NOTE]
>
>Um eine Liste der verfügbaren Sicherungsdateien anzuzeigen, geben Sie `magento info:backups:list` ein

Dieser Befehl führt die folgenden Aufgaben aus:

1. Versetzt den Speicher in den Wartungsmodus.
1. Überprüft den Namen der Sicherungsdatei.
1. Wenn Sie eine Code-Rollback-Datei angeben:

   a. Überprüft, ob die Rollback-Zielspeicherorte beschreibbar sind (beachten Sie, dass die Ordner `pub/static` und `var` ignoriert werden).

   b. Löscht alle Dateien und Verzeichnisse unter dem Installationsverzeichnis der Anwendung.

   c. Extrahiert die Archivdatei an die Zielspeicherorte.

1. Wenn Sie eine Rollback-Datei für die Datenbank angeben:

   a. Löscht die gesamte Datenbank.

   b. Stellt die Datenbank mithilfe der Datenbanksicherung wieder her.

1. Wenn Sie eine Medien-Rollback-Datei angeben:

   a. Überprüft, ob die Rollback-Zielspeicherorte beschreibbar sind.

   b. Löscht alle Dateien und Ordner unter `pub/media`

   c. Extrahiert die Archivdatei an die Zielspeicherorte.

1. Entfernt den Speicher aus dem Wartungsmodus.

Um beispielsweise ein Code-Backup (d. h. ein Dateisystem-Backup) wiederherzustellen, geben Sie die folgenden Befehle in der angegebenen Reihenfolge ein:

* Zeigt eine Liste der Backups an:

  ```bash
  magento info:backups:list
  ```

* Stellen Sie eine Dateisicherung mit dem Namen `1433876616_filesystem.tgz` wieder her:

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  Meldungen ähnlich der folgenden werden angezeigt:

  ```
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>Um den `magento` erneut auszuführen, ohne die Verzeichnisse zu ändern, müssen Sie möglicherweise `cd pwd` eingeben.
