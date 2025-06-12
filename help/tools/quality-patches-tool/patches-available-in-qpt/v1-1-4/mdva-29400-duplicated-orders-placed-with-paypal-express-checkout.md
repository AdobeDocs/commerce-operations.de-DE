---
title: 'MDVA-29400: Duplizierte Bestellungen mit PayPal Express Checkout'
description: Der MDVA-29400 Patch löst das Problem, dass doppelte Bestellungen erstellt werden, wenn Kunden Bestellungen mit PayPal Express Checkout aufgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-29400. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.
feature: Checkout, Orders, Payments
role: Admin
exl-id: 6f7291d3-d554-4e4e-a55d-89ea2b9dea33
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# MDVA-29400: Duplizierte Bestellungen mit PayPal Express Checkout

Der MDVA-29400 Patch löst das Problem, dass doppelte Bestellungen erstellt werden, wenn Kunden Bestellungen mit PayPal Express Checkout aufgeben. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-29400. Beachten Sie, dass das Problem in Adobe Commerce 2.4.1 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Duplizierte Bestellungen werden erstellt, wenn Benutzer Bestellungen mit dem PayPal Express Checkout aufgeben.

<u>Voraussetzungen</u>:

PayPal Express-Checkout aktiviert und konfiguriert.

<u>Schritte zur Reproduktion</u>:

1. Produkt zum Warenkorb hinzufügen.
1. Gehen Sie auf die Checkout-Seite und verwenden Sie PayPal Express als Zahlungsmethode.
1. Es wird zu PayPal/Express/review/page weitergeleitet.
1. Bestellung aufgeben. Sie werden zur Erfolgsseite weitergeleitet.
1. Zurück zu PayPal/express/review/page.
1. Klicken Sie auf die Schaltfläche **Bestellung aufgeben**.

<u>Erwartete Ergebnisse</u>:

Es wird nur eine Bestellung erstellt.

<u>Tatsächliche Ergebnisse</u>:

Sie erhalten die folgende Fehlermeldung: *PayPal Express Checkout Token existiert nicht* aber die zweite Bestellung wurde erfolgreich platziert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
