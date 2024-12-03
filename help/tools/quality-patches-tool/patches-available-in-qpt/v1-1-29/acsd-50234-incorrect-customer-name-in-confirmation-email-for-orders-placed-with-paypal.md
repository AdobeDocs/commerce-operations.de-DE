---
title: 'ACSD-50234: Falscher Kundenname in der Bestätigungs-E-Mail für Bestellungen, die mit [!DNL PayPal] aufgegeben wurden'
description: Wenden Sie den Patch ACSD-50234 an, um das Adobe Commerce-Problem zu beheben, bei dem der Kundenname in der Bestätigungs-E-Mail für Bestellungen mit  [!DNL PayPal] falsch angezeigt wird.
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 9a8a7cef-0166-4b4b-96a0-87fd4f1a0ef3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50234: Falscher Kundenname in der Bestätigungs-E-Mail für Bestellungen mit [!DNL PayPal]

Der Patch ACSD-50234 behebt das Problem, dass der Kundenname in der Bestätigungs-E-Mail für Bestellungen, die mit [!DNL PayPal] aufgegeben wurden, falsch angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID ist ACSD-50234. Beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Bestätigungs-E-Mail für Bestellungen, die mit [!DNL PayPal] aufgegeben wurden, zeigt den falschen Kundennamen an.

<u>Zu reproduzierende Schritte</u>

1. Aktivieren Sie **[!UICONTROL PayPal Express Checkout]**.
1. Navigieren Sie als Gast zum Frontend.
1. Produkte zum Warenkorb hinzufügen.
1. Checkout mit **[!UICONTROL PayPal Express Checkout]** als Zahlungsmethode.
1. Überprüfen Sie die E-Mail zur Bestellbestätigung.

<u>Erwartete Ergebnisse</u>

Die Bestätigungs-E-Mail, die Rechnungsemail und alle versandbezogenen E-Mails werden an den Namen des Kunden adressiert.

<u>Tatsächliche Ergebnisse</u>

Die Bestätigungs-E-Mail, die Rechnungsemail und alle versandbezogenen E-Mails werden an *Gast* adressiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
