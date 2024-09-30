---
title: 'ACSD-57565: Das Dashboard für die Bestellung zeigt falsche Bestellinformationen an.'
description: Wenden Sie den Patch ACSD-57565 an, um das Adobe Commerce-Problem zu beheben, bei dem das Bestell-Dashboard falsche Bestellinformationen anzeigt, bis der Zeitraum aktualisiert wurde.
feature: Roles/Permissions
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-57565: Das Dashboard für Bestellungen zeigt falsche Bestellinformationen an

Der Patch ACSD-57565 behebt das Problem, dass das Bestell-Dashboard falsche Bestellinformationen anzeigt, bis der Zeitraum aktualisiert wurde. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID ist ACSD-57565. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden der Patch-ID als Suchschlüsselwort, um den Patch zu finden

## Problem

Im Dashboard für Bestellungen werden falsche Bestellinformationen angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie **[!UICONTROL dashboard charts]**.
1. Erstellen Sie eine Bestellung und rechnen Sie sie aus.
1. Warten Sie mindestens 24 Stunden nach der Erstellung der Bestellung.
1. Überprüfen Sie die **[!UICONTROL dashboard chart]** -Daten.
1. Notieren Sie sich die vollständige Bestellanzahl.
1. Ändern Sie die Zeit in den *aktuellen Monat* und ändern Sie ihn dann wieder zurück in *heute*.

<u>Erwartete Ergebnisse</u>:

Das Dashboard-Diagramm sollte stets die korrekten Statistiken anzeigen.

<u>Tatsächliche Ergebnisse</u>:

Das Dashboard-Diagramm zeigt beim ersten Laden falsche Statistiken an. Die genauen Statistiken der Grafik werden nach dem Zeitraum aktualisiert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
