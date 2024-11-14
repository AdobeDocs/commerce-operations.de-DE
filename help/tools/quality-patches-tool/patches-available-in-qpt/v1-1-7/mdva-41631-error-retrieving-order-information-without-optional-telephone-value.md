---
title: '"MDVA-41631: Fehler beim Abrufen von Bestellinformationen ohne optionalen "Telefonwert"-Wert'
description: Der Patch MDVA-41631 behebt das Problem, dass Benutzer einen Fehler beim Abrufen von Bestellinformationen ohne optionalen "Telefonwert"über [!DNL GraphQL] erhalten. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
source-git-commit: 3f14d93eca09967e320aae4af5e94c6d0c16cd20
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-41631: Fehler beim Abrufen von Bestellinformationen ohne optionalen &quot;Telefonwert&quot;-Wert

Der Patch MDVA-41631 behebt das Problem, dass Benutzer einen Fehler beim Abrufen von Bestellinformationen ohne optionalen &quot;Telefonwert&quot;über [!DNL GraphQL] erhalten. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer erhalten einen Fehler beim Abrufen der Bestellinformationen ohne optionalen &quot;Telefonwert&quot;über [!DNL GraphQL].

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Store** > **Konfiguration** > **Kunden** > **Kundenkonfiguration** > **Name und Adressenoptionen** > **Telefon anzeigen** und legen Sie die Telefonnummer als optional fest.
1. Platzieren Sie eine Bestellung mit [!DNL GraphQL API] als angemeldeten Kunden.
   * Legen Sie die Telefonnummer nicht fest, wenn Sie die Abrechnungs- und Versandadressen festlegen. Befolgen Sie die Anweisungen in [[!DNL GraphQL] Checkout-Tutorial](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in unserer Entwicklerdokumentation.
1. Rufen Sie die Reihenfolge mit der [!DNL GraphQL] [`customerOrders` -Abfrage](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/) ab.

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Benutzer erhalten die Bestellinformationen.

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten den folgenden Fehler: *&quot;message&quot;: &quot;Interner Server-Fehler&quot;,*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum [!DNL Quality Patches Tool] finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
