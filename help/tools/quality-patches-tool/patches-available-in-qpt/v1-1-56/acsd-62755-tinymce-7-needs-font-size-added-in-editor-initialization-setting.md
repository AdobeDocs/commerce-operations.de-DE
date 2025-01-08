---
title: 'ACSD-62755: [!DNL TinyMCE] 7 benötigt Schriftgröße und Schriftart, die zu den Editor-Initialisierungseinstellungen hinzugefügt werden'
description: Wenden Sie den Patch ACSD-62755 an, um das Adobe Commerce-Problem zu beheben, bei dem  [!DNL TinyMCE] 7 erfordert, dass *font size* und *font family* speziell in den Editor-Initialisierungseinstellungen hinzugefügt werden.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
source-git-commit: 4aba81ea12cc08370881d3cc108e94ba410a2198
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# ACSD-62755: [!DNL TinyMCE] 7 benötigt Schriftgröße und Schriftart, die zu den Editor-Initialisierungseinstellungen hinzugefügt werden

Mit dem Patch ACSD-62755 wird das Problem behoben, dass [!DNL TinyMCE] 7 *Selektoren* Schriftgröße) und *Schriftfamilie* erfordert, die speziell in den Editor-Initialisierungseinstellungen hinzugefügt werden müssen. Dieser Patch ist ab dem [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) verfügbar, in dem 1.1.56 installiert ist. Die Patch-ID ist ACSD-62755. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p10

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL TinyMCE] 7 erfordert, *Selektoren für* Schriftgröße“ und *Schriftfamilie* in den Editor-Initialisierungseinstellungen speziell hinzugefügt werden.

<u>Schritte zur Reproduktion</u>:

Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]** und wählen Sie *[!UICONTROL Show Editor]* aus.

<u>Erwartete Ergebnisse</u>:

*Schriftgröße* und *Schriftfamilie* werden im WYSIWYG-Editor angezeigt.

<u>Tatsächliche Ergebnisse</u>:

*Schriftgröße*-Auswahl fehlt im WYSIWYG-Editor.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
