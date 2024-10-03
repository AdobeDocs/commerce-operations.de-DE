---
title: "ACSD-59925: Sortieren von Elementen in [!UICONTROL Media Gallery] nach Position in GraphQL"
description: Wenden Sie den Patch ACSD-59925 an, um das Adobe Commerce-Problem zu beheben, bei dem Elemente in [!UICONTROL Media Gallery] nicht nach Position sortiert werden, was zu einer falschen Anzeigereihenfolge führt.
feature: Media, GraphQL
role: Admin, Developer
source-git-commit: 97e3ab77e7c8f5f1efd9b616b5e1d198a1b41ab0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-59925: Sortieren von Elementen in der [!UICONTROL Media Gallery] nach Position in GraphQL

Der Patch ACSD-59925 behebt das Problem, dass Elemente in den [!UICONTROL Media Gallery] nicht nach Position sortiert werden, was zu einer falschen Anzeigereihenfolge führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-59925. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Elemente in den [!UICONTROL Media Gallery] werden nicht nach Position sortiert, was zu einer falschen Anzeigereihenfolge führt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen/bearbeiten Sie das Produkt.
1. Fügen Sie zwei oder mehr Bilder hinzu und speichern Sie sie.
1. Bearbeiten Sie dasselbe Produkt, ziehen Sie dieses Mal jedoch das letzte Bild an die erste Position.
1. Speichern Sie das Produkt.
1. Neuindizieren.
1. Wechseln Sie zum GraphQL-Client.
1. GraphQL-Abfrage ausführen:

   ```GraphQL
   {
     products(filter: { sku: { eq: "24-MB01" } }) {
        items {
          name
          sku
          url_key
          stock_status
          media_gallery {
             __typename
             ... on ProductVideo {
               video_content {
                 video_url
                 video_title
                 __typename
               }
               __typename
             }
             ... on ProductImage {
               url
               __typename
             }
               position
               disabled
            }
         }
         total_count
         page_info {
         page_size
        }
      }
    }
   ```

<u>Erwartete Ergebnisse</u>:

Die Elemente in den `media_gallery` sind nach Position sortiert.

<u>Tatsächliche Ergebnisse</u>:

Elemente in der `media_gallery` werden nicht nach Position sortiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.