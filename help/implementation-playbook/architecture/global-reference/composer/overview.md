---
title: Komponentenentwicklung
description: Erfahren Sie mehr über die Entwicklung von Composer-Modulen im Verzeichnis "Anbieter/Anbieter".
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 7664ffb5-2e46-49c3-b2e6-c133c35d2f6b
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Komponentenentwicklung

In diesem Thema wird der empfohlene Ansatz für die Entwicklung von Composer-Modulen (als Git-Repositorys im Verzeichnis `vendor/` ) und das Hinzufügen dieser Module zu Ihrem Git-Hauptprojekt beschrieben.

>[!NOTE]
>
>Diese Richtlinien gelten hauptsächlich für [globale Referenzarchitektur (GRA)](../overview.md)-Projekte.

## Vorbereiten eines Entwicklungszweigs

1. Erstellen oder überprüfen Sie die Entwicklungsverzweigung in Ihrem Git-Haupt-Repository.
1. Erfordert Entwicklungsversionen für jedes Modul, das Sie pflegen.

   In diesem Beispiel stellt jede Verzweigung in Ihrem Git-Haupt-Repository eine Composer-Paketversion dar. Die empfohlene Benennungskonvention für Composer-Versionen in diesem Szenario lautet &quot;`dev-`&quot;, gefolgt vom Namen der Verzweigung. Beispiel:

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. Wenn für ein anderes Composer-Paket eine bestimmte Version eines Moduls erforderlich ist (z. B. `client/module-example 1.0.12`), installieren Sie es mit einem Alias:

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   Ersetzen Sie für den Zweig `qa` `dev-develop` durch `dev-qa`.

## Pakete in Git-Repositorys konvertieren

Standardmäßig enthalten Pakete kein Verzeichnis `.git/` . Der Composer kann Pakete aus Git auschecken, anstatt die vordefinierten Composer-Pakete zu verwenden. Der Vorteil dieses Ansatzes besteht darin, dass Sie die Pakete während der Entwicklung einfach ändern können.

1. Entfernen Sie das Modul aus dem Verzeichnis &quot;`vendor/`&quot;.

   ```bash
   rm -rf vendor/client/module-example
   ```

1. Installieren Sie das Modul unter Verwendung der [angegebenen Git-Quelle](#prepare-a-development-branch) neu.

   ```bash
   composer install --prefer-source
   ```

1. Stellen Sie sicher, dass das Composer-Paket jetzt ein Git-Repository ist:

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. So konvertieren Sie mehrere Module im Batch-Modus in Git-Repositorys (z. B. &quot;Client&quot;-Module):

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## Start development

1. Erstellen oder überprüfen Sie eine Funktion/Arbeitsverzweigung. Das folgende Beispiel zeigt eine Verzweigung mit demselben Namen wie ein Jira-Ticket.

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. Nachdem Sie die Verzweigungen in einem Modul geändert haben, sehen Sie sich die Änderungen an, indem Sie den Adobe Commerce-Cache und statischen Inhalt leeren.

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## Aktualisieren des Hauptprojekts mit Ihrer Entwicklung

Aktualisieren Sie Ihr Haupt-Git-Repository, indem Sie die Datei `composer.lock` ändern. Wenn Ihr Modul neu ist, aktivieren Sie es.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
