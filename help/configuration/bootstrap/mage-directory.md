---
title: Basisordnerpfade anpassen
description: Verwenden Sie die Variable MAGE_DIRS , um ein Array absoluter Pfade festzulegen.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Basisordnerpfade

Die `MAGE_DIRS` Mit der Umgebungsvariablen können Sie benutzerdefinierte Basisordnerpfade und Fragmente von Basis-URLs angeben, die von der Commerce-Anwendung zum Erstellen absoluter Pfade zu verschiedenen Dateien oder zum Generieren von URLs verwendet werden.

## MAGE_DIRS festlegen

Geben Sie ein assoziatives Array an, aus dem Schlüssel Konstanten sind [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] und -Werte sind absolute Pfade von Verzeichnissen bzw. deren URL-Pfaden.

Sie können `MAGE_DIRS` auf eine der folgenden Arten:

- [Wert der Bootstrap-Parameter festlegen](../bootstrap/set-parameters.md)
- Verwenden Sie ein benutzerdefiniertes Einstiegspunkt-Skript wie das folgende:

  ```php
  <?php
  /**
   * Copyright © Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
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

Im vorherigen Beispiel werden Pfade für `[cache]` und `[media]` Verzeichnisse in `/mnt/nfs/cache` und `/mnt/nfs/media`, bzw.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
