---
title: 'ACSD-52287: Status der archivierten Bestellungen ändert sich nicht'
description: Wenden Sie den Patch ACSD-52287 an, um das Adobe Commerce-Problem zu beheben, bei dem sich der Status der archivierten Bestellungen nach der Übermittlung der Gutschrift nicht von „Abgeschlossen“ in „Geschlossen“ im Raster ändert.
feature: Orders, Checkout
role: Admin, Developer
exl-id: 012f49ba-fdc1-4e1e-87fe-7b9c661f231b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-52287: Status der archivierten Bestellungen ändert sich nicht

Mit dem Patch ACSD-52287 wird das Problem behoben, dass sich der Status der archivierten Bestellungen nach der Übermittlung der Gutschrift nicht *abgeschlossen* in *geschlossen* im Raster ändert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.38 installiert ist. Die Patch-ID ist ACSD-52287. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Status archivierter Bestellungen ändert sich nach der Übermittlung der Gutschrift nicht ** abgeschlossen *in* Geschlossen“ im Raster.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie *[!UICONTROL Asynchronous Indexing]*.
   * Navigieren Sie in der Seitenleiste Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Erweitern Sie im linken Bereich den Abschnitt **[!UICONTROL Advanced]** und wählen Sie darunter **[!UICONTROL Developer]**.
   * Erweitern Sie den Abschnitt **[!UICONTROL Grid Settings]** .
   * Setzen Sie *[!UICONTROL Asynchronous indexing]* auf *Ja*.
   * Klicken Sie auf **[!UICONTROL Save Config]**.
1. Konfigurieren Sie die *[!UICONTROL Order Archive]*.
   * Navigieren Sie in der Seitenleiste Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Erweitern Sie im linken Bereich den Abschnitt **[!UICONTROL Sales]** und wählen Sie darunter **[!UICONTROL Sales]**.
   * Erweitern Sie den Abschnitt **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]** .
   * Setzen Sie *[!UICONTROL Enable Archiving]* auf *Ja* (Belassen Sie den Rest der Konfigurationen als Standard).
   * Klicken Sie auf **[!UICONTROL Save Config]**.
1. Bestellung im Frontend.
1. Führen Sie die [!DNL cron] aus, damit die Reihenfolge in der *[!UICONTROL Admin Order Grid]* angezeigt wird.
1. Rechnung erstellen und die Bestellung versenden, um den Bestellstatus auf „Abgeschlossen *zu*.
1. Führen Sie die [!DNL cron] aus, um die *[!UICONTROL Sales Order Grid]* mit dem neuesten Bestellstatus zu aktualisieren.
1. Archivieren Sie die Bestellung.
1. Gehen Sie zum *[!UICONTROL Archived order grid]*.
1. Öffnen Sie die archivierte Bestellung und erstatten Sie die Bestellung offline, indem Sie eine [!UICONTROL Credit Memo] erstellen, um die [!UICONTROL Order status]: *Geschlossen* vorzunehmen.
1. Führen Sie die [!DNL cron] einige Male aus.
1. Überprüfen Sie den *[!UICONTROL Archived order grid]* auf den neuen Bestellstatus.

<u>Erwartete Ergebnisse</u>:

Die Reihenfolge wird als *Geschlossen“*.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird als &quot;*&quot;*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
