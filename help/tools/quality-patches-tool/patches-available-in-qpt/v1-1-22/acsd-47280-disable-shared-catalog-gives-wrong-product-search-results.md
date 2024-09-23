---
title: '''[!DNL ACSD-47280]: Durch Deaktivieren des freigegebenen Katalogs werden falsche Produktsuchergebnisse angezeigt.'
description: Wenden Sie den Patch [!DNL ACSD-47280] an, um das Problem zu beheben, dass die richtigen Suchergebnisse angezeigt werden, wenn die Funktion des freigegebenen Katalogs deaktiviert ist.
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: Das Deaktivieren des freigegebenen Katalogs führt zu falschen Produktsuchergebnissen

Der Patch [!DNL ACSD-47280] behebt die Anzeige der richtigen Suchergebnisse, wenn die Funktion [!DNL shared catalog] deaktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22 installiert ist. Die [!DNL patch ID] ist [!DNL ACSD-47280]. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie den [!DNL patch ID] als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Deaktivierung von [!DNL shared catalog] führt zu falschen Produktsuchergebnissen.

<u>Voraussetzungen</u>:

* [!DNL B2B] installierte Module

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zweite Website.
1. Weisen Sie der zweiten Website ein Produkt zu.
1. Überprüfen Sie die Produkte auf der **zweiten Website** mit [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Aktivieren Sie **[!UICONTROL Shared Catalog]** für den Standardwert [!DNL scope].
1. Die [!DNL GraphQL] -Anfrage zeigt keine Produkte für die zweite Website mehr an, was das richtige Ergebnis ist.
1. Wechseln Sie zur [!DNL scope] der zweiten Website und deaktivieren Sie **[!UICONTROL Company]**.

<u>Erwartete Ergebnisse</u>:

Die [!DNL GraphQL] -Anfrage sollte weiterhin Produkte für die zweite Website anzeigen.

<u>Tatsächliche Ergebnisse</u>:

Die [!DNL GraphQL] -Anfrage zeigt keine Produkte für die zweite Website an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
