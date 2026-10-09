---
title: 'ACSD-53098: Produkte im freigegebenen Katalog werden nicht im Frontend reflektiert'
description: Wenden Sie den Patch ACSD-53098 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte, die einem freigegebenen Katalog zugewiesen sind, beim Ausführen eines partiellen Index nicht im Frontend reflektiert werden.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
exl-id: 25230086-13b5-4b16-b50f-931e9e3d7102
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
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
source-wordcount: '442'
ht-degree: 0%
---
# ACSD-53098: Produkte im freigegebenen Katalog werden nicht im Frontend reflektiert

Mit dem Patch ACSD-53098 wird das Problem behoben, dass Produkte, die einem freigegebenen Katalog zugewiesen sind, beim Ausführen eines partiellen Index nicht im Frontend reflektiert werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.38 installiert ist. Die Patch-ID ist ACSD-53098. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produkte, die einem freigegebenen Katalog über die API zugewiesen wurden, werden nicht im Frontend angezeigt, nachdem der partielle Indexer den Cron-Auftrag gefolgt vom Consumer-Cron ausgeführt hat.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie [!DNL RabbitMQ] als Warteschlangendienst ein.
1. Wechseln Sie in den **[!UICONTROL Update on Schedule]**.
1. Erstellen Sie einen freigegebenen Katalog und weisen Sie ihn einem Unternehmen zu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es einer Kategorie zu. Führen Sie die partielle Neuindizierung aus:

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Verwenden Sie die folgende API-Anfrage, um das erstellte Produkt dem freigegebenen Katalog zuzuweisen.

   ```text
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Führen Sie den folgenden Cron aus, um die Warteschlangen zu leeren, und führen Sie die partielle Neuindizierung aus:

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Melden Sie sich beim Frontend als Benutzer des Unternehmens an.
1. Überprüfen Sie die Frontend-Kategorieseite.

<u>Erwartete Ergebnisse</u>:

Die neu zugewiesenen Produkte werden im Frontend angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die neu zugewiesenen Produkte werden nicht im Frontend angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
