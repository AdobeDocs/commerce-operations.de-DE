---
title: Projektstruktur des Composers
description: Erfahren Sie, wie Sie die Option für separate Pakete einrichten und verwalten, die in den Beispielen der globalen Referenzarchitektur beschrieben wird.
feature: Best Practices
role: Developer
source-git-commit: b4213c40fdf903fd962a15fc99b143f31aedbcde
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# Projektstruktur des Composers

In diesem Handbuch wird beschrieben, wie Sie die [Option für separate Pakete](../examples.md#option-1-separate-packages) in den Beispielen der globalen Referenzarchitektur (GRA) beschrieben.

## Voraussetzungen

Bevor Sie beginnen, überprüfen Sie Folgendes:

- Sie verfügen über ein Git-Repository
- Sie verfügen über ein Composer-Repository (in diesem Thema wird Private Packagist hervorgehoben).
- Sie haben Ihr Composer-Repository so konfiguriert, dass es den `repo.magento.com` und `packagist.org` Repositorys

## Haupt-Git-Projekt-Repository

Das Haupt-Git-Projekt-Repository sollte nur ein Composer-Projekt enthalten. Sie können alles andere mit Composer-Paketen verwalten. Das Hauptprojekt sollte niemals etwas Anderes als die folgende Dateistruktur enthalten, da der Composer alle anderen Pakete über Abhängigkeiten installiert:

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Fügen Sie dem `.gitignore` Datei:

```tree
/*
!/composer.json
!/composer.lock
```

## Initialisieren des Hauptprojekts

1. Erstellen Sie ein Git-Repository mit dem Namen `project-<region/country/brand>`.

1. Erstellen `composer.json` und `composer.lock` -Dateien:

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## Speichern von Nicht-Moduldateien

1. Fügen Sie die `app/etc/config.xml` in das Git-Repository.

   Sie können das Modul verwenden, das Sie erstellen werden, um andere regionsspezifische oder markenspezifische Dateien zu installieren, z. B. `.htaccess`, Google- oder Bing-Authentifizierungstextdateien, ausführbare Dateien oder andere statische Dateien, die nicht von Adobe Commerce-Modulen verwaltet werden.

   Verwendung `magento2-component` Geben Sie Pakete ein, um eine Dateizuordnung zu erstellen, um Dateien in das Git-Haupt-Repository zu kopieren während `composer install` und `composer update` Vorgänge.

1. Erstellen Sie ein Git-Repository, das der Benennungskonvention entspricht. `component-environment-<region/country/brand>`:

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. Fügen Sie die `app/etc/config.php` als Zuordnung in der `extra.map` -Attribut Ihres `composer.json` Datei:

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. Validieren Sie Ihre `composer.json` und übertragen Sie sie in das Git-Repository:

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## Einrichten von Metapaketen

1. Erstellen Sie die folgenden Git-Repositorys:

   - `meta-gra`
   - `meta-<region/country/brand>`

1. Richten Sie die folgende Abhängigkeitsstruktur ein:

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. Erstellen Sie das GRA-Metapaket:

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Erstellen Sie das Markenmetapaket:

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Erfordert die Sammlung über Abhängigkeitsverwaltung im Hauptprojekt:

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Überprüfen Sie, ob der Composer die `app/etc/config.php` Datei aus `<client>/component-environment-<region/country/brand>`.

## Bereitstellungscode

Auf dem Webserver können Sie Code mithilfe von Composer bereitstellen, das Hauptprojekt jedoch nicht aktualisieren. Installieren Sie das Projekt mit Composer bei jeder neuen Implementierung neu, wodurch Produktions- und Testserver keinen Zugriff auf Git haben müssen.

## Andere Instanzen und Pakete hinzufügen

Jede Instanz (Region, Marke oder anderweitig eindeutige Adobe Commerce-Installation) sollte eine eigene erhalten **Hauptprojekt** Instanz, **spezifisches Metapaket**, und **Umgebungs-Komponentenpaket**. Die **GRA-Metapaket** sollte **shared** alle Instanzen.

Funktionspakete (z. B. Adobe Commerce-Module, Designs, Sprachpakete und Bibliotheken) und Pakete von Drittanbietern sollten erforderlich sein, indem Sie:

- **GRA-Metapaket**—Für die Installation auf _all_ Instanzen
- **Instanzspezifisches Metapaket**—Für die Installation auf einer einzigen Marke oder Region

>[!IMPORTANT]
>
>Sie benötigen keine Pakete im Hauptprojekt `composer.json` -Datei auf `main` oder `release` Verzweigungen.

## Vorbereitungen für die Entwicklung

Für die Entwicklung installieren Sie `develop` Versionen aller Module, die Sie verwalten.

Abhängig von Ihrer Verzweigungsstrategie haben Sie möglicherweise `develop`, `qa`, `uat`, und `main` Verzweigungen. Jede Verzweigung ist in Composer mit einer `dev-` -Präfix. Also die `develop` Verzweigung kann über Composer als Version erforderlich sein `dev-develop`.

1. Erstellen `develop` Verzweigungen in allen Modulen und Projekt-Repositorys.

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   Der vorherige Schritt generiert die folgenden Zeilen in Ihrer `composer.json` Datei:

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**Keine Zusammenführung** diese `composer.json` -Datei in Ihrer Produktionsverzweigung geändert. Installieren Sie nur stabile Versionen von Paketen auf `release` und `main` Verzweigungen. Sie können diese Abhängigkeiten für `qa` Zweige und andere Zweige, die keine Hauptzweige sind.
