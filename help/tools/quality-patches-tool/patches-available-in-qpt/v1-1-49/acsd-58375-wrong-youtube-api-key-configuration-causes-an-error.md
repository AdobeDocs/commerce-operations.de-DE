---
title: "ACSD-58375: Falsch konfigurierter YouTube API-Schlüssel verursacht Fehler beim Hinzufügen von Videos auf Store-Ansichtsebene"
description: Wenden Sie den Patch ACSD-58375 an, um das Adobe Commerce-Problem zu beheben, bei dem die falsche Konfiguration des YouTube-API-Schlüssels beim Hinzufügen eines YouTube-Videos auf der Store-Ansichtsebene einen Fehler verursacht.
feature: Catalog Management, Configuration
role: Admin, Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-58735: Falsch konfigurierter YouTube API-Schlüssel verursacht Fehler beim Hinzufügen von Videos auf Store-Ansichtsebene

Der Patch ACSD-58735 behebt das Problem, bei dem eine falsche Konfiguration des YouTube-API-Schlüssels beim Hinzufügen eines YouTube-Videos auf der Store-Ansichtsebene einen Fehler verursacht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-58735. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine falsche Konfiguration des YouTube-API-Schlüssels verursacht einen Fehler beim Hinzufügen eines YouTube-Videos auf der Store-Ansichtsebene.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu Admin > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**.
1. Ändern Sie den *Umfang* in den *[!UICONTROL Main Website]* Level.
1. Fügen Sie den YouTube-API-Schlüssel hinzu.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Wählen Sie ein beliebiges Produkt aus und scrollen Sie zu *[!UICONTROL Images and Video]*. Klicken Sie auf **[!UICONTROL Add Video]**.
1. Kopieren Sie einen YouTube-Videolink und fügen Sie ihn in das Feld für den Videolink ein. Aus dem Feld verschieben

<u>Erwartete Ergebnisse</u>:

Der YouTube-API-Schlüssel hat einen globalen Umfang und ist auf der Website-Ebene ausgeblendet.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird ausgegeben: *Video wird aus folgendem Grund nicht angezeigt: API-Schlüssel ist ungültig. Bitte übergeben Sie einen gültigen API-Schlüssel*.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
