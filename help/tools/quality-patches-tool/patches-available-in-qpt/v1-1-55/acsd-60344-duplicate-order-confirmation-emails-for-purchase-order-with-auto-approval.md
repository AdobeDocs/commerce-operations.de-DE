---
title: 'ACSD-60344: E-Mails zur Bestellbestätigung bei Verwendung von [!UICONTROL Purchase Order] mit automatischer Genehmigung duplizieren'
description: Wenden Sie den Patch ACSD-60344 an, um das Adobe Commerce-Problem zu beheben, bei dem doppelte Bestellbestätigungs-E-Mails gesendet werden, wenn eine [!UICONTROL Purchase Order] mit automatischer Genehmigung verwendet wird.
feature: Purchase Orders
role: Admin, Developer
source-git-commit: afa03b31e4af0be1ebc0d12aabd4f9d8be17d1fe
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344: E-Mails zur Bestellbestätigung bei Verwendung von *[!UICONTROL Purchase Order]* mit automatischer Genehmigung duplizieren

Der Patch ACSD-60344 behebt das Problem, dass E-Mails mit doppelter Bestellbestätigung gesendet werden, wenn eine *[!UICONTROL Purchase Order]* mit automatischer Genehmigung verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-60344. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Bei Verwendung von &quot;*[!UICONTROL Purchase Order]*&quot; mit automatischer Validierung werden E-Mails zur Bestätigung von doppelten Bestellungen gesendet.

<u>Voraussetzungen</u>

Aktivieren Sie B2B-Module und *[!UICONTROL Purchase Order]*.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Unternehmenskonto und aktivieren Sie dafür den Wert &quot;*[!UICONTROL Purchase Order]*&quot;.
1. Erstellen Sie ein reguläres Benutzerkonto und fügen Sie es dem Unternehmenskonto als Unternehmensbenutzer hinzu.
1. Platzieren Sie mithilfe dieses Kontos eine Bestellung.
1. Führen Sie Cron aus und überprüfen Sie E-Mails.

<u>Erwartete Ergebnisse</u>:

Pro Bestellung wird nur eine Bestätigungs-E-Mail empfangen.

<u>Tatsächliche Ergebnisse</u>:

Zwei Bestellbestätigungs-E-Mails werden empfangen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
