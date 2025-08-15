---
title: 'ACSD-50234: Falscher Kundenname in der Bestätigungs-E-Mail für Bestellungen mit [!DNL PayPal]'
description: Wenden Sie den Patch ACSD-50234 an, um das Problem mit Adobe Commerce zu beheben, bei dem der Kundenname in der Bestätigungs-E-Mail für Bestellungen mit falsch angezeigt wird [!DNL PayPal].
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 9a8a7cef-0166-4b4b-96a0-87fd4f1a0ef3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50234: Falscher Kundenname in der Bestätigungs-E-Mail für Bestellungen mit [!DNL PayPal]

Mit dem Patch ACSD-50234 wird das Problem behoben, dass der Kundenname in der Bestätigungs-E-Mail für Bestellungen, die mit [!DNL PayPal] aufgegeben werden, falsch angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID ist ACSD-50234. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bestätigungs-E-Mail für Bestellungen mit [!DNL PayPal] zeigt den falschen Kundennamen an.

<u>Schritte zur Reproduktion</u>

1. **[!UICONTROL PayPal Express Checkout]** aktivieren.
1. Navigieren Sie als Gast zum Frontend.
1. Fügen Sie Produkte zum Warenkorb hinzu.
1. Checkout mit **[!UICONTROL PayPal Express Checkout]** als Zahlungsmethode.
1. Überprüfen Sie die E-Mail zur Bestellbestätigung.

<u>Erwartete Ergebnisse</u>

Die E-Mail mit der Bestellbestätigung, die Rechnungs-E-Mail und alle versandbezogenen E-Mails sind an den Namen des Kunden gerichtet.

<u>Tatsächliche Ergebnisse</u>

Die E-Mail mit der Bestellbestätigung, die E-Mail mit der Rechnung und alle versandbezogenen E-Mails sind an *Gast* gerichtet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
