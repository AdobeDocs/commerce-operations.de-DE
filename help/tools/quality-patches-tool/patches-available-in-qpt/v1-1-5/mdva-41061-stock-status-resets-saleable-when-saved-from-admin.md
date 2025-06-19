---
title: 'MDVA-41061: Bestandsstatus wird auf „verkaufsfähig“ zurückgesetzt, wenn Produkt vom Administrator gespeichert wurde'
description: Mit dem Patch MDVA-41061 wird das Problem behoben, dass der Lagerstatus auf „verkaufbar“ zurückgesetzt wird, wenn das Produkt vom Administrator gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41061. Die neueste Patch-Version ist in QPT 1.1.15 mit MDVA-41061-V3 Patch-ID verfügbar. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: ddbc30ef-bc88-4878-8bd8-6880823819a2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-41061: Bestandsstatus wird auf „verkaufsfähig“ zurückgesetzt, wenn Produkt vom Administrator gespeichert wurde

Mit dem Patch MDVA-41061 wird das Problem behoben, dass der Lagerstatus auf „verkaufbar“ zurückgesetzt wird, wenn das Produkt vom Administrator gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41061. Die neueste Patch-Version ist in QPT 1.1.15 mit MDVA-41061-V3 Patch-ID verfügbar. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Lagerstatus wird auf „verkaufbar“ zurückgesetzt, wenn das Produkt vom Administrator gespeichert wird.

<u>Voraussetzungen</u>:

Inventarmodule sind installiert.

<u>Schritte zur Reproduktion</u>:

1. Einfaches Produkt mit Menge = 1 erstellen.
1. Bestellen Sie mit dem in Schritt 1 erstellten Produkt.
1. Cron ausführen - Stellen Sie sicher, dass `inventory.reservations.updateSalabilityStatus` Warteschlange ausgeführt und der Produktlagerstatus in der `cataloginventory_stock_status`-Tabelle auf null geändert wurde.
1. Überprüfen Sie das Produkt im Frontend. Sie sollte als „Nicht **&quot; gekennzeichnet**.
1. Produkt ohne Änderungen im Admin-Bereich speichern.

<u>Erwartete Ergebnisse</u>:

* Der Lagerstatus sollte nicht aktualisiert werden.
* Das Produkt sollte **nicht vorrätig** am Frontend sein.

<u>Tatsächliche Ergebnisse</u>:

* Einfaches Produkt wird im Frontend mit **Auf Lager** gekennzeichnet.
* Benutzende erhalten *Die angeforderte Menge ist nicht verfügbar* Meldung, wenn sie versuchen, sie zum Warenkorb hinzuzufügen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
