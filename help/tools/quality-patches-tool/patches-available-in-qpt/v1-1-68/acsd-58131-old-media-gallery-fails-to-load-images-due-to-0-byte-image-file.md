---
title: 'ACSD-58131: Laden von Bildern in der alten Mediensammlung aufgrund einer 0-Byte-Bilddatei fehlgeschlagen'
description: Wenden Sie den Patch ACSD-58131 an, um das Adobe Commerce-Problem zu beheben, bei dem die alte Mediensammlung Bilder nicht rendern kann, wenn ein 0-Byte-Bild im Verzeichnis vorhanden ist.
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131: Laden von Bildern in der alten Mediensammlung aufgrund einer 0-Byte-Bilddatei fehlgeschlagen

Mit dem Patch ACSD-58131 wird das Problem behoben, dass die alte Mediensammlung Bilder nicht rendern kann, wenn ein 0-Byte-Bild im Verzeichnis vorhanden ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-58131. Dieses Problem wird voraussichtlich in Adobe Commerce 2.5.0 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn ein 0-Byte-Bild im Verzeichnis der Mediensammlung platziert wird, kann die alte Mediensammlung keine Bilder rendern. Das aktualisierte System überspringt jetzt ungültige 0-Byte-Dateien, zeigt gültige Bilder erwartungsgemäß an und protokolliert eine Warnung für jede ungültige Datei.

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]**.
1. Setzen Sie **[!UICONTROL Enable Old Media Gallery]** auf *Ja*.
1. Platzieren Sie einige Bilder im `pub/media/wysiwyg`.
1. Erstellen Sie mit `touch pub/media/wysiwyg/empty_image.png` ein 0-Byte-Bild im selben Verzeichnis.
1. Fügen Sie ein Bild aus dem `wysiwyg` Verzeichnis über den Page Builder unter einem beliebigen Inhalt hinzu (z. B. einem CMS-Block):
   1. Erstellen Sie einen neuen Block. Gehen Sie zu **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]** und klicken Sie auf **[!UICONTROL Add New Block]**.
   1. Bearbeiten Sie den Inhaltsabschnitt mit Page Builder.
   1. Ziehen Sie unter **[!UICONTROL Layout]** eine neue **[!UICONTROL Row]** auf die Bühne.
   1. Erweitern Sie **[!UICONTROL Media]** und ziehen Sie einen **[!UICONTROL Image]** Platzhalter in die Zeile.
   1. Klicken Sie auf **[!UICONTROL Select from Gallery]**.
   1. Wählen Sie das `wysiwyg` Verzeichnis aus, wenn es nicht standardmäßig ausgewählt ist.

<u>Erwartete Ergebnisse</u>:

Die Mediensammlung bleibt auch dann funktionsfähig, wenn ein 0-Byte-Bild (oder eine andere Datei) vorhanden ist.

<u>Tatsächliche Ergebnisse</u>:

Die Mediensammlung kann aufgrund eines kritischen Fehlers, der bei der `wysiwyg` protokolliert wurde, keine Bilder aus dem `var/log/system.log` Verzeichnis laden:

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
