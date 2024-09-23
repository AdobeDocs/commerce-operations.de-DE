---
title: "ACSD-53643: Die Summe der Bestellungen ist bei der Bestellung nicht korrekt."
description: Wenden Sie den Patch ACSD-53643 an, um das Adobe Commerce-Problem zu beheben, bei dem die Bestellung bei der Bestellung mit deaktivierten oder nicht vorrätigen Produkten einen falschen Gesamtwert aufweist.
feature: B2B
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: Die Gesamtsumme der Bestellungen ist bei der Bestellung nicht korrekt

Der Patch ACSD-53643 behebt das Problem, bei dem die Bestellung bei der Bestellung mit deaktivierten oder nicht vorrätigen Produkten einen falschen Gesamtwert aufweist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 installiert ist. Die Patch-ID ist ACSD-53643. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Bestellsumme ist falsch, wenn eine Bestellung mit deaktivierten oder nicht vorrätigen Produkten aufgegeben wird.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie *[!UICONTROL B2B]* und *[!UICONTROL Inventory]*.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** und legen Sie **[!UICONTROL Company]** = *Ja* und **[!UICONTROL Purchase Order]** = *Ja* fest.
1. Löschen Sie den Konfigurationscache.
1. Erstellen Sie ein neues Unternehmen, aktivieren Sie es und aktivieren Sie *[!UICONTROL Purchase order]* für das Unternehmen.
1. Erstellen Sie einen neuen Benutzer für das Unternehmen.
1. Erstellen Sie eine *Genehmigungsregel* , um alle Bestellungen von mehr als *1 USD* durch den Unternehmensadministrator zu genehmigen.
1. Erstellen Sie eine zusätzliche Quelle.
1. Melden Sie sich als neuer Unternehmensbenutzer an.
1. Fügen Sie zwei Produkte zum Warenkorb hinzu und geben Sie eine Bestellung auf.
1. Deaktivieren Sie das zweite Produkt.
1. Melden Sie sich als Unternehmensadministrator an.
1. Öffnen Sie die Bestellung und sehen Sie, dass die Bestellung sowohl Produkte als auch die Summe für beide Produkte enthält.
1. Validieren Sie die Bestellung.
1. Platzieren Sie die Bestellung.
1. Öffnen Sie die Bestelldetails.

<u>Erwartete Ergebnisse</u>:

* Die Reihenfolge kann nicht platziert werden, selbst wenn ein Produkt in der Reihenfolge *deaktiviert* oder *nicht vorrätig ist*.
* Schaltfläche *[!UICONTROL Place Order]* ist ausgeblendet.

<u>Tatsächliche Ergebnisse</u>:

Die aufgegebene Bestellung enthält nur das erste aktive Produkt, aber die Bestellsumme wird für beide Produkte berechnet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
