---
title: Projektstruktur des Composers
description: Erfahren Sie, wie Sie die Option für separate Pakete einrichten und verwalten, die in den Beispielen der globalen Referenzarchitektur beschrieben wird.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 8757d5b8-8309-452f-bfb3-1188a816d14f
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Projektstruktur des Composers

In diesem Handbuch wird beschrieben, wie Sie die Option [Separate Packages](../examples.md#option-1-separate-packages) einrichten und verwalten, die in den Beispielen der globalen Referenzarchitektur (GRA) beschrieben wird.

## Voraussetzungen

Bevor Sie beginnen, überprüfen Sie Folgendes:

- Sie verfügen über ein Git-Repository
- Sie verfügen über ein Composer-Repository (in diesem Thema wird Private Packagist hervorgehoben).
- Sie haben Ihr Composer-Repository so konfiguriert, dass es die Repositorys `repo.magento.com` und `packagist.org` spiegelt

## Haupt-Git-Projekt-Repository

Das Haupt-Git-Projekt-Repository sollte nur ein Composer-Projekt enthalten. Sie können alles andere mit Composer-Paketen verwalten. Das Hauptprojekt sollte niemals etwas Anderes als die folgende Dateistruktur enthalten, da der Composer alle anderen Pakete über Abhängigkeiten installiert:

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Fügen Sie der Datei `.gitignore` den folgenden Inhalt hinzu:

```tree
/*
!/composer.json
!/composer.lock
```

## Initialisieren des Hauptprojekts

1. Erstellen Sie ein Git-Repository mit dem Namen `project-<region/country/brand>`.

1. Erstellen Sie die Dateien `composer.json` und `composer.lock`:

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

1. Fügen Sie die Datei `app/etc/config.xml` zum Git-Repository hinzu.

   Sie können das Modul verwenden, das Sie erstellen werden, um andere regionsspezifische oder markenspezifische Dateien wie `.htaccess`, Google- oder Bing-Authentifizierungstextdateien, ausführbare Dateien oder andere statische Dateien zu installieren, die nicht von Adobe Commerce-Modulen verwaltet werden.

   Verwenden Sie Pakete vom Typ `magento2-component` , um eine Dateizuordnung zu erstellen, damit Dateien während der Vorgänge `composer install` und `composer update` in das Git-Haupt-Repository kopiert werden.

1. Erstellen Sie ein Git-Repository, das der Benennungsregel `component-environment-<region/country/brand>` folgt:

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

1. Fügen Sie die Datei `app/etc/config.php` als Zuordnung im Attribut `extra.map` Ihrer `composer.json` -Datei hinzu:

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

1. Validieren Sie Ihre `composer.json` -Datei und übertragen Sie sie in das Git-Repository:

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

1. Stellen Sie sicher, dass der Composer die Datei &quot;`app/etc/config.php`&quot; aus &quot;`<client>/component-environment-<region/country/brand>`&quot; kopiert hat.

## Bereitstellungscode

Auf dem Webserver können Sie Code mithilfe von Composer bereitstellen, das Hauptprojekt jedoch nicht aktualisieren. Installieren Sie das Projekt mit Composer bei jeder neuen Implementierung neu, wodurch Produktions- und Testserver keinen Zugriff auf Git haben müssen.

## Andere Instanzen und Pakete hinzufügen

Jede Instanz (Region, Marke oder anderweitig eindeutige Adobe Commerce-Installation) sollte eine eigene **Hauptprojektinstanz**, ein **spezifisches Metapaket** und ein **Umgebungskomponentenpaket** erhalten. Das **GRA-Metapaket** sollte **shared** für alle Instanzen sein.

Funktionspakete (z. B. Adobe Commerce-Module, Designs, Sprachpakete und Bibliotheken) und Pakete von Drittanbietern sollten erforderlich sein, indem Sie:

- **GRA-Metapaket** - Für die Installation auf _allen_ -Instanzen
- **Instanzspezifisches Metapaket** - Zur Installation auf einer einzelnen Marke oder Region

>[!IMPORTANT]
>
>Sie benötigen keine Pakete in der Datei `composer.json` des Hauptprojekts in den Verzweigungen `main` oder `release`.

## Vorbereitungen für die Entwicklung

Installieren Sie für die Entwicklung `develop` Versionen aller Module, die Sie verwalten.

Abhängig von Ihrer Verzweigungsstrategie können Sie über die Verzweigungen `develop`, `qa`, `uat` und `main` verfügen. Jede Verzweigung ist im Composer mit dem Präfix `dev-` vorhanden. Der Zweig `develop` kann also über den Composer als Version `dev-develop` erforderlich sein.

1. Erstellen Sie `develop` Zweige in allen Modulen und Projektrepositorys.

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

   Der vorherige Schritt generiert die folgenden Zeilen in Ihrer `composer.json` -Datei:

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**Führen Sie diese `composer.json` Dateiänderungen nicht in Ihrer Produktionsverzweigung zusammen.** Installieren Sie nur stabile Versionen von Paketen auf den Verzweigungen `release` und `main` . Sie können diese Abhängigkeiten für `qa` -Zweige und andere Nicht-Haupt-Zweige definieren.
