---
title: 'ACSD-57337: Admin-Benutzer mit Zugriffsbeschränkungen konnten alle Unternehmen im *Unternehmensnetz* anzeigen.'
description: Wenden Sie den Patch ACSD-57337 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites im *Unternehmen*-Raster aus anzeigen konnte.
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: 7a05d335-5ed8-460e-80c4-dbc51d06c5bd
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-57337: Admin-Benutzer mit Zugriffsbeschränkungen konnten alle Unternehmen im Raster *Unternehmen* anzeigen.

Der Patch ACSD-57337 behebt das Problem, dass ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites Unternehmen von allen Websites im Raster *Unternehmen* anzeigen kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48 installiert ist. Die Patch-ID ist ACSD-57337. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Admin-Benutzer mit Zugriffsbeschränkungen auf bestimmte Websites könnte Unternehmen von allen Websites im Raster *Unternehmen* anzeigen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine zusätzliche Website, einen Store und eine Storeübersicht.
1. Erstellen Sie einige Unternehmen, die verschiedenen Websites zugewiesen sind.
1. Erstellen Sie eine Admin-Benutzerrolle und legen Sie den Rollenbereich auf die erstellte Website fest.
1. Erstellen Sie einen Administrator und weisen Sie ihn der erstellten Rolle zu.
1. Melden Sie sich mit einem neuen Administrator an.
1. Öffnen Sie **[!UICONTROL Customers]** > **[!UICONTROL Companies]** und beobachten Sie die Liste der Unternehmen.

<u>Erwartete Ergebnisse</u>:

Die Unternehmen, die der zusätzlichen Website zugewiesen wurden, sind im Raster *Unternehmen* sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Alle Unternehmen sind im Raster *Unternehmen* sichtbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
