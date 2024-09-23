---
title: 'ACSD-60441: Beim Aktualisieren von Kunden über den API-Endpunkt V1/customer [!DNL REST] wird ein Fehler ausgegeben.'
description: Wenden Sie den Patch ACSD-60441 an, um das Adobe Commerce-Problem zu beheben, bei dem bei der Aktualisierung von Kunden über die API V1/customer [!DNL REST] API bei der Verwendung des vom Backend generierten Integrationszugriffs-Tokens ein Fehler ausgegeben wird.
feature: REST, Customers
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-60441: Beim Aktualisieren von Kunden über den API-Endpunkt `V1/customers` [!DNL REST] wird ein Fehler ausgegeben

Der Patch ACSD-60441 behebt das Problem, dass das Aktualisieren von Kunden über die API `V1/customers` [!DNL REST] bei Verwendung des vom Backend generierten Integrationszugriffstokens einen Fehler verursacht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-60441. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Beim Aktualisieren von Kunden über den API-Endpunkt `V1/customers` [!DNL REST] bei Verwendung des vom Backend generierten Integrationszugriffstokens wird ein Fehler ausgegeben.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Integration über den Administrator.
1. Senden Sie mit dem Integrations-Token eine [!DNL POST] -Anfrage an `rest/default/V1/customers/<customer_id>`.

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u>Erwartete Ergebnisse</u>:

Die Kundendaten werden aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler:

    &quot;json
    {
    &quot;message&quot;: &quot;Ein Kunde mit derselben E-Mail-Adresse ist bereits auf einer verknüpften Website vorhanden.&quot;,
    &quot;trace&quot;: ...
    
    &quot;

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
