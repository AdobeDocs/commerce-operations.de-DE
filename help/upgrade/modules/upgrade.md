---
title: Upgrade-Module und -Erweiterungen
description: Verwenden Sie die Befehlszeilenschnittstelle und den Composer, um Adobe Commerce- und Magento Open Source-Module und -Erweiterungen zu aktualisieren.
source-git-commit: c619bff9785d22298bc49e2ac9874480ff7a320b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Upgrade-Module und -Erweiterungen

So aktualisieren oder aktualisieren Sie ein Modul oder eine Erweiterung:

1. Laden Sie die aktualisierte Datei von Marketplace oder einem anderen Erweiterungsentwickler herunter. Notieren Sie sich den Modulnamen und die Version.

1. Exportieren Sie die Inhalte in den Installationsordner des Adobe Commerce- oder Magento Open Source-Stammordners.

1. Wenn für das Modul ein Composer-Paket vorhanden ist, führen Sie einen der folgenden Schritte aus.

   Aktualisierung nach Modulname:

   ```bash
   composer update vendor/module-name
   ```

   Aktualisierung pro Version:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Führen Sie die folgenden Befehle aus, um den Cache zu aktualisieren, bereitzustellen und zu leeren.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## Gebündelte Erweiterungen (VBEs) des Anbieters

Adobe entfernt alle [VBEs](https://devdocs.magento.com/extensions/vendor/) in 2.4.4. Anbieter unterstützen diese Erweiterungen weiterhin auf dem Adobe Commerce Marketplace.

Wenn Sie diese Erweiterungen weiterhin mit Adobe Commerce und Magento Open Source 2.4.4 und höher verwenden möchten, müssen Sie die entsprechenden Paketabhängigkeiten in Ihrer `composer.json` file _before_ Aktualisierung auf 2.4.4. Wenden Sie sich an den Anbieter, um den Paketnamen und die zu verwendende Version zu erhalten.

Weitere Informationen finden Sie in den folgenden Adobe Commerce Marketplace-Listen:

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)

