---
title: "MDVA-38929: Rechnung mit FPT zeigt falsche Summe an"
description: Der Patch MDVA-38929 löst das Problem, dass die Rechnung mit FPT einen falschen Gesamtwert anzeigt, wenn die Bestellung mit einem Store-Guthaben beglichen wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38929. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Invoices, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-38929: Rechnung mit FPT zeigt falsche Summe an

Der Patch MDVA-38929 löst das Problem, dass die Rechnung mit FPT einen falschen Gesamtwert anzeigt, wenn die Bestellung mit einem Store-Guthaben beglichen wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38929. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Rechnung mit FPT zeigt einen falschen Gesamtwert an, wenn die Bestellung mit einem Store-Guthaben bezahlt wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen Kunden und stellen Sie sicher, dass der Kunde über ausreichend Guthaben verfügt, um die Bestellung abzudecken.
1. Aktivieren Sie FPT und fügen Sie einem Produkt FPT hinzu.
1. Melden Sie sich vom Frontend an, wie der Kunde gerade erstellt hat.
1. Fügen Sie das Produkt mit FPT zum Warenkorb hinzu.
1. Checkout und bezahlen mit Gutschrift. Es sollte sich um einen Nulllohnauftrag handeln.
1. Gehen Sie zu Bestellungen und berechnen Sie die Bestellung manuell.
1. Überprüfen Sie die Rechnungsgesamtsumme.

<u>Erwartete Ergebnisse</u>:

* Die Rechnungsgesamtsumme ist null.
* Der bezahlte Bestellgesamtbetrag ist null.

<u>Tatsächliche Ergebnisse</u>:

* Die Rechnungsgesamtsumme zeigt weiterhin den FPT-Betrag an.
* Der gezahlte Gesamtbetrag zeigt weiterhin den FPT-Betrag an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
