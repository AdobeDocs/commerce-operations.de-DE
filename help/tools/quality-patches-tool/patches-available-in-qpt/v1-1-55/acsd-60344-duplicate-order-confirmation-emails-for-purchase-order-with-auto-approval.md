---
title: 'ACSD-60344: Bei Verwendung von [!UICONTROL Purchase Order] mit automatischer Validierung doppelte Bestellbestätigungs-E-Mails'
description: Wenden Sie den Patch ACSD-60344 an, um das Adobe Commerce-Problem zu beheben, bei dem doppelte E-Mails zur Bestellbestätigung gesendet werden, wenn ein [!UICONTROL Purchase Order] mit automatischer Genehmigung verwendet wird.
feature: Purchase Orders
role: Admin, Developer
exl-id: c4d415ee-b1ac-4094-9209-19b91f9a7666
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344: Bei Verwendung von *[!UICONTROL Purchase Order]* mit automatischer Validierung doppelte Bestellbestätigungs-E-Mails

Der Patch ACSD-60344 behebt das Problem, dass doppelte E-Mails zur Bestellbestätigung gesendet werden, wenn ein *[!UICONTROL Purchase Order]* mit automatischer Genehmigung verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-60344. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei Verwendung eines *[!UICONTROL Purchase Order]* mit automatischer Validierung werden doppelte E-Mails zur Bestellbestätigung gesendet.

<u>Voraussetzungen</u>

Aktivieren von B2B-Modulen und -*[!UICONTROL Purchase Order]*.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Unternehmenskonto und aktivieren Sie eine *[!UICONTROL Purchase Order]* dafür.
1. Erstellen Sie ein reguläres Benutzerkonto und fügen Sie es dem Unternehmenskonto als Firmenbenutzer hinzu.
1. Mit diesem Konto eine Bestellung aufgeben.
1. Cron ausführen und E-Mails überprüfen.

<u>Erwartete Ergebnisse</u>:

Pro Bestellung wird nur eine Bestätigungs-E-Mail empfangen.

<u>Tatsächliche Ergebnisse</u>:

Zwei Bestätigungs-E-Mails gehen ein.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
