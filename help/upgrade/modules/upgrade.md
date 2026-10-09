---
title: Upgrade von Modulen und Erweiterungen
description: Verwenden Sie die Befehlszeilenschnittstelle und den Composer, um Adobe Commerce-Module und -Erweiterungen zu aktualisieren.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
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
source-wordcount: '196'
ht-degree: 0%
---
# Upgrade von Modulen und Erweiterungen

So aktualisieren oder aktualisieren Sie ein Modul oder eine Erweiterung:

1. Laden Sie die aktualisierte Datei von Marketplace oder einem anderen Entwickler der Erweiterung herunter. Notieren Sie sich den Modulnamen und die Version.

1. Exportieren Sie die Inhalte in das Adobe Commerce-Stammverzeichnis.

1. Wenn für das Modul ein Composer-Paket vorhanden ist, führen Sie einen der folgenden Schritte aus.

   Aktualisierung pro Modulname:

   ```shell
   composer update vendor/module-name
   ```

   Aktualisierung pro Version:

   ```shell
   composer require vendor/module-name ^x.x.x
   ```

1. Führen Sie die folgenden Befehle aus, um den Cache zu aktualisieren, bereitzustellen und zu bereinigen.

   ```shell
   bin/magento setup:upgrade --keep-generated
   ```

   ```shell
   bin/magento setup:static-content:deploy
   ```

   ```shell
   bin/magento cache:clean
   ```

## Vom Anbieter gebündelte Erweiterungen (VBEs)

Adobe hat alle [VBEs](/help/upgrade/modules/upgrade.md) in 2.4.4 entfernt. Anbieter unterstützen diese Erweiterungen weiterhin auf dem Adobe Commerce Marketplace.

Wenn Sie diese Erweiterungen weiterhin mit Adobe Commerce 2.4.4 und höher verwenden möchten, müssen Sie die entsprechenden Paketabhängigkeiten in Ihrer `composer.json`-Datei aktualisieren _vor_ einem Upgrade auf 2.4.4. Wenden Sie sich an den Anbieter, um den Paketnamen und die zu verwendende Version zu erhalten.

Weitere Informationen finden Sie in den folgenden Adobe Commerce Marketplace-Listen:

- [Amazon Pay](https://commercemarketplace.adobe.com//amzn-amazon-pay-magento-2-module.html)
- [dotdigital](https://commercemarketplace.adobe.com//dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://commercemarketplace.adobe.com//klarna-m2-klarna.html)
- [Scheitelpunkt](https://commercemarketplace.adobe.com//vertexinc-vertex-tax-module.html)
- [Yotopo](https://commercemarketplace.adobe.com//yotpo-module-yotpo.html)
