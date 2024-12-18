---
title: Upgrade von Modulen und Erweiterungen
description: Verwenden Sie die Befehlszeilenschnittstelle und den Composer, um Adobe Commerce-Module und -Erweiterungen zu aktualisieren.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Upgrade von Modulen und Erweiterungen

So aktualisieren oder aktualisieren Sie ein Modul oder eine Erweiterung:

1. Laden Sie die aktualisierte Datei von Marketplace oder einem anderen Entwickler der Erweiterung herunter. Notieren Sie sich den Modulnamen und die Version.

1. Exportieren Sie die Inhalte in das Adobe Commerce-Stammverzeichnis.

1. Wenn für das Modul ein Composer-Paket vorhanden ist, führen Sie einen der folgenden Schritte aus.

   Aktualisierung pro Modulname:

   ```bash
   composer update vendor/module-name
   ```

   Aktualisierung pro Version:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Führen Sie die folgenden Befehle aus, um den Cache zu aktualisieren, bereitzustellen und zu bereinigen.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## Vom Anbieter gebündelte Erweiterungen (VBEs)

Adobe hat alle [VBEs](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/modules/upgrade) in 2.4.4 entfernt. Anbieter unterstützen diese Erweiterungen weiterhin auf dem Adobe Commerce Marketplace.

Wenn Sie diese Erweiterungen weiterhin mit Adobe Commerce 2.4.4 und höher verwenden möchten, müssen Sie die entsprechenden Paketabhängigkeiten in Ihrer `composer.json`-Datei aktualisieren _vor_ einem Upgrade auf 2.4.4. Wenden Sie sich an den Anbieter, um den Paketnamen und die zu verwendende Version zu erhalten.

Weitere Informationen finden Sie in den folgenden Adobe Commerce Marketplace-Listen:

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)
