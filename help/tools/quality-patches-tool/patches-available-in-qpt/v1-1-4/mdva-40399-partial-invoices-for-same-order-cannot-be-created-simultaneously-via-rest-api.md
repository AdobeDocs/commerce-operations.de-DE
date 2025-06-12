---
title: 'MDVA-40399: Teilrechnungen für dieselbe Bestellung können nicht gleichzeitig über API erstellt werden'
description: Der Patch MDVA-40399 behebt das Problem, dass Teilrechnungen für dieselbe Bestellung nicht gleichzeitig über die REST-API erstellt werden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40399. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: REST, Invoices, Orders
role: Admin
exl-id: aa400a15-57b9-4f80-a49f-f4680b7e4705
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40399: Teilrechnungen für dieselbe Bestellung können nicht gleichzeitig über API erstellt werden

Der Patch MDVA-40399 behebt das Problem, dass Teilrechnungen für dieselbe Bestellung nicht gleichzeitig über die REST-API erstellt werden können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40399. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Teilrechnungen für dieselben Bestellungen können nicht gleichzeitig mit der REST-API erstellt werden.

<u>Voraussetzungen</u>:

Ein konfigurierbares Produkt mit mindestens zwei Varianten.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie beide Varianten des konfigurierbaren Produkts zum Warenkorb hinzu.
1. Bestellung aufgeben.
1. Erstellen Sie über die REST-API zwei Rechnungen gleichzeitig für die Bestellung.

<u>Erwartete Ergebnisse</u>:

* Beide Rechnungen müssen erfolgreich erstellt werden.
* `qty_invoiced` sollten für beide Rechnungen in der `sales_order_item` aktualisiert werden.
* Beide Produkte sollten über die fakturierte Menge verfügen.

<u>Tatsächliche Ergebnisse</u>:

* Beide Rechnungen wurden erfolgreich erstellt.
* `qty_invoiced` wird nicht für eine der Rechnungen in der `sales_order_item` aktualisiert.
* Auf der Admin-Seite **Auftragsansicht** wird die Rechnungsmenge nur für ein Produkt angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
