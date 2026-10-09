---
title: Anpassen von Basisordnerpfaden
description: Verwenden Sie die Variable MAGE_DIRS , um ein Array absoluter Pfade festzulegen.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%
---
# Basisverzeichnispfade

Mit der Umgebungsvariablen `MAGE_DIRS` können Sie benutzerdefinierte Basisordnerpfade und Fragmente von Basis-URLs angeben, die von der Commerce-Anwendung zum Erstellen absoluter Pfade zu verschiedenen Dateien oder zum Generieren von URLs verwendet werden.

## MAGE_DIRS festlegen

Geben Sie ein assoziatives Array an, in dem Schlüssel Konstanten aus [\\Magento\\App\\Filesystem\\DirectoryList](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php) sind und Werte absolute Pfade von Verzeichnissen bzw. deren URL-Pfade sind.

Sie können `MAGE_DIRS` auf eine der folgenden Arten festlegen:

- [Festlegen des Werts von Bootstrap-Parametern](../bootstrap/set-parameters.md)
- Verwenden Sie ein benutzerdefiniertes Einstiegspunkt-Skript wie das folgende:

  ```php
  <?php
  /**
   * Copyright [first year code created] Adobe
   * All Rights Reserved.
   */
  
  use Magento\Framework\App\Bootstrap;
  use Magento\Framework\App\Filesystem\DirectoryList;
  use Magento\Framework\App\Http;
  
  require __DIR__ . '/app/bootstrap.php';
  $params = $_SERVER;
  $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
       DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
       DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
       DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
       DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
       DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
  ];
  $bootstrap = Bootstrap::create(BP, $params);
  /** @var Http $app */
  $app = $bootstrap->createApplication(Http::class);
  $bootstrap->run($app);
  ```

Im vorherigen Beispiel werden Pfade für `[cache]`- und `[media]`-Verzeichnisse auf `/mnt/nfs/cache` bzw. `/mnt/nfs/media` festgelegt.

