---
title: 'ACSD-50621: Stufenpreise für verschiedene Websites im freigegebenen Katalog sind nicht sichtbar'
description: Wenden Sie den ACSD-50621-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Stufenpreise für verschiedene Websites im freigegebenen Katalog nicht sichtbar sind, wenn Sie sie in einer Umgebung mit mehreren Websites bearbeiten.
feature: Catalog Management, Orders
role: Admin
exl-id: 2256dee7-e544-4723-9753-ba9cf7247880
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-50621: Stufenpreise für verschiedene Websites im freigegebenen Katalog sind nicht sichtbar

Mit dem Patch ACSD-50621 wird das Problem behoben, dass die Stufenpreise für verschiedene Websites im freigegebenen Katalog nicht sichtbar sind, wenn sie in einer Umgebung mit mehreren Websites bearbeitet werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-50621. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Stufenpreise für verschiedene Websites im freigegebenen Katalog sind nicht sichtbar, wenn sie in einer Umgebung mit mehreren Websites bearbeitet werden.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie die **[!UICONTROL Catalog Price Scope]** auf **[!UICONTROL Website]** fest.
1. Erstellen Sie eine zusätzliche Website, einen Store und eine Storeview.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es allen Websites zu.
1. Erstellen Sie einen benutzerdefinierten freigegebenen Katalog.
1. Navigieren Sie zu **[!UICONTROL Set Pricing and Structure]** für den benutzerdefinierten freigegebenen Katalog, den Sie erstellt haben.
1. In Schritt 1: Produkte für Katalog auswählen. Fügen Sie das von Ihnen erstellte einfache Produkt hinzu.
1. In Schritt 2: Benutzerdefinierte Preise festlegen und auf **[!UICONTROL Configure]** klicken.
1. Legen Sie unterschiedliche Stufenpreise für verschiedene Websites fest.
1. Wählen Sie **[!UICONTROL Done]** und klicken Sie auf **[!UICONTROL Generate Catalog]** und dann auf **[!UICONTROL Save]**.
1. Cron ausführen.
1. Navigieren Sie zu **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** und überprüfen Sie den Stufenpreis.

<u>Erwartete Ergebnisse</u>:

Alle zuvor konfigurierten Stufenpreise für verschiedene Websites sind vorhanden.

<u>Tatsächliche Ergebnisse</u>:

Zuvor konfigurierte Stufenpreise sind nicht vorhanden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
