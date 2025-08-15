---
title: 'ACSD-51149: Geplante [!UICONTROL ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] machen Indexer ungültig'
description: Wenden Sie den Patch ACSD-51149 an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem die geplanten [!UICONTROL ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] Indexer ungültig machen.
feature: Cache, Data Import/Export
role: Admin
exl-id: eafc69ab-ec81-4192-85f8-a235f0a131a9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-51149: Geplante [!UICONTROL ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] machen Indexer ungültig

Der Patch ACSD-51149 behebt das Problem, dass die geplanten [!UICONTROL ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] Indexer ungültig machen. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51149. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Geplante [!UICONTROL ImportExport] mit aktivierten [!UICONTROL Catalog Permissions] machen Indexer ungültig.

<u>Schritte zur Reproduktion</u>:

1. *[!UICONTROL Catalog Permissions]* aktivieren.
1. Setzen Sie alle Indexer auf *[!UICONTROL Update by Schedule]*.
1. Erstellen Sie ein einfaches Produkt.
1. Exportieren Sie dieses Produkt über **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Laden Sie die exportierte CSV-Datei herunter und legen Sie sie in `<AC root folder>/var/import` ab.
1. Erstellen Sie einen geplanten Produktimport mit der heruntergeladenen CSV-Datei.
1. Vollständige Neuindizierung ausführen.
1. Überprüfen Sie den Status der Indexer. Alle Indexer sollten sich im Status *[!UICONTROL Ready]* befinden.
1. Führen Sie den erstellten geplanten Import aus dem Raster aus.
1. Überprüfen Sie den Status der Indizes.

<u>Erwartete Ergebnisse</u>:

Alle Indexer befinden sich im Status *[!UICONTROL Ready]* .

<u>Tatsächliche Ergebnisse</u>:

Einige der Indexer befinden sich im Status *[!UICONTROL Reindex Required]* .

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
