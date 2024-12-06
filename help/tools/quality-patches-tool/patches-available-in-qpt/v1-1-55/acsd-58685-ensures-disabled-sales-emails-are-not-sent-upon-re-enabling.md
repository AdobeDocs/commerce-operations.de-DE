---
title: 'ACSD-58685: Deaktivierte Verkaufs-E-Mails werden bei der erneuten Aktivierung gesendet'
description: Wenden Sie den Patch ACSD-58685 an, um das Adobe Commerce-Problem zu beheben, bei dem bei Deaktivierung der E-Mail-Kommunikation initiierte Verkaufs-E-Mails gesendet werden, sobald die E-Mail-Kommunikation wieder aktiviert ist.
feature: Configuration
role: Admin, Developer
source-git-commit: db495f2dbf307f9da42b6dc4fc7bed1e6af1d307
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685: Deaktivierte Verkaufs-E-Mails werden bei der erneuten Aktivierung gesendet

Der Patch ACSD-58685 behebt das Problem, dass Verkaufs-E-Mails, die bei deaktivierter E-Mail-Kommunikation initiiert wurden, gesendet werden, sobald die E-Mail-Kommunikation wieder aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58685. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bei Deaktivierung der E-Mail-Kommunikation initiierte E-Mails werden nach der erneuten Aktivierung der E-Mail-Kommunikation gesendet.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]** und legen Sie **[!UICONTROL Disable Email Communications]** auf *[!UICONTROL No]* fest.
1. Navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]** und legen Sie **[!UICONTROL Asynchronous Sending]** auf *[!UICONTROL Yes]* fest.
1. Löschen Sie den Konfigurations-Cache.
1. Bestellung aufgeben.
1. Aktivieren Sie die E-Mail-Kommunikation.
1. Platzieren Sie eine andere Bestellung.
1. Führen Sie den Cron aus.

<u>Erwartete Ergebnisse</u>:

Nur die E-Mail für die zweite Bestellung wird gesendet.

<u>Tatsächliche Ergebnisse</u>:

E-Mails für die erste und zweite Bestellung werden gesendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
