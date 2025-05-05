---
title: 'MDVA-41631: Fehler beim Abrufen von Bestellinformationen ohne optionalen Wert für „Telefon“'
description: Mit dem Patch MDVA-41631 wird das Problem behoben, bei dem Benutzende einen Fehler beim Abrufen von Bestellinformationen erhalten, ohne dass ein optionaler Wert für „Telefon“ durch  [!DNL GraphQL]. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
source-git-commit: 3f14d93eca09967e320aae4af5e94c6d0c16cd20
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-41631: Fehler beim Abrufen von Bestellinformationen ohne optionalen Wert für „Telefon“

Der Patch MDVA-41631 behebt das Problem, dass Benutzende einen Fehler beim Abrufen von Bestellinformationen erhalten, ohne dass der Wert „Telefon“ über [!DNL GraphQL] angegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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

    orders(filter:{number:{eq:"000000001"}})&lbrace;
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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum [!DNL Quality Patches Tool] finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
