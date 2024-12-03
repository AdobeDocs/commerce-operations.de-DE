---
title: 'ACSD-58352: Rückgabeattributbeschriftungen für den Standardspeicher werden über die API [!DNL GraphQL] zurückgegeben.'
description: 'Wenden Sie den Patch ACSD-58352 an, um das Adobe Commerce-Problem zu beheben, bei dem Rückgabeattributbeschriftungen für den Standardspeicher über die API zurückgegeben werden, wenn eine nicht standardmäßige Store-Ansicht im Anfrageheader angegeben ist. [!DNL GraphQL] '
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-58352: Rückgabe der Attributbeschriftungen für den Standardspeicher werden über die API [!DNL GraphQL] zurückgegeben

Der Patch ACSD-58352 behebt das Problem, dass Rückgabeattributbeschriftungen für den Standardspeicher über die API [!DNL GraphQL] zurückgegeben werden, wenn eine nicht standardmäßige Store-Ansicht im Anfrageheader angegeben ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-58352. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Rückgabeattributbeschriftungen für den Standardspeicher werden über die API [!DNL GraphQL] zurückgegeben.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die **[!UICONTROL Return Merchandising Authorization]**.
1. Erstellen Sie eine *[!UICONTROL Additional Store]* und eine *[!UICONTROL Store View]* unter der Standardwebsite.
1. Bearbeiten Sie das Attribut **[!UICONTROL Reason for Return]** return und fügen Sie Beschriftungen für alle Store-Ansichten hinzu.
1. Erstellen Sie eine *[!UICONTROL Order]*.
1. Erstellen Sie eine *[!UICONTROL Return]* für diese Bestellung. Stellen Sie sicher, dass der *[!UICONTROL Return]* den Status *[!UICONTROL Pending]* aufweist.
1. Senden Sie eine Customer [!DNL GraphQL] -Abfrage mit dem angegebenen nicht standardmäßigen [!UICONTROL Store View] in der Kopfzeile:

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

Rückgabebeschriftungen in der Antwort [!DNL GraphQL] beziehen sich auf die im Anfrageheader festgelegte [!UICONTROL Store View].

<u>Tatsächliche Ergebnisse</u>:

Rückgabebeschriftungen in der Antwort [!DNL GraphQL] beziehen sich auf den Standardwert [!UICONTROL Store View].

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
