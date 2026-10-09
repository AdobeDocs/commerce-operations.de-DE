---
title: 'ACSD-58685: Bei der erneuten Aktivierung werden deaktivierte Verkaufs-E-Mails gesendet'
description: Wenden Sie den Patch ACSD-58685 an, um das Adobe Commerce-Problem zu beheben, bei dem Verkaufs-E-Mails, die initiiert werden, während die E-Mail-Kommunikation deaktiviert ist, gesendet werden, sobald die E-Mail-Kommunikation wieder aktiviert ist.
feature: Configuration
role: Admin, Developer
exl-id: 773c0e0e-92c3-42b1-8fbf-fcb05e0e8311
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%
---
# ACSD-58685: Bei der erneuten Aktivierung werden deaktivierte Verkaufs-E-Mails gesendet

Mit dem Patch ACSD-58685 wird das Problem behoben, dass Verkaufs-E-Mails, die initiiert werden, während die E-Mail-Kommunikation deaktiviert ist, gesendet werden, sobald die E-Mail-Kommunikation wieder aktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58685. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Verkaufs-E-Mails, die initiiert werden, während die E-Mail-Kommunikation deaktiviert ist, werden gesendet, sobald die E-Mail-Kommunikation erneut aktiviert wurde.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]** und setzen Sie **[!UICONTROL Disable Email Communications]** auf *[!UICONTROL No]*.
1. Navigieren Sie zu **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]** und setzen Sie **[!UICONTROL Asynchronous Sending]** auf *[!UICONTROL Yes]*.
1. Löschen Sie den Konfigurations-Cache.
1. Bestellung aufgeben.
1. E-Mail-Kommunikation aktivieren.
1. Geben Sie eine weitere Bestellung auf.
1. Lauf die Cron.

<u>Erwartete Ergebnisse</u>:

Es wird nur die E-Mail für die zweite Bestellung gesendet.

<u>Tatsächliche Ergebnisse</u>:

E-Mails für die erste und zweite Bestellung werden gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

[[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
