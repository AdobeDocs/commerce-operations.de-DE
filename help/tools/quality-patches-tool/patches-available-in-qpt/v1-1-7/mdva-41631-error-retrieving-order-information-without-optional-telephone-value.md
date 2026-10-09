---
title: 'MDVA-41631: Fehler beim Abrufen von Bestellinformationen ohne optionalen Wert für „Telefon“'
description: Der Patch MDVA-41631 behebt das Problem, dass Benutzende einen Fehler beim Abrufen von Bestellinformationen erhalten, ohne dass der Wert „Telefon“ über [!DNL GraphQL] angegeben wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%
---
# MDVA-41631: Fehler beim Abrufen von Bestellinformationen ohne optionalen Wert für „Telefon“

Der Patch MDVA-41631 behebt das Problem, dass Benutzende einen Fehler beim Abrufen von Bestellinformationen erhalten, ohne dass der Wert „Telefon“ über [!DNL GraphQL] angegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.7 installiert ist. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzende erhalten einen Fehler beim Abrufen von Bestellinformationen ohne optionalen „Telefon“-Wert über [!DNL GraphQL].

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **Store** > **Configuration** > **Customers** > **Customer Configuration** > **Name and Address Options** > **Show Phone** und legen Sie die Telefonnummer als optional fest.
1. Aufgeben einer Bestellung mit [!DNL GraphQL API] als angemeldeter Kunde.
   * Legen Sie beim Festlegen der Rechnungs- und Versandadressen nicht die Telefonnummer fest. Befolgen Sie die Anweisungen im [[!DNL GraphQL] Checkout-Tutorial](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in unserer Entwicklerdokumentation.
1. Abrufen der Reihenfolge mithilfe der [!DNL GraphQL] [`customerOrders` Abfrage](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/).

<pre>
<code class="language-graphql">
&lbrace;
  customer &lbrace;
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}&#x200B;})&lbrace;
        items&lbrace;
          billing_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
shipping_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
        &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Benutzer erhalten die Bestellinformationen.

<u>Tatsächliche Ergebnisse</u>:

Benutzende erhalten folgende Fehlermeldung: *„message“: „Internal server error“,*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum [!DNL Quality Patches Tool] finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
