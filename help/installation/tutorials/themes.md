---
title: Designs deinstallieren
description: Führen Sie diese Schritte aus, um ein Adobe Commerce- oder Magento Open Source-Design zu deinstallieren.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Designs deinstallieren

Bevor Sie diesen Befehl verwenden, müssen Sie den relativen Pfad zu Ihrem Design kennen. Designs befinden sich in einem Unterverzeichnis von `<magento_root>/app/design/<area name>`. Sie müssen den Pfad zum Thema angeben, beginnend mit dem Bereich, der entweder `frontend` (für Storefront-Designs) oder `adminhtml` (für [Admin](https://glossary.magento.com/magento-admin) Themen).

Beispielsweise der Pfad zum Luma [Design](https://glossary.magento.com/theme) mit Adobe Commerce und Magento Open Source bereitgestellt wird `frontend/Magento/luma`.

Weitere Informationen zu Designs finden Sie unter [Designstruktur](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Überblick über die Deinstallation von Designs

In diesem Abschnitt wird beschrieben, wie Sie ein oder mehrere Designs deinstallieren, optional einschließlich des Designcodes aus dem Dateisystem. Sie können zunächst Sicherungen erstellen, damit Sie die Daten später wiederherstellen können.

Dieser Befehl deinstalliert *only* Designs, die in `composer.json`; mit anderen Worten: Themen, die als [Verfasser](https://glossary.magento.com/composer) Packages. Wenn Ihr Design kein Composer-Paket ist, müssen Sie es manuell deinstallieren, indem Sie:

* Aktualisieren der `parent` Knoteninformationen in `theme.xml` , um Verweise auf das Design zu entfernen.
* Entfernen des Design-Codes aus dem Dateisystem.

   [Weitere Informationen zur Vererbung von Designs](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Designs deinstallieren

Befehlsverwendung:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Wo

* `{theme path}` ist der relative Pfad zum Thema, beginnend mit dem Bereichsnamen. Beispielsweise lautet der Pfad zum leeren Design, das mit Adobe Commerce und Magento Open Source bereitgestellt wird: `frontend/Magento/blank`.
* `--backup-code` sichert die Codebase, wie in den folgenden Absätzen beschrieben.
* `--clear-static-content` erzeugte Bereinigungen [statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md), was erforderlich ist, damit statische Ansichtsdateien ordnungsgemäß angezeigt werden.

Der Befehl führt die folgenden Aufgaben aus:

1. Stellt sicher, dass die angegebenen Design-Pfade vorhanden sind; Wenn nicht, wird der Befehl beendet.
1. Stellt sicher, dass das Design ein Composer-Paket ist; Wenn nicht, wird der Befehl beendet.
1. Prüft auf Abhängigkeiten und beendet den Befehl, wenn es nicht erfüllte Abhängigkeiten gibt.

   Um dies zu umgehen, können Sie entweder alle Designs gleichzeitig deinstallieren oder die Datei je nach Design zuerst deinstallieren.

1. Stellt sicher, dass das Design nicht verwendet wird; Wenn sie verwendet wird, wird der Befehl beendet.
1. Stellt sicher, dass das Design nicht die Grundlage des virtuellen Designs ist; Wenn es die Basis eines virtuellen Designs ist, wird der Befehl beendet.
1. Setzt den Speicher in den Wartungsmodus.
1. Wenn `--backup-code` angegeben ist, sichern Sie die Codebase, mit Ausnahme der `pub/static`, `pub/media`und `var` Verzeichnissen.

   Der Name der Sicherungsdatei lautet `var/backups/<timestamp>_filesystem.tgz`

   Sie können Backups jederzeit mithilfe des [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) Befehl.

1. Entfernt Designs aus der `theme` Datenbanktabelle.
1. Entfernen Sie Designs aus der Codebasis mit `composer remove`.
1. Bereinigt die [cache](https://glossary.magento.com/cache).
1. Bereinigt generierte Klassen
1. Wenn `--clear-static-content` spezifiziert ist, cleans [generierte statische Ansichtsdateien](../../configuration/cli/static-view-file-deployment.md).

Wenn Sie beispielsweise versuchen, ein Design zu deinstallieren, von dem ein anderes Design abhängig ist, wird die folgende Meldung angezeigt:

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

Eine Alternative besteht darin, beide Designs gleichzeitig zu deinstallieren, wie in der folgenden Sicherung der Codebasis beschrieben:

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

Meldungen, die der folgenden Anzeige ähneln:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>So deinstallieren Sie eine [Admin](https://glossary.magento.com/admin) -Design verwenden, müssen Sie es auch aus dem [Abhängigkeitsinjektion](https://glossary.magento.com/dependency-injection) Konfiguration, `<component root directory>/etc/di.xml`.
