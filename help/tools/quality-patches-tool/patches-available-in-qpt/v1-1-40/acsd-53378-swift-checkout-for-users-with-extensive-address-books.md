---
title: "ACSD-53378: Verbessertes Kassenerlebnis für Kunden mit umfangreichen Adressbüchern"
description: Wenden Sie den Patch ACSD-53378 an, um das Adobe Commerce-Problem zu beheben, bei dem Leistungsprobleme durch große Kundenadressenvolumen verursacht werden.
feature: Customers, Checkout
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-53378: Verbessertes Kassenerlebnis für Kunden mit umfangreichen Adressbüchern

Der Patch ACSD-53378 behebt das Problem, bei dem Leistungsprobleme durch große Kundenadressenvolumen verursacht werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 installiert ist. Die Patch-ID ist ACSD-53378. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Leistung von Adobe Commerce wird sehr langsam, wenn ein Kunde über eine große Anzahl von Adressen verfügt.

Wenn die Konfigurationsoption *[!UICONTROL Enable search address]* unter **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** aktiviert ist, wird das vollständige Adressbuch des Kunden nicht mehr vollständig verarbeitet. Die Anzahl der verarbeiteten Kundenadressen wird durch die Einstellung *[!UICONTROL Customer Addresses Limit]* unter **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** bestimmt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt aus Admin.
1. Erstellen Sie einen Kunden mit einem umfangreichen Adressbuch mit 1000 Adressen.
1. Navigieren Sie zum Frontend und fügen Sie das Produkt zum Warenkorb hinzu.
1. Öffnen Sie die Warenkorbseite.

<u>Erwartete Ergebnisse</u>:

Die Anzahl der Kundenadressen hat keine Auswirkungen auf die Antwortzeit.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der Warenkorbseite dauert sehr lange.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
