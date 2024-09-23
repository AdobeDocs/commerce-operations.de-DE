---
title: "MDVA-40399: Teilrechnungen für dieselbe Bestellung können nicht gleichzeitig über API erstellt werden"
description: Der Patch MDVA-40399 behebt das Problem, dass Teilrechnungen für die gleiche Bestellung nicht gleichzeitig über die Rest-API erstellt werden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40399. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40399: Teilrechnungen für dieselbe Bestellung können nicht gleichzeitig über API erstellt werden

Der Patch MDVA-40399 behebt das Problem, dass Teilrechnungen für die gleiche Bestellung nicht gleichzeitig über die Rest-API erstellt werden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40399. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Teilrechnungen für dieselben Bestellungen können nicht gleichzeitig mit der Rest-API erstellt werden.

<u>Voraussetzungen</u>:

Ein konfigurierbares Produkt mit mindestens zwei Varianten.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie beide Varianten des konfigurierbaren Produkts zum Warenkorb hinzu.
1. Platzieren Sie die Bestellung.
1. Erstellen Sie zwei Rechnungen gleichzeitig für die Bestellung über die Rest-API.

<u>Erwartete Ergebnisse</u>:

* Beide Rechnungen müssen erfolgreich erstellt werden.
* `qty_invoiced` sollte für beide Rechnungen in der Tabelle `sales_order_item` aktualisiert werden.
* Für beide Produkte sollte eine fakturierte Menge vorliegen.

<u>Tatsächliche Ergebnisse</u>:

* Beide Rechnungen wurden erfolgreich erstellt.
* `qty_invoiced` wird nicht mit einer der Rechnungen in der Tabelle `sales_order_item` aktualisiert.
* Auf der Seite **Bestellansicht** des Administrators wird die Rechnungsmenge nur für ein Produkt angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-) verfügbare Patches.
