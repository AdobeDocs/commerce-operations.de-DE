---
title: 'ACSD-65777: Fehlendes Feld „types“ für Produktbildtypen in der GraphQL-Anfrage „MediaGallery“'
description: Wenden Sie den Patch ACSD-65777 an, um das Adobe Commerce-Problem zu beheben, bei dem das Feld „types“ für Produktbildtypen in der GraphQL-Anfrage „MediaGallery“ fehlte.
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4f0ac23d70eed6d2ea0441d4c8aa8cfc3138ff04
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# ACSD-65777: Fehlendes **[!UICONTROL types]** für Produktbildtypen in der `MediaGallery` GraphQL-Anfrage

Mit dem Patch ACSD-65777 wird das Problem behoben, dass das Feld **[!UICONTROL types]** für Produktbildtypen in der `MediaGallery` GraphQL-Anfrage fehlte. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 installiert ist. Die Patch-ID ist ACSD-65777. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Feld **[!UICONTROL types]** fehlt für Produktbildtypen beim Abrufen von Mediendaten über die `MediaGallery` GraphQL-Anfrage.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt.
1. Laden Sie ein Bild in das Produkt hoch.
1. Rufen Sie die Mediendaten mit der folgenden GraphQL ab.

   ```
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Die `media_gallery` GraphQL-Benutzeroberfläche sollte das Feld **[!UICONTROL types]** enthalten.

<u>Tatsächliche Ergebnisse</u>:

Die `media_gallery` enthält nicht das **[!UICONTROL types]**.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
