---
title: Basisordnerpfade anpassen
description: Verwenden Sie die Variable MAGE_DIRS , um ein Array absoluter Pfade festzulegen.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Basisordnerpfade

Mit der Umgebungsvariablen `MAGE_DIRS` können Sie benutzerdefinierte Basisordnerpfade und Fragmente von Basis-URLs angeben, die von der Commerce-Anwendung zum Erstellen absoluter Pfade zu verschiedenen Dateien oder zum Generieren von URLs verwendet werden.

## MAGE_DIRS festlegen

Geben Sie ein assoziatives Array an, in dem Schlüssel Konstanten von [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] sind und Werte absolute Pfade von Verzeichnissen bzw. deren URL-Pfaden sind.

Sie können `MAGE_DIRS` auf eine der folgenden Arten festlegen:

- [Wert der Bootstrap-Parameter festlegen](../bootstrap/set-parameters.md)
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

Im vorherigen Beispiel werden die Pfade für die Verzeichnisse `[cache]` und `[media]` auf `/mnt/nfs/cache` bzw. `/mnt/nfs/media` gesetzt.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
