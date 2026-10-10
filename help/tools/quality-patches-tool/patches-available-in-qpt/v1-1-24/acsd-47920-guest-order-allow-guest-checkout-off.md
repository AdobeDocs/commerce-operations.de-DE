---
title: 'ACSD-47920: Ein Gastbenutzer kann Bestellungen über die REST-API aufgeben, selbst wenn die [!UICONTROL Allow Guest Checkout] deaktiviert ist'
description: Wenden Sie den Patch ACSD-47920 an, um das Adobe Commerce-Problem zu beheben, bei dem Bestellungen als Gastbenutzer über die REST-API aufgegeben werden können, selbst wenn die [!UICONTROL Allow Guest Checkout] deaktiviert ist.
feature: REST, Checkout, Orders
role: Admin
exl-id: 27c74803-a3f3-46bc-9eb8-8e2c72c30cd9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%
---
# ACSD-47920: Ein Gastbenutzer kann Bestellungen über die REST-API aufgeben, selbst wenn die **[!UICONTROL Allow Guest Checkout]** deaktiviert ist

Mit dem Patch ACSD-47920 wird das Problem behoben, dass Bestellungen als Gastbenutzer über die REST-API selbst dann aufgegeben werden können, wenn die **[!UICONTROL Allow Guest Checkout]** deaktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47920. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bestellungen können über die REST-API auch dann als Gastbenutzer aufgegeben werden, wenn die **[!UICONTROL Allow Guest Checkout]** deaktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > und legen Sie die **[!UICONTROL Allow Guest Checkout]** auf _Nein_ fest.
1. Verwenden Sie die REST-API, um ein Produkt zu einem Warenkorb hinzuzufügen und eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

Die Gast-Checkout-API gibt eine *[!UICONTROL Sorry, guest checkout is not available]* zurück, wenn **[!UICONTROL Allow Guest Checkout]** auf &quot;_&quot;_.

<u>Tatsächliche Ergebnisse</u>:

Mit der Gast-Checkout-API kann eine Bestellung auch dann aufgegeben werden, wenn **[!UICONTROL Allow Guest Checkout]** auf &quot;_&quot;_.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
