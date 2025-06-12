---
title: 'ACSD-45675: Der Produktexport verwendet Kategorienamen aus dem Standard-Ansichtsbereich des Stores'
description: Mit dem Patch ACSD-45675 wird das Problem behoben, dass der Produktexport Kategorienamen aus dem standardmäßigen Store-Ansichtsbereich verwendet. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 installiert ist. Die Patch-ID ist ACSD-45675. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: ebe72038-511d-43e1-bd65-e5b468342f05
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-45675: Der Produktexport verwendet Kategorienamen aus dem Standard-Ansichtsbereich des Stores

Mit dem Patch ACSD-45675 wird das Problem behoben, dass der Produktexport Kategorienamen aus dem standardmäßigen Store-Ansichtsbereich verwendet. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 installiert ist. Die Patch-ID ist ACSD-45675. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Produktexport verwendet Kategorienamen aus dem standardmäßigen Store-Ansichtsbereich.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine benutzerdefinierte Store-**[!UICONTROL Thai]** im Hauptspeicher.
1. **[!UICONTROL Thai]** Sie als Standard-Store-Ansicht der Haupt-Website.
1. Erstellen Sie die folgende Kategoriestruktur unter **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Wählen Sie die **[!UICONTROL Tea]** aus und ändern Sie die **[!UICONTROL Scope]** in **[!UICONTROL Thai]**.
1. Legen Sie die **[!UICONTROL Category Name]** als **[!UICONTROL ชาดำ]** fest.
1. Erstellen Sie eine einfache **[!UICONTROL SP001]** und weisen Sie die **[!UICONTROL Black]** zu.
1. Stellen Sie sicher, dass die Cron nicht läuft.
1. Führen Sie einen Produktexport durch. Nach SKU filtern und **[!UICONTROL SP001]** auswählen.
1. Überprüfen Sie die Spalte **[!UICONTROL categories]** in der exportierten CSV-Datei.

<u>Erwartete Ergebnisse</u>:

Da beim Export kein Store ausgewählt wurde, sollten Sie einen Kategoriepfad wie den folgenden erhalten: *[!UICONTROL Default Category/Tea/Black]*.

<u>Tatsächliche Ergebnisse</u>:

Kategoriepfad hat gemischte Sprachen: *[!UICONTROL Default Category/ชาดำ/Black]*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tools] > Nutzung](/help/tools/quality-patches-tool/usage.md) im Handbuch zum Quality Patches Tool.
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
