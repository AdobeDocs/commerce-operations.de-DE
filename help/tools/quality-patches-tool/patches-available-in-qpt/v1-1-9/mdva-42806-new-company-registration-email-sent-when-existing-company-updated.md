---
title: 'MDVA-42806: Bei jeder Aktualisierung eines bestehenden Unternehmens wird eine neue E-Mail zur Firmenregistrierung gesendet'
description: Mit dem Patch MDVA-42806 wird das Problem behoben, dass jedes Mal, wenn ein vorhandenes Unternehmen über die REST-API aktualisiert wird, eine neue E-Mail zur Unternehmensregistrierung gesendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42806. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: REST, B2B, Communications, Companies
role: Admin
exl-id: 4fc2ee54-d88b-4940-b6ac-e25ad61e5c66
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42806: Bei jeder Aktualisierung eines bestehenden Unternehmens wird eine neue E-Mail zur Firmenregistrierung gesendet

Mit dem Patch MDVA-42806 wird das Problem behoben, dass jedes Mal, wenn ein vorhandenes Unternehmen über die REST-API aktualisiert wird, eine neue E-Mail zur Unternehmensregistrierung gesendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-42806. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Jedes Mal, wenn ein vorhandenes Unternehmen über die REST-API aktualisiert wird, wird eine neue E-Mail zur Unternehmensregistrierung gesendet.

<u>Voraussetzungen</u>:

B2B-Module installiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Unternehmenskonto.
1. Verwenden Sie `/V1&#x200B;/company&#x200B;/<company_id>` Endpunkt. Informationen zum Aktualisieren der erstellten Firma finden Sie unter [Aktualisieren der Firma](https://developer.adobe.com/commerce/webapi/rest/b2b/company-object/#update-the-company) in unserer Entwicklerdokumentation. Nachfolgend finden Sie eine Beispiel-Payload:

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

Es wird keine E-Mail mit der Meldung „Neue Unternehmensregistrierungsanfrage“ gesendet, da die API ein vorhandenes Unternehmen aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

Bei jeder API-Anfrage wird eine E-Mail mit der Meldung „Neue Unternehmensregistrierungsanfrage“ gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
