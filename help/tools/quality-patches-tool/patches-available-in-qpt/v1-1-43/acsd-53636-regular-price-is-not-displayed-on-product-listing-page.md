---
title: 'ACSD-53636: Regulärer Preis wird auf [!UICONTROL Product Listing] Seite nicht angezeigt'
description: Wenden Sie den Patch ACSD-53636 an, um das Adobe Commerce-Problem zu beheben, bei dem der reguläre Preis für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreisen nicht auf *[!UICONTROL Product Listing]*-Seiten angezeigt wird.
feature: Catalog Management, Products
role: Admin, Developer
exl-id: e6d66ae4-2c21-466a-b03c-a1f486e7fa29
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-53636: Regulärer Preis wird auf *[!UICONTROL Product Listing]* Seite nicht angezeigt

Mit dem Patch ACSD-53636 wird das Problem behoben, dass der reguläre Preis für konfigurierbare Produkte mit untergeordneten Produkten mit Sonderpreisen nicht auf *[!UICONTROL Product Listing]* Seiten angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 installiert ist. Die Patch-ID ist ACSD-53636. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der reguläre Preis wird auf *[!UICONTROL Product Listing]* Seiten für konfigurierbare Produkte, die untergeordnete Produkte mit Sonderpreisen haben, nicht angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei Admin an, gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** und erstellen oder öffnen Sie ein konfigurierbares Produkt.
2. Öffnen Sie das untergeordnete Produkt, fügen Sie allen oder einem untergeordneten Produkt einen Sonderpreis hinzu und speichern Sie das Produkt.
3. Wechseln Sie zu Frontend und öffnen Sie die **[!UICONTROL Product Detail]** Seite des konfigurierbaren Produkts. In den Farbfeldern des untergeordneten Produkts mit dem Sonderpreis wird der *[!UICONTROL Regular price]* gestrichen angezeigt (erwartet).
4. Wechseln Sie zu Frontend und öffnen Sie die **[!UICONTROL Product Listing]** für das konfigurierbare Produkt mit einem Sonderpreis. Sie sehen, dass die konfigurierbaren Produktmuster im Gegensatz zu den *[!UICONTROL Product Detail Page]* und anderen einfachen Produkten nicht den regulären Preis anzeigen.

<u>Erwartete Ergebnisse</u>:

Auf der Seite *[!UICONTROL Product Listing]* zeigt das konfigurierbare Produkt den regulären Preis für sein untergeordnetes Produkt an.

<u>Tatsächliche Ergebnisse</u>:

Auf der Seite *[!UICONTROL Product Listing]* zeigt das konfigurierbare Produkt nicht den regulären Preis für sein untergeordnetes Produkt an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
