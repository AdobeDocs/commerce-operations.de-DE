---
title: 'ACSD-64113: Fehler in Admin beim Hochladen eines Bildes mit einer Breite, die kleiner ist als die Höhe, über [!DNL Media Gallery]'
description: Wenden Sie den ACSD-64113 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem in Admins Fehler auftreten, wenn Bilder hochgeladen werden, die im Vergleich zur Höhe (oder umgekehrt) relativ klein sind [!DNL Media Gallery].
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64113: Fehler in Admin beim Hochladen eines Bildes mit einer Breite, die kleiner ist als die Höhe, über [!DNL Media Gallery]

Mit dem Patch ACSD-64113 wird das Problem behoben, dass beim Hochladen von Bildern mit einer relativ kleinen Breite im Vergleich zu ihrer Höhe (oder umgekehrt) über die [!DNL Media Gallery] Fehler in der Admin-Instanz auftreten. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 installiert ist. Die Patch-ID ist ACSD-64113. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Administratoren haben Fehler, wenn sie Bilder hochladen, deren Breite im Vergleich zur Höhe (oder umgekehrt) über die [!DNL Media Gallery] relativ gering ist.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zu **[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]** und wählen Sie das **[!UICONTROL wysiwyg]** Verzeichnis aus.
1. Laden Sie das Bild mit einer relativ kleinen Breite im Vergleich zur Höhe hoch (oder umgekehrt).

<u>Erwartete Ergebnisse</u>:

Das Bild wird fehlerfrei hochgeladen.

<u>Tatsächliche Ergebnisse</u>:

1. Die folgende Fehlermeldung wird ausgegeben:

   *Ein technisches Problem mit dem Server hat einen Fehler verursacht. Versuchen Sie erneut, mit Ihrer Arbeit fortzufahren. Wenn das Problem weiterhin besteht, versuchen Sie es später erneut.*
1. `var/log/exception.log` enthält:

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   oder

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
