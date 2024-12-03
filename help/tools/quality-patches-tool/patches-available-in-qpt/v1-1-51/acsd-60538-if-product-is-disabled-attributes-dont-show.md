---
title: 'ACSD-60538: Attribute werden nicht korrekt angezeigt, wenn das Produkt in [!UICONTROL All Store Views] deaktiviert ist'
description: Wenden Sie den Patch ACSD-60538 an, um das Adobe Commerce-Problem zu beheben. Wenn ein Produkt in "Alle Store-Ansichten"deaktiviert und nur in bestimmten Speicheransichtsbereichen aktiviert ist, werden die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt, sodass das Produkt nicht richtig angezeigt wird.
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538: Attribute werden nicht korrekt angezeigt, wenn das Produkt in *[!UICONTROL All Store Views]* deaktiviert ist

Der Patch ACSD-60538 behebt das Problem, dass die Produktattribute in der GraphQL-Antwort nicht richtig angezeigt werden, wenn ein Produkt in *[!UICONTROL All Store Views]* deaktiviert und nur in bestimmten Bereichen der Store-Ansicht aktiviert ist, sodass das Produkt nicht richtig angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 installiert ist. Die Patch-ID ist ACSD-60538. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Wenn ein Produkt in *[!UICONTROL All Store Views]* deaktiviert und nur in bestimmten Bereichen der Store-Ansicht aktiviert ist, werden die Produktattribute in der GraphQL-Antwort nicht korrekt angezeigt, sodass das Produkt nicht ordnungsgemäß angezeigt wird.

<u>Voraussetzungen</u>:

Das Lagerbestandsmodul ist installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit dem Attribut *Farbe* und drei untergeordneten Produkten (*blau*, *schwarz* und *braun*).
1. Deaktivieren Sie zwei zugehörige untergeordnete Produkte (*blue* und *black*) im Bereich *[!UICONTROL All Store Views]* .
1. Wechseln Sie zum Bereich **[!UICONTROL Store View]** .
1. Aktivieren Sie untergeordnete Produkte (*blue* und *black*) im Bereich *[!UICONTROL Store View]*.
1. Führen Sie die folgende GraphQL-Anforderung aus:

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

Die GraphQL-Antwort enthält die Attributwerte für das untergeordnete verknüpfte Produkt, das unter *[!UICONTROL All Store Views]* deaktiviert und im Gültigkeitsbereich *[!UICONTROL Store View]* aktiviert ist.

<u>Tatsächliche Ergebnisse</u>:

Die GraphQL-Antwort weist leere Attributwerte für das untergeordnete verknüpfte Produkt auf, wenn das Produkt für *[!UICONTROL All Store Views]* deaktiviert und für den Bereich *[!UICONTROL Store View]* aktiviert ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
