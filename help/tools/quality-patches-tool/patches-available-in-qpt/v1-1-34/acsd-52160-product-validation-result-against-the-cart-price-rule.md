---
title: "ACSD-52160: Ergebnis der Produktvalidierung anhand der Preisregel des Warenkorbs"
description: Wenden Sie den Patch ACSD-52160 an, um das Adobe Commerce-Problem zu beheben, bei dem das Ergebnis der Produktvalidierung anhand der Preisregel für den Warenkorb nicht ordnungsgemäß anhand der Regelbedingung *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]* bewertet wird.
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52160: Das Ergebnis der Produktvalidierung mit der Warenkorbpreisregel wird nicht ordnungsgemäß ausgewertet

Der Patch ACSD-52160 behebt das Problem, dass das Ergebnis der Produktvalidierung anhand der Preisregel für den Warenkorb nicht ordnungsgemäß anhand der Regelbedingung *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]* ausgewertet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34 installiert ist. Die Patch-ID ist ACSD-52160. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Ergebnis der Produktvalidierung mit der Regel zum Warenkorbpreis wird nicht ordnungsgemäß anhand der Regelbedingung *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]* ausgewertet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Produkte, die zwei verschiedenen Kategorien zugeordnet sind.
1. Erstellen Sie eine **[!UICONTROL Cart Price Rule]** mit Bedingungen wie:

   * **SKU 1** im Parameter *[!UICONTROL FOUND]*
   * **SKU 2** im Parameter *[!UICONTROL NOT FOUND]*

1. Fügen Sie beide Produkte zum Warenkorb hinzu.
1. Wenden Sie den Gutscheincode an.

<u>Erwartete Ergebnisse</u>

Der Couponcode wird nicht angewendet, da der Warenkorb Produkte der eingeschränkten Kategorie enthält.

<u>Tatsächliche Ergebnisse</u>

Der Couponcode wird angewendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](</help/tools/quality-patches-tool/usage.md>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
