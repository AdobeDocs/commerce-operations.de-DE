---
title: 'ACSD-65777: Fehlendes Feld „types“ für Produktbildtypen in der GraphQL-Anfrage „MediaGallery“'
description: Wenden Sie den Patch ACSD-65777 an, um das Adobe Commerce-Problem zu beheben, bei dem das Feld „types“ für Produktbildtypen in der GraphQL-Anfrage „MediaGallery“ fehlte.
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 20866963-54a3-4859-9c2d-716945e37156
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
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
source-wordcount: '320'
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

   ```text
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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
