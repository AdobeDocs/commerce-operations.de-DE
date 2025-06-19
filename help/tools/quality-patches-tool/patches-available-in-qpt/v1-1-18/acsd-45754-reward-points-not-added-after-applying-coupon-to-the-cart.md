---
title: 'ACSD-45754: Prämienpunkte werden nach Anwendung des Gutscheins auf den Warenkorb nicht hinzugefügt'
description: Der Patch des ACSD-45754 löst das Problem, dass Belohnungspunkte nicht hinzugefügt werden, nachdem ein Coupon auf den Warenkorb angewendet wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45754. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
feature: Orders, Rewards, Shopping Cart
role: Admin
exl-id: 02f3bfc4-440b-4d77-adf5-0824d1b21073
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-45754: Prämienpunkte werden nach Anwendung des Gutscheins auf den Warenkorb nicht hinzugefügt

Der Patch des ACSD-45754 löst das Problem, dass Belohnungspunkte nicht hinzugefügt werden, nachdem ein Coupon auf den Warenkorb angewendet wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID ist ACSD-45754. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bonuspunkte werden nach dem Anwenden eines Coupons auf den Warenkorb nicht hinzugefügt.

<u>Voraussetzungen</u>:

Die PayPal-Zahlungsmethode ist konfiguriert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie die Prämienpunktwechselkurse unter **Speichern** > **Andere Einstellungen** > **Prämienwechselkurse**.
1. Erstellen Sie eine Preisregel für den Warenkorb mit einem Couponcode, um 100 Prämienpunkte für angemeldete Kunden anzuwenden.
1. Checken Sie ein Produkt als angemeldeter Kunde mit PayPal und dem Gutscheincode aus.
1. Überprüfen Sie den Verlauf der Belohnungspunkte unter dem Kundenkonto in der Admin Console.

<u>Erwartete Ergebnisse</u>:

Prämienpunkte werden dem Kunden gemäß der Preisregel hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

Dem Kunden werden keine Prämienpunkte hinzugefügt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
