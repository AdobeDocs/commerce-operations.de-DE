---
title: 'ACSD-60538: Attribute werden nicht korrekt angezeigt, wenn das Produkt in [!UICONTROL All Store Views] deaktiviert ist'
description: Wenden Sie den Patch ACSD-60538 an, um das Adobe Commerce-Problem zu beheben, bei dem die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt werden, wenn ein Produkt in „Alle Store-Ansichten“ deaktiviert und nur in bestimmten Store-Ansichtsbereichen aktiviert ist, sodass das Produkt nicht richtig angezeigt wird.
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
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
source-wordcount: '476'
ht-degree: 0%
---
# ACSD-60538: Attribute werden nicht korrekt angezeigt, wenn das Produkt in *[!UICONTROL All Store Views]* deaktiviert ist

Der Patch ACSD-60538 behebt das Problem, dass, wenn ein Produkt in *[!UICONTROL All Store Views]* deaktiviert und nur in bestimmten Bereichen der Store-Ansicht aktiviert ist, die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt werden, was dazu führt, dass das Produkt nicht richtig angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.51 installiert ist. Die Patch-ID ist ACSD-60538. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn ein Produkt in *[!UICONTROL All Store Views]* deaktiviert und nur in bestimmten Bereichen der Store-Ansicht aktiviert ist, werden die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt, was dazu führt, dass das Produkt nicht richtig angezeigt wird.

<u>Voraussetzungen</u>:

Das Inventar-Modul ist installiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit dem *color*-Attribut und drei untergeordneten Produkten (*blue*, *black* und *brown*).
1. Deaktivieren Sie zwei verknüpfte untergeordnete Produkte (*blau* und *schwarz*) im *[!UICONTROL All Store Views]*.
1. Zum Umfang **[!UICONTROL Store View]**.
1. Untergeordnete Produkte (*blau* und *schwarz*) *[!UICONTROL Store View]* Umfang aktivieren.
1. Führen Sie die folgende GraphQL-Anfrage aus:

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u>Erwartete Ergebnisse</u>:

Die GraphQL-Antwort enthält die Attributwerte für das untergeordnete zugehörige Produkt, das in *[!UICONTROL All Store Views]* deaktiviert und im *[!UICONTROL Store View]* aktiviert ist.

<u>Tatsächliche Ergebnisse</u>:

Die GraphQL-Antwort enthält leere Attributwerte für das untergeordnete verknüpfte Produkt, wenn das Produkt in *[!UICONTROL All Store Views]* deaktiviert und im *[!UICONTROL Store View]* aktiviert ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
