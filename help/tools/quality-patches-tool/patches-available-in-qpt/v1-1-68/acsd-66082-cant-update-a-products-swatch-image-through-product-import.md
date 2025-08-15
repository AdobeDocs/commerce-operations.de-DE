---
title: 'ACSD-66082: Das Musterbild eines Produkts kann nicht durch einen Produktimport aktualisiert werden'
description: Wenden Sie den Patch ACSD-66082 an, um das Adobe Commerce-Problem zu beheben, bei dem das Hochladen einer CSV-Datei mit dem Feld swatch_image, das auf EMPTY_VALUE zum Aufheben der Einstellung von Farbfeldbildern eingestellt ist, dazu führt, dass der Importvorgang mit einem Fehler fehlschlägt.
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 0bfff90e-5f1f-4c87-8a99-efc5bb0d814b
source-git-commit: e0d2e42b070591f3fefc0e9adb1bf5c1ba580fd9
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-66082: Das Musterbild eines Produkts kann nicht durch einen Produktimport aktualisiert werden

Mit dem Patch ACSD-66082 wird das Problem behoben, dass es nicht möglich war, das Musterbild eines Produkts durch einen Produktimport zu aktualisieren. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-66082. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Hochladen einer CSV-Datei mit dem `swatch_image` Feld `EMPTY_VALUE` zum Aufheben der Einstellung von Farbfeldbildern schlägt der Importvorgang mit einem Fehler fehl.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Klicken Sie auf den Abwärtspfeil neben der Schaltfläche **[!UICONTROL Add Product]** und wählen Sie **[!UICONTROL Simple Product]** aus. Setzen Sie den **[!UICONTROL SKU]** auf *ABC*.
1. Laden Sie ein PNG-Bild mit dem Namen *testing.png* in `var/import/images/` hoch.
1. Erstellen Sie eine CSV-Datei mit folgendem Inhalt:

   ```
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. Wechseln Sie zu **[!UICONTROL System]** > **[!UICONTROL Import]** , um die Datei zu importieren, indem Sie die folgenden Einstellungen anpassen:
   * **[!UICONTROL Entity type]**: *Produkte*
   * **[!UICONTROL Import Behavior]**: *Hinzufügen/Aktualisieren*
   * Klicken Sie auf **[!UICONTROL Choose File]** , um die im vorherigen Schritt erstellte CSV-Datei zum Importieren auszuwählen. Der Import ist erfolgreich und das Farbfeld wird hinzugefügt.
1. Aktualisieren Sie die CSV-Datei mit dem folgenden Inhalt:

   ```
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. Wiederholen Sie den Importvorgang.

<u>Erwartete Ergebnisse</u>:

Das Farbfeldbild ist nicht festgelegt.

<u>Tatsächliche Ergebnisse</u>:

Der Importvorgang gibt einen Fehler aus.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
