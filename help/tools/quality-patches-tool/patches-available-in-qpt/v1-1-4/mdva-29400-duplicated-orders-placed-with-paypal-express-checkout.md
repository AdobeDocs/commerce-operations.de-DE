---
title: 'MDVA-29400: Doppelte Bestellungen bei PayPal Express Checkout'
description: Der Patch MDVA-29400 löst das Problem, dass duplizierte Bestellungen erstellt werden, wenn Kunden mit PayPal Express Checkout Bestellungen aufgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-29400. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.
feature: Checkout, Orders, Payments
role: Admin
exl-id: 6f7291d3-d554-4e4e-a55d-89ea2b9dea33
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# MDVA-29400: Doppelte Bestellungen bei PayPal Express Checkout

Der Patch MDVA-29400 löst das Problem, dass duplizierte Bestellungen erstellt werden, wenn Kunden mit PayPal Express Checkout Bestellungen aufgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-29400. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Duplizierte Bestellungen werden erstellt, wenn Benutzer Bestellungen mit PayPal Express Checkout aufgeben.

<u>Voraussetzungen</u>:

PayPal Express-Checkout aktiviert und konfiguriert.

<u>Zu reproduzierende Schritte</u>:

1. Produkt zum Warenkorb hinzufügen.
1. Gehen Sie zur Checkout-Seite und verwenden Sie PayPal Express als Zahlungsmethode.
1. Sie wird zur Seite &quot;paypal/Express/review/&quot;umgeleitet.
1. Bestellung aufgeben Sie werden auf die Erfolgsseite weitergeleitet.
1. Gehen Sie zurück zu PayPal/Express/review/ Seite.
1. Klicken Sie auf die Schaltfläche **Bestellung platzieren** .

<u>Erwartete Ergebnisse</u>:

Es wird nur eine Bestellung erstellt.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten den folgenden Fehler: *PayPal Express Checkout-Token existiert nicht*, aber die zweite Bestellung wurde erfolgreich aufgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
