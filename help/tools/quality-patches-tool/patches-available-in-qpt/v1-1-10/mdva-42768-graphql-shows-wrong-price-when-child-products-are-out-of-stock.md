---
title: 'MDVA-42768: GraphQL zeigt falschen Preis an, wenn untergeordnete Produkte nicht vorrätig sind'
description: Der Patch MDVA-42768 behebt das Problem, dass GraphQL den falschen Preis anzeigt, wenn die untergeordneten Produkte eines konfigurierbaren Produkts nicht vorrätig sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42768. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: GraphQL, Orders, Products
role: Admin
exl-id: 9f6ab418-2267-4548-952a-17dc8295f632
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%
---
# MDVA-42768: GraphQL zeigt falschen Preis an, wenn untergeordnete Produkte nicht vorrätig sind

Der Patch MDVA-42768 behebt das Problem, dass GraphQL den falschen Preis anzeigt, wenn die untergeordneten Produkte eines konfigurierbaren Produkts nicht vorrätig sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42768. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn die untergeordneten Produkte eines konfigurierbaren Produkts nicht vorrätig sind und die Einstellung Nicht vorrätige Produkte anzeigen aktiviert ist, zeigt die GraphQL-Abfrage den regulären Preis des Produkts als **0** an.

<u>Voraussetzungen</u>:

Beispieldaten werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie die Einstellung Nicht vorrätiges Produkt anzeigen in der Commerce-Admin, indem Sie zu **Stores** > **Configuration** > **Catalog** > **Inventory** gehen.
1. Erstellen Sie ein konfigurierbares Produkt und weisen Sie ihm ein einfaches untergeordnetes Produkt zu.
1. Legen Sie den Bestand des Varianten-(einfachen) Produkts auf „Nicht **&quot;**.
1. Neuindizieren.
1. Führen Sie die folgende GraphQL-Abfrage aus:

   ```GraphQL
   query {
     products(filter: { sku: { eq: "MH01" } }) {
       items {
         sku
         price_range {
           minimum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
           maximum_price {
             regular_price {
               value
               currency
             }
             final_price {
               value
               currency
             }
             discount {
               amount_off
               percent_off
             }
           }
         }
       }
     }
   }
   ```

1. Überprüfen Sie den Abschnitt Antwort `minimum_price` > `regular price`.

<u>Erwartete Ergebnisse</u>:

Der reguläre Mindestpreis wird nicht als 0 angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der reguläre Mindestpreis = 0 als Antwort.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
