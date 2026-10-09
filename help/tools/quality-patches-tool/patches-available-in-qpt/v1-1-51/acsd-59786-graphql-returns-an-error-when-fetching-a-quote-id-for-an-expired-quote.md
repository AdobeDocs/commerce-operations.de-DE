---
title: 'ACSD-59786: GraphQL gibt beim Abrufen einer „quote_id“ für ein abgelaufenes Angebot einen Fehler zurück'
description: Wenden Sie den Patch ACSD-59786 an, um das Adobe Commerce-Problem zu beheben, bei dem eine GraphQL-Abfrage beim Abrufen einer „quote_id“ für ein abgelaufenes Angebot einen Fehler zurückgibt.
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 792a7e9b-6519-5e99-a913-56c3dd2408da
    internal-label: Quotes
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
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
source-wordcount: '435'
ht-degree: 0%
---
# ACSD-59786: GraphQL gibt beim Abrufen eines `quote_id` für ein abgelaufenes Angebot einen Fehler zurück

Der Patch ACSD-59786 behebt das Problem, dass eine GraphQL-Abfrage beim Abrufen eines `quote_id` für ein abgelaufenes Angebot einen Fehler zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.51 installiert ist. Die Patch-ID ist ACSD-59786. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine GraphQL-Abfrage gibt beim Abrufen eines `quote_id` für ein abgelaufenes Angebot einen Fehler zurück.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **[!UICONTROL Companies]** und **[!UICONTROL Purchase Orders]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** und **[!UICONTROL Enable Company]** auf *Ja*.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]** und **[!UICONTROL Enable Purchase Orders]** auf *Ja* setzen.
1. Erstellen Sie eine neue Firma und setzen Sie **[!UICONTROL Enable Purchase Orders]** auf *Ja*.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es einer Kategorie zu.
1. Melden Sie sich mit dem Firmen-Admin-Konto bei Storefront an und erstellen Sie eine neue Bestellung mit **[!UICONTROL Purchase Order]** als Zahlungsmethode.
1. Ändern Sie die **[!UICONTROL Quote Lifetime (days)]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. Führen Sie den `bin/magento c:f` aus.
1. Wechseln Sie zum DB-`quote_table` und ändern Sie die `created_at` und `updated_at` Werte mit einem Tag in der Vergangenheit.
1. Führen Sie den `bin/magento cron:run --group="sales_clean_quotes` aus.
1. Führen Sie die unten angegebene GraphQL-Anfrage mit einem autorisierten Token für den Administrator aus, der die **[!UICONTROL Purchase Order]** erstellt:

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>Erwartete Ergebnisse</u>:

Die GraphQL-Abfrage gibt die `quote_id` zurück.

<u>Tatsächliche Ergebnisse</u>:

Die GraphQL-Abfrage gibt einen internen Server-Fehler zurück.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
