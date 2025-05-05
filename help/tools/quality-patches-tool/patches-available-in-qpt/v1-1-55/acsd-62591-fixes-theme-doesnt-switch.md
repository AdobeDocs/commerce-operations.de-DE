---
title: 'ACSD-62591: Design wechselt nicht, wenn **[!UICONTROL User Agent Rules]** konfiguriert ist'
description: Wenden Sie den Patch ACSD-62591 an, um das Adobe Commerce-Problem zu beheben, bei dem das Design nicht richtig wechselt, wenn die **[!UICONTROL User Agent Rules]** konfiguriert sind.
feature: Themes
role: Admin, Developer
exl-id: 7b206b25-8918-40a6-a956-d38d5058d38f
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# ACSD-62591: Design wechselt nicht richtig, wenn es konfiguriert [!UICONTROL User Agent Rules]

Der Patch ACSD-62591 behebt das Problem, dass das Design nicht richtig wechselt, wenn die **[!UICONTROL User Agent Rules]** konfiguriert sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-62591. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Design wechselt nicht richtig, wenn die **[!UICONTROL User Agent Rules]** konfiguriert sind.

<u>Schritte zur Reproduktion</u>:

1. Öffnen Sie Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Bearbeiten eines Store-Ansichtsdesigns.
1. Legen Sie `/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i` in **[!UICONTROL User Agent Rules]** fest und wählen Sie ein anderes Design.
1. Änderungen speichern und Caches löschen.
1. Öffnen Sie eine Storefront-Seite auf einem Mobilgerät.
1. Öffnen Sie dieselbe Seite über einen Desktop-Browser.

<u>Erwartete Ergebnisse</u>:

Der Desktop-Browser und das Mobilgerät zeigen Seiten mit ihren jeweiligen Designs an.

<u>Tatsächliche Ergebnisse</u>:

Der Desktop-Browser zeigt die zwischengespeicherte Seite mit dem mobilen Design an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.

