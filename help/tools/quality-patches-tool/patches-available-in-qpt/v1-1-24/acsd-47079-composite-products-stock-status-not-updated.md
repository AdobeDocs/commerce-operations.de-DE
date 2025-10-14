---
title: 'ACSD-47079: Lagerstatus von zusammengesetzten Produkten wird nicht aktualisiert, wenn sich der Lagerstatus von Unterprodukten ändert'
description: Wenden Sie den Patch ACSD-47079 an, um das Adobe Commerce-Problem zu beheben, bei dem der Lagerstatus von zusammengesetzten Produkten (gebündelt, gruppiert und konfigurierbar) nicht aktualisiert wird, wenn sich der Lagerstatus des Unterprodukts über REST-API POST /rest/V1/inventory/source-items ändert.
feature: Orders, Products
role: Admin
exl-id: f035f530-fae5-4b61-8af9-044f6ec02284
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-47079: Lagerstatus von zusammengesetzten Produkten wird nicht aktualisiert, wenn sich der Lagerstatus von Unterprodukten ändert

Mit dem Patch ACSD-47079 wird das Problem behoben, dass der Lagerstatus von zusammengesetzten Produkten (Bundle, Gruppiert und Konfigurierbar) nicht aktualisiert wird, wenn der Lagerstatus des Unterprodukts über die REST-API-POST-`/rest/V1/inventory/source-items` geändert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47079. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Lagerstatus von zusammengesetzten Produkten (gebündelt, gruppiert und konfigurierbar) wird nicht aktualisiert, wenn der Lagerstatus des Unterprodukts über die REST-API-POST-`/rest/V1/inventory/source-items` geändert wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares, gebündeltes und gruppiertes Produkt mit jeweils einem einfachen untergeordneten Produkt.
1. Legen Sie jeden einfachen untergeordneten Produktstatus mithilfe des **[!UICONTROL Out of Stock]**-API-Aufrufs auf `source-items` fest.
1. Überprüfen Sie jetzt den Lagerstatus des übergeordneten Produkts.

<u>Erwartete Ergebnisse</u>:

Der Status des übergeordneten Produkts ist [!UICONTROL Out of Stock].

<u>Tatsächliche Ergebnisse</u>:

Der Status des übergeordneten Produkts ist [!UICONTROL In Stock].

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
