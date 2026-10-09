---
title: 'ACSD-54885: Ausnahme beim Auschecken mehrerer Adressen, wenn sich der Administrator als Kunde anmeldet'
description: Wenden Sie den Patch ACSD-54885 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Auschecken mehrerer Adressen ein Fehler auftritt, wenn der Administrator die *[!UICONTROL Login as Customer]*-Funktion verwendet.
feature: Checkout
role: Admin, Developer
exl-id: c146bc2a-2df1-4825-9cfc-69e04095b3c2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
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
source-wordcount: '412'
ht-degree: 0%
---
# ACSD-54885: Ausnahme beim Auschecken mehrerer Adressen, wenn sich der Administrator als Kunde anmeldet

Mit dem Patch ACSD-54885 wird das Problem behoben, dass beim Auschecken mehrerer Adressen ein Fehler auftritt, wenn der Administrator die Funktion *[!UICONTROL Login as Customer]* verwendet. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43 installiert ist. Die Patch-ID ist ACSD-54885. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Auschecken mehrerer Adressen tritt ein Fehler auf, wenn der Administrator die Funktion *[!UICONTROL Login as Customer]* verwendet.

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie sicher, dass *[!UICONTROL Login as Customer]* aktiviert ist. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie ein neues Kundenkonto mit einer Adresse.
1. Gehen Sie zum Kundenkonto im Backend:

   * Wechseln Sie zur Registerkarte **[!UICONTROL Account Information]** und legen Sie *[!UICONTROL Allow remote shopping assistance]* = *Ja* fest.
   * Klicken Sie auf **[!UICONTROL Login as Customer]**.

1. Fügen Sie das Produkt zum Warenkorb hinzu und fahren Sie mit der *[!UICONTROL Checkout with multiple addresses]* fort.
1. Aktualisieren Sie die Produktmenge.
1. Versuchen Sie, zum Warenkorb zurückzukehren.

<u>Erwartete Ergebnisse</u>:

Sie können den Warenkorb aktualisieren und mehrere Checkout-Adressen verwenden.

<u>Tatsächliche Ergebnisse</u>:

Wenn Sie zum Warenkorb zurückkehren, erhalten Sie die folgende Fehlermeldung.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
