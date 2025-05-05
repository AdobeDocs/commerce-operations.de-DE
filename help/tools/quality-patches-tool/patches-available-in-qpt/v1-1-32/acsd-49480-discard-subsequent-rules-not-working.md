---
title: 'ACSD-49480: Nachfolgende Regeln verwerfen funktioniert nicht'
description: Wenden Sie den ACSD-49480 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die [!UICONTROL Cart Price Rule - Discard Subsequent Rules] nicht wie vorgesehen funktioniert.
feature: Price Rules
role: Admin
exl-id: 1919043b-99a8-46a2-94df-9285c05bec7b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-49480: [!UICONTROL Cart Price Rule - Discard Subsequent Rules] funktioniert nicht wie beabsichtigt

Mit dem Patch ACSD-49480 wird das Problem behoben, dass die [!UICONTROL Cart Price Rule - Discard Subsequent Rules] nicht wie vorgesehen funktioniert. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-49480. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] funktioniert nicht wie beabsichtigt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine **[!UICONTROL Cart Price Rule]** mit einem Couponcode (nennen Sie ihn *TEST*), der der *Produkt-ID 1* auf der Registerkarte **[!UICONTROL Actions]** einen Rabatt von 10 USD gewährt, wobei [!UICONTROL Discard Subsequent Rules] auf *[!UICONTROL Yes]* eingestellt ist und [!UICONTROL Priority] auf *1 eingestellt*.
1. Erstellen Sie eine weitere **[!UICONTROL Cart Price Rule]** ohne Couponcode, der einen Rabatt von 5 $ auf *Produkt-ID 2* auf der Registerkarte &quot;**[!UICONTROL Actions]**&quot; gewährt, wobei [!UICONTROL Priority] auf *2 eingestellt ist*. Hier nehmen wir an, dass es sich um einen globalen Verkauf für *Produkt-ID 2* handelt.
1. Gehen Sie zur Frontend-Site und fügen Sie *Produkt-ID 1* und *Produkt-ID 2* in den Warenkorb ein.
1. Wenden Sie den *TEST*-Couponcode an.

<u>Erwartete Ergebnisse</u>

* *Rabatt 1* wird auf *Produkt-ID 1* angewendet.
* *Rabatt 2* wird auf *Produkt-ID 2* angewendet.

<u>Tatsächliche Ergebnisse</u>

* Nur *Rabatt 1* wird auf *Produkt-ID 1* angewendet.
* *Rabatt 2* wird nicht auf „Produkt *ID 2“*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
