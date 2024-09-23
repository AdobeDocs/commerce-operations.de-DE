---
title: "MDVA-42806: Bei jeder Aktualisierung eines bestehenden Unternehmens wird eine E-Mail zur Registrierung eines neuen Unternehmens gesendet."
description: Der Patch MDVA-42806 behebt das Problem, dass jedes Mal, wenn ein bestehendes Unternehmen über die REST-API aktualisiert wird, eine E-Mail zur Registrierung eines neuen Unternehmens gesendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42806. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: REST, B2B, Communications, Companies
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42806: Bei jeder Aktualisierung eines bestehenden Unternehmens wird eine E-Mail zur Registrierung eines neuen Unternehmens gesendet

Der Patch MDVA-42806 behebt das Problem, dass jedes Mal, wenn ein bestehendes Unternehmen über die REST-API aktualisiert wird, eine E-Mail zur Registrierung eines neuen Unternehmens gesendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42806. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Jedes Mal, wenn ein bestehendes Unternehmen über die REST-API aktualisiert wird, wird eine E-Mail zur Registrierung eines neuen Unternehmens gesendet.

<u>Voraussetzungen</u>:

B2B-Module installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Unternehmenskonto.
1. Verwenden Sie den Endpunkt `/V1&#x200B;/company&#x200B;/<company_id>` . Informationen zum Aktualisieren des erstellten Unternehmens finden Sie unter [Aktualisieren des Unternehmens](https://devdocs.magento.com/guides/v2.4/b2b/company-object.html#update-the-company) in unserer Entwicklerdokumentation. Nachfolgend finden Sie eine Beispiel-Payload:

```php
{
    "company": {
        "id": 2,
        "status": 1,
        "company_name": "Company",
        "company_email": "company@example.test",
        "street": [
            "Test"
        ],
        "city": "Test",
        "country_id": "US",
        "region_id": "1",
        "postcode": "12345",
        "telephone": "8009994301",
        "customer_group_id": 2,
        "sales_representative_id": 1,
        "super_user_id": 2
    }
}
```

<u>Erwartete Ergebnisse</u>:

Es wird keine E-Mail mit der Meldung &quot;Neue Registrierungsanfrage für Unternehmen&quot;gesendet, da die API ein vorhandenes Unternehmen aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Jedes Mal, wenn die API-Anfrage gesendet wird, wird eine E-Mail mit der Meldung &quot;Neue Registrierungsanfrage für Unternehmen&quot;gesendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
