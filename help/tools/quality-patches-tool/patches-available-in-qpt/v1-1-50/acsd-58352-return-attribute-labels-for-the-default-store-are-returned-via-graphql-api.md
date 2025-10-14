---
title: 'ACSD-58352: Rückgabeattributbeschriftungen für den Standardspeicher werden über die API  [!DNL GraphQL] .'
description: Wenden Sie den Patch ACSD-58352 an, um das Adobe Commerce-Problem zu beheben, bei dem Rückgabeattributbeschriftungen für den Standardspeicher über die API zurückgegeben werden [!DNL GraphQL]  wenn in der Anfragekopfzeile eine nicht standardmäßige Speicheransicht angegeben ist.
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-58352: Rückgabe-Attributbeschriftungen für den Standardspeicher werden über [!DNL GraphQL] API zurückgegeben

Mit dem Patch „ACSD-58352“ wird das Problem behoben, dass Rückgabeattributbeschriftungen für den Standardspeicher über [!DNL GraphQL] API zurückgegeben werden, wenn in der Anfragekopfzeile eine nicht standardmäßige Speicheransicht angegeben ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-58352. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Rückgabeattributbeschriftungen für den Standardspeicher werden über [!DNL GraphQL] API zurückgegeben.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die **[!UICONTROL Return Merchandising Authorization]**.
1. Erstellen Sie eine *[!UICONTROL Additional Store]* und eine *[!UICONTROL Store View]* unter der Standard-Website.
1. Bearbeiten Sie das Attribut **[!UICONTROL Reason for Return]** Rückgabe und fügen Sie Beschriftungen für alle Store-Ansichten hinzu.
1. Erstellen Sie eine *[!UICONTROL Order]*.
1. Erstellen Sie eine *[!UICONTROL Return]* für diese Bestellung. Stellen Sie sicher, dass sich die *[!UICONTROL Return]* im Status *[!UICONTROL Pending]* befindet.
1. Senden Sie eine [!DNL GraphQL]-Abfrage mit dem angegebenen nicht standardmäßigen [!UICONTROL Store View] in der -Kopfzeile:

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. Beobachten Sie die Antwort.

<u>Erwartete Ergebnisse</u>

Rückgabekennzeichnungen in der [!DNL GraphQL]-Antwort gelten für die im Anfrage-Header festgelegten [!UICONTROL Store View].

<u>Tatsächliche Ergebnisse</u>:

Rückgabekennzeichnungen in [!DNL GraphQL] Antwort gelten für die [!UICONTROL Store View].

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
