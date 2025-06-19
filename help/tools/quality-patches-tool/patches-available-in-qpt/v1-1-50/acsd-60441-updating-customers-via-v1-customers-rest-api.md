---
title: 'ACSD-60441: Beim Aktualisieren von Kundinnen und Kunden über den V1 [!DNL REST] Kunden-API-Endpunkt wird ein Fehler ausgegeben'
description: Wenden Sie den ACSD-60441-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem eine Aktualisierung von Kundinnen und Kunden über V1/customers [!DNL REST] API bei Verwendung des vom Backend generierten Integrations-Zugriffstokens einen Fehler auslöst.
feature: REST, Customers
role: Admin, Developer
exl-id: 3936c065-41a6-4860-8313-e054f9b23ac7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-60441: Beim Aktualisieren von Kunden über `V1/customers` API-Endpunkt [!DNL REST] wird ein Fehler ausgegeben

Mit dem Patch ACSD-60441 wird das Problem behoben, dass eine Aktualisierung von Kundinnen und Kunden über `V1/customers` [!DNL REST] API bei Verwendung des vom Backend generierten Integrations-Zugriffstokens einen Fehler verursacht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-60441. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Aktualisieren von Kundinnen und Kunden über `V1/customers` API-Endpunkt [!DNL REST] bei Verwendung des vom Backend generierten Integrations-Zugriffstokens wird ein Fehler ausgegeben.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Integration über den Administrator.
1. Senden Sie mithilfe des Integrations-Tokens eine [!DNL POST]-Anfrage an `rest/default/V1/customers/<customer_id>`.

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

Es wird die folgende Fehlermeldung angezeigt:

    „json
    {
    „message“: „Ein Kunde mit derselben E-Mail-Adresse ist bereits auf einer zugehörigen Website vorhanden.“,
    „trace“: …
    }
    &quot;

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
