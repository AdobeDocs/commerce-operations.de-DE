---
title: 'ACSD-57565: Im Bestellungs-Dashboard werden falsche Bestellinformationen angezeigt'
description: Wenden Sie den Patch ACSD-57565 an, um das Problem in Adobe Commerce zu beheben, bei dem im Bestell-Dashboard falsche Bestellinformationen angezeigt werden, bis der Zeitraum aktualisiert wird.
feature: Roles/Permissions
role: Admin, Developer
exl-id: dc4ad263-725e-4605-9b85-fc4305ab9a29
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-57565: Im Bestellungs-Dashboard werden falsche Bestellinformationen angezeigt

Mit dem Patch ACSD-57565 wird das Problem behoben, dass im Bestellungs-Dashboard falsche Bestellinformationen angezeigt werden, bis der Zeitraum aktualisiert wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID ist ACSD-57565. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden

## Problem

Im Bestell-Dashboard werden falsche Bestellinformationen angezeigt.

<u>Schritte zur Reproduktion</u>:

1. **[!UICONTROL dashboard charts]** aktivieren.
1. Bestellung erstellen und fakturieren.
1. Warten Sie nach der Bestellerstellung mindestens 24 Stunden.
1. Überprüfen Sie die **[!UICONTROL dashboard chart]**.
1. Notieren Sie sich die vollständige Bestellanzahl.
1. Ändern Sie die Zeit in *aktuellen Monat* und ändern Sie sie dann wieder zurück in *Heute*.

<u>Erwartete Ergebnisse</u>:

Das Dashboard-Diagramm sollte stets die richtigen Statistiken anzeigen.

<u>Tatsächliche Ergebnisse</u>:

Das Dashboard-Diagramm zeigt falsche Statistiken beim ersten Laden an. Die genauen Statistiken des Diagramms werden nach dem Zeitraum aktualisiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
