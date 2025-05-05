---
title: 'ACSD-63242: Langsamer Import beim Hinzufügen von mehr als 10.000 Katalogprodukten'
description: Wenden Sie den Patch ACSD-63242 an, um das Adobe Commerce-Problem langsamer Importe zu beheben, wenn Katalogprodukte mit mehr als 10.000 Einträgen hinzugefügt werden.
feature: Data Import/Export
role: Admin, Developer
exl-id: 2d9114c8-72e4-4a11-89e7-b1a41c1fe14f
source-git-commit: ee0d0afc6231a08f0fbae29b5be2078cf7a4f940
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# ACSD-63242: Langsamer Import beim Hinzufügen von mehr als 10.000 Katalogprodukten

Der Patch ACSD-63242 behebt das Problem langsamer Importe, wenn Katalogprodukte mit mehr als 10.000 Einträgen hinzugefügt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installiert ist. Die Patch-ID ist ACSD-63242. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p8

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p8 und 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Produktimport ist langsam, wenn Katalogprodukte mit mehr als 10.000 Einträgen hinzugefügt werden.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Import]** > **[!UICONTROL Products]** > **[!UICONTROL Add/Update]**.
1. Datei mit über 10.000 Einträgen importieren.

<u>Erwartete Ergebnisse</u>:

Der Import von Katalogprodukten wird in der erwarteten Zeit ausgeführt.

<u>Tatsächliche Ergebnisse</u>:

Der Produktimport ist langsam. Die `var/log/exception.log` enthält:

```PHP
Exception: Warning: DOMXPath::query(): Recursion limit exceeded in /var/www/html/lib/internal/Magento/Framework/Validator/HTML/ConfigurableWYSIWYGValidator.php on line 114 in /var/www/html/lib/internal/Magento/Framework/App/ErrorHandler.php:62
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
