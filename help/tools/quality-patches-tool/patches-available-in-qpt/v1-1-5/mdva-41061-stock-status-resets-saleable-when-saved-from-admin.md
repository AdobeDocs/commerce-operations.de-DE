---
title: "MDVA-41061: Der Lagerstatus wird beim Speichern des Produkts unter Admin auf verkäuflich zurückgesetzt."
description: Der Patch MDVA-41061 behebt das Problem, dass der Lagerstatus beim Speichern des Produkts vom Administrator auf verkäuflich zurückgesetzt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41061. Die neueste Patch-Version ist in QPT 1.1.15 mit der Patch-ID MDVA-41061-V3 verfügbar. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-41061: Der Lagerstatus wird auf verkäuflich zurückgesetzt, wenn das Produkt über Admin gespeichert wird

Der Patch MDVA-41061 behebt das Problem, dass der Lagerstatus beim Speichern des Produkts vom Administrator auf verkäuflich zurückgesetzt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 installiert ist. Die Patch-ID lautet MDVA-41061. Die neueste Patch-Version ist in QPT 1.1.15 mit der Patch-ID MDVA-41061-V3 verfügbar. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Lagerstatus wird beim Speichern des Produkts vom Administrator auf verkäuflich zurückgesetzt.

<u>Voraussetzungen</u>:

Die Inventarmodule sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein einfaches Produkt mit Menge = 1.
1. Platzieren Sie eine Bestellung mithilfe des in Schritt 1 erstellten Produkts.
1. cron ausführen - Stellen Sie sicher, dass die Warteschlange `inventory.reservations.updateSalabilityStatus` ausgeführt wird und der Produktstatus in der Tabelle `cataloginventory_stock_status` auf null geändert wurde.
1. Überprüfen Sie das Produkt auf der Vorderseite. Sie sollte als **Nicht auf Lager** markiert werden.
1. Speichern Sie das Produkt in der Admin-Konsole ohne Änderungen.

<u>Erwartete Ergebnisse</u>:

* Der Lagerstatus sollte nicht aktualisiert werden.
* Das Produkt sollte auf der Vorderseite **nicht auf Lager** sein.

<u>Tatsächliche Ergebnisse</u>:

* Einfaches Produkt wird als **Auf Lager** an der Vorderseite gekennzeichnet.
* Benutzer erhalten die Meldung *Die angeforderte Menge ist nicht verfügbar* , wenn sie versuchen, sie zum Warenkorb hinzuzufügen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
