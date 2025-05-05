---
title: 'ACSD-47910: fehlende Bestellungen, Rechnungen, Lieferungen, Gutschriften in den jeweiligen Entitätsrastern'
description: Wenden Sie den ACSD-47910 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem in den entsprechenden Entitätsrastern Bestellungen, Rechnungen, Lieferungen und Gutschriften fehlen.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 09115cf3-62c3-425e-bc99-e8971398dd20
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47910: fehlende Bestellungen, Rechnungen, Lieferungen und Gutschriften in den entsprechenden Entitätsrastern

Mit dem Patch ACSD-47910 wird das Problem behoben, dass in den entsprechenden Entitätsrastern Bestellungen, Rechnungen, Lieferungen und Gutschriften fehlen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID ist ACSD-47910. Die Version, in der dieses Problem behoben wird, ist noch nicht verfügbar.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Fehlende Bestellungen, Rechnungen, Lieferungen und Gutschriften in den entsprechenden Entitätsrastern.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **[!UICONTROL Asynchronous indexing]** unter **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Geben Sie zwei Bestellungen auf.
1. Führen Sie den Cron aus, um diese Bestellungen mit dem Raster zu synchronisieren.
1. Öffnen Sie eine der Bestellungen und stellen Sie sie für die Fakturierung bereit. RECHNUNG NOCH NICHT EINREICHEN.
1. Erstellen Sie eine neue Bestellung, die im Frontend platziert werden kann. KLICKEN SIE NOCH NICHT AUF DIE SCHALTFLÄCHE BESTELLUNG AUFGEBEN .
1. Fügen Sie eine `sleep(30)` in die `foreach` unter `NotSyncedDataProvider::L43`.
1. `bin/magento cron:run` ausführen.
1. Bestellen Sie jetzt neu.
1. Rechnung der vorherigen Bestellung.
1. Führen Sie den Cron erneut aus und erwarten Sie, dass die neue Reihenfolge synchronisiert wird.
1. Navigieren Sie zum Bestellraster im Admin-Bereich.

<u>Erwartete Ergebnisse</u>:

Die neue Reihenfolge sollte im Bestellraster angezeigt werden.

<u>Tatsächliche Ergebnisse</u>:

Die vorherige Aktualisierung der Reihenfolge wurde mit dem Raster (**[!UICONTROL status: Processing]**) synchronisiert. Die neue Reihenfolge wird nie im Raster angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
