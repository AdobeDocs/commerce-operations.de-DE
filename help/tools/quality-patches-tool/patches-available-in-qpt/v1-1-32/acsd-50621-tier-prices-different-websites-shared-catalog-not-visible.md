---
title: "ACSD-50621: Die Stufenpreise für verschiedene Websites im freigegebenen Katalog sind nicht sichtbar."
description: Wenden Sie den Patch ACSD-50621 an, um das Adobe Commerce-Problem zu beheben, bei dem die Stufenpreise für verschiedene Websites im freigegebenen Katalog nicht sichtbar sind, wenn sie in einer Umgebung mit mehreren Websites bearbeitet werden.
feature: Catalog Management, Orders
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-50621: Stufentarife für verschiedene Websites im freigegebenen Katalog sind nicht sichtbar

Der Patch ACSD-50621 behebt das Problem, dass die Stufenpreise für verschiedene Websites im freigegebenen Katalog nicht sichtbar sind, wenn sie in einer Umgebung mit mehreren Websites bearbeitet werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-50621. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Statuspreise für verschiedene Websites im freigegebenen Katalog sind nicht sichtbar, wenn sie in einer Umgebung mit mehreren Websites bearbeitet werden.

<u>Zu reproduzierende Schritte</u>:

1. Setzen Sie die **[!UICONTROL Catalog Price Scope]** auf **[!UICONTROL Website]**.
1. Erstellen Sie eine zusätzliche Website, einen Store und eine Storeübersicht.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es allen Websites zu.
1. Erstellen Sie einen benutzerdefinierten freigegebenen Katalog.
1. Wechseln Sie für den von Ihnen erstellten benutzerdefinierten freigegebenen Katalog zu &quot;**[!UICONTROL Set Pricing and Structure]**&quot;.
1. In Schritt 1: Produkte für den Katalog auswählen. Fügen Sie das von Ihnen erstellte einfache Produkt hinzu.
1. In Schritt 2: Legen Sie benutzerdefinierte Preise fest und klicken Sie auf **[!UICONTROL Configure]**.
1. Legen Sie für verschiedene Websites unterschiedliche Preise fest.
1. Wählen Sie &quot;**[!UICONTROL Done]**&quot;, klicken Sie auf &quot;**[!UICONTROL Generate Catalog]**&quot; und klicken Sie dann auf &quot;**[!UICONTROL Save]**&quot;.
1. Führen Sie cron aus.
1. Navigieren Sie zu **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** und überprüfen Sie den Tierpreis.

<u>Erwartete Ergebnisse</u>:

Alle zuvor konfigurierten Tier-Preise für verschiedene Websites sind vorhanden.

<u>Tatsächliche Ergebnisse</u>:

Zuvor konfigurierte Statuspreise sind nicht vorhanden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
