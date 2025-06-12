---
title: 'ACSD-53378: Verbessertes Kassenerlebnis für Kunden mit umfangreichen Adressbüchern'
description: Wenden Sie den ACSD-53378 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Leistungsprobleme auftreten, die durch große Kundenadressvolumen verursacht werden.
feature: Customers, Checkout
role: Admin
exl-id: 699d09fe-872f-44d3-88bb-b5b585e15067
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-53378: Verbessertes Kassenerlebnis für Kunden mit umfangreichen Adressbüchern

Mit dem Patch ACSD-53378 wird das Problem behoben, dass Leistungsprobleme auftreten, die durch große Kundenadressvolumen verursacht werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-53378. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn ein Kunde über eine große Anzahl von Adressen verfügt, wird die Leistung von Adobe Commerce sehr langsam.

Wenn die Konfigurationsoption *[!UICONTROL Enable search address]* unter **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** aktiviert ist, wird das gesamte Kundenadressbuch nicht mehr vollständig verarbeitet. Die Anzahl der verarbeiteten Kundenadressen wird durch die Einstellung *[!UICONTROL Customer Addresses Limit]* unter **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** bestimmt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt aus der Admin-Liste.
1. Erstellen Sie einen Kunden mit einem umfangreichen Adressbuch mit 1000 Adressen.
1. Navigieren Sie zum Frontend und fügen Sie das Produkt zum Warenkorb hinzu.
1. Öffnen Sie die Warenkorbseite.

<u>Erwartete Ergebnisse</u>:

Die Anzahl der Kundenadressen hat keinen Einfluss auf die Antwortzeit.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der Warenkorbseite dauert sehr lange.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
