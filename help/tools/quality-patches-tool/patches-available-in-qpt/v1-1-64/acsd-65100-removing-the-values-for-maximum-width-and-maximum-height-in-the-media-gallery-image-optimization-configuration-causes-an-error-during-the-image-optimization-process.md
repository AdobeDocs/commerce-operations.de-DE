---
title: 'ACSD-65100: Das Entfernen der [!UICONTROL Maximum Width]- und [!UICONTROL Maximum Height] in der [!UICONTROL Media Gallery Image Optimization] verursacht einen Fehler'
description: Wenden Sie den ACSD-65100-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem das Entfernen der [!UICONTROL Maximum Width]- und [!UICONTROL Maximum Height] in der [!UICONTROL Media Gallery Image Optimization]-Konfiguration einen Fehler während des Bildoptimierungsprozesses verursacht.
feature: Media
role: Admin, Developer
exl-id: 86197602-19a1-41c2-b129-1f695f303ce5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-65100: Das Entfernen der [!UICONTROL Maximum Width]- und [!UICONTROL Maximum Height] in der [!UICONTROL Media Gallery Image Optimization] verursacht einen Fehler

Mit dem Patch ACSD-65100 wird das Problem behoben, dass das Entfernen der **[!UICONTROL Maximum Width]**- und **[!UICONTROL Maximum Height]** in der **[!UICONTROL Media Gallery Image Optimization]**-Konfiguration einen Fehler während des Bildoptimierungsprozesses verursacht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 installiert ist. Die Patch-ID ist ACSD-65100. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Während des Bildoptimierungsprozesses tritt ein Fehler auf, wenn die Werte für **[!UICONTROL Maximum Width]** und **[!UICONTROL Maximum Height]** in der **[!UICONTROL Media Gallery Image Optimization]** entfernt werden.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]**.
1. Entfernen Sie die Werte für **[!UICONTROL Maximum Width]** und **[!UICONTROL Maximum Height]**.
1. Bereinigen Sie den Konfigurations-Cache.
1. Navigieren Sie zu **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Öffnen Sie eine beliebige Seite zur Bearbeitung.
1. Im Inhaltsbereich:
   1. Wählen Sie **[!UICONTROL Add Layout]** > **[!UICONTROL Row]** aus.
   1. Wählen Sie **[!UICONTROL Add Elements]** > **[!UICONTROL Text]** aus.
   1. Klicken Sie im WYSIWYG-Editor auf **[!UICONTROL Add Image]**.
   1. Laden Sie ein Bild hoch und wählen Sie **[!UICONTROL Add Selected]** aus.
1. Überprüfen Sie die `var/log/exception.log`.

<u>Erwartete Ergebnisse</u>:

Keine Fehler.

<u>Tatsächliche Ergebnisse</u>:

Es wird ein Fehler ähnlich dem folgenden protokolliert:

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
