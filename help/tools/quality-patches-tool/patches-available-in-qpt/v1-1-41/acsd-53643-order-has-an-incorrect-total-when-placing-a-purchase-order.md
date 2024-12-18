---
title: 'ACSD-53643: Bestellung hat eine falsche Summe bei der Bestellung'
description: Wenden Sie den ACSD-53643 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Bestellung eine falsche Summe aufweist, wenn Sie eine Bestellung mit deaktivierten oder nicht vorrätigen Produkten aufgeben.
feature: B2B
role: Admin, Developer
exl-id: 72b52695-ef3c-4143-9e77-901463d4a9ed
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# ACSD-53643: Bestellung hat eine falsche Summe bei der Bestellung

Der Patch von ACSD-53643 behebt das Problem, dass die Bestellung eine falsche Summe aufweist, wenn eine Bestellung mit deaktivierten oder nicht vorrätigen Produkten aufgegeben wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 installiert ist. Die Patch-ID ist ACSD-53643. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bestellsumme ist falsch, wenn eine Bestellung mit deaktivierten oder nicht vorrätigen Produkten aufgegeben wird.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie *[!UICONTROL B2B]* und *[!UICONTROL Inventory]*.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** und setzen Sie **[!UICONTROL Company]** = *Ja* und **[!UICONTROL Purchase Order]** = *Ja*.
1. Konfigurationscache löschen.
1. Erstellen Sie eine neue Firma, aktivieren Sie sie und aktivieren Sie *[!UICONTROL Purchase order]* für die Firma.
1. Erstellen Sie einen neuen Benutzer für das Unternehmen.
1. Erstellen Sie eine *Genehmigungsregel* um alle Bestellungen von mehr als *1 USD)* Unternehmensadministrator zu genehmigen.
1. Erstellen Sie eine zusätzliche Quelle.
1. Melden Sie sich als neuer Unternehmensbenutzer an.
1. Fügen Sie zwei Produkte zum Warenkorb hinzu und geben Sie eine Bestellung auf.
1. Deaktivieren Sie das zweite Produkt.
1. Melden Sie sich als Unternehmensadministrator an.
1. Öffnen Sie die Bestellung, und prüfen Sie, ob die Bestellung beide Produkte enthält und die Summe für beide Produkte gilt.
1. Validieren Sie die Bestellung.
1. Bestellung aufgeben.
1. Öffnen Sie die Bestelldetails.

<u>Erwartete Ergebnisse</u>:

* Bestellung kann nicht aufgegeben werden, selbst wenn ein Produkt in der Bestellung *deaktiviert* oder *nicht vorrätig*.
* *[!UICONTROL Place Order]* Schaltfläche ist ausgeblendet.

<u>Tatsächliche Ergebnisse</u>:

Die aufgegebene Bestellung enthält nur das erste aktive Produkt, aber die Bestellsumme wird für beide Produkte berechnet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
