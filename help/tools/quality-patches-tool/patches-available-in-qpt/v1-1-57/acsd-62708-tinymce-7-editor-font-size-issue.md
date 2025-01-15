---
title: 'Schriftgröße des ACSD-62708: [!DNL TinyMCE] -Editors im Admin-Bedienfeld zeigt PT'
description: Wenden Sie den Patch ACSD-62708 an, um das Adobe Commerce-Problem zu beheben, bei dem die  [!DNL TinyMCE] 7-Editor-Schriftgröße in der Admin-Liste PT und nicht PX anzeigt. Jetzt können Sie auch die Schriftgröße in PX anstelle von PT festlegen.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: ecb04a058e858580dfbc7a1edcd319423be9eeaa
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# ACSD-62708: Schriftgröße des [!DNL TinyMCE] 7-Editors im Admin-Bedienfeld zeigt PT

Mit dem Patch ACSD-62708 wird das Problem behoben, dass die Schriftgröße des [!DNL TinyMCE] 7-Editors im Admin-Bedienfeld in PT anstelle von PX angezeigt wird. Mit diesem Patch können Sie die Schriftgröße in PX festlegen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-62708. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der [!DNL TinyMCE] 7-Editor im Admin-Bedienfeld zeigt die Schriftgröße in PT anstelle von PX an.

<u>Schritte zur Reproduktion</u>:

1. Öffnen Sie die Seite zur Produktbearbeitung im Admin-Bedienfeld.
1. Erweitern Sie den Abschnitt [!UICONTROL Content] .
1. Überprüfen Sie die Steuerelemente für Schriftarten im [!DNL TinyMCE].

<u>Erwartete Ergebnisse</u>:

Die Schriftgröße muss in Pixel angegeben werden.

<u>Tatsächliche Ergebnisse</u>:

Die Schriftgröße ist PT.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
