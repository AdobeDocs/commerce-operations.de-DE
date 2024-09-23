---
title: 'ACSD-51149: Geplant [!UICONTROL ImportExport] mit aktiviertem [!UICONTROL Catalog Permissions] Invalidierung von Indizes'
description: Wenden Sie den Patch ACSD-51149 an, um das Adobe Commerce-Leistungsproblem zu beheben, bei dem die geplante [!UICONTROL ImportExport] mit aktiviertem [!UICONTROL Catalog Permissions] Indexer ungültig macht.
feature: Cache, Data Import/Export
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-51149: Geplant [!UICONTROL ImportExport] mit aktiviertem [!UICONTROL Catalog Permissions] ungültig macht Indexer

Der Patch ACSD-51149 behebt das Problem, dass der geplante [!UICONTROL ImportExport] mit aktiviertem [!UICONTROL Catalog Permissions] Indexer ungültig macht. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51149. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Geplant [!UICONTROL ImportExport] mit aktiviertem [!UICONTROL Catalog Permissions] ungültig macht Indexer.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie *[!UICONTROL Catalog Permissions]*.
1. Setzen Sie alle Indexer auf *[!UICONTROL Update by Schedule]*.
1. Erstellen Sie ein einfaches Produkt.
1. Exportieren Sie dieses Produkt über **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Laden Sie die exportierte CSV-Datei herunter und legen Sie sie in `<AC root folder>/var/import` ab.
1. Erstellen Sie einen geplanten Produktimport mit der heruntergeladenen CSV-Datei.
1. Führen Sie die vollständige Neuindizierung aus.
1. Überprüfen Sie den Indexstatus. Alle Indexer sollten den Status *[!UICONTROL Ready]* aufweisen.
1. Führen Sie den erstellten geplanten Import aus dem Raster aus.
1. Überprüfen Sie den Indexstatus erneut.

<u>Erwartete Ergebnisse</u>:

Alle Indexer befinden sich im Status &quot;*[!UICONTROL Ready]*&quot;.

<u>Tatsächliche Ergebnisse</u>:

Einige Indexer befinden sich im Status *[!UICONTROL Reindex Required]* .

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
