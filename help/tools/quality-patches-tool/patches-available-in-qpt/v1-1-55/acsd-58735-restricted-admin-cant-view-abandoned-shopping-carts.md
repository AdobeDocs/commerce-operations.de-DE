---
title: "ACSD-58735: Eingeschränkte Administratoren können verlassene Warenkörbe nicht im Kundenkonto für zugehörige Websites anzeigen."
description: Wenden Sie den Patch ACSD-58735 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Administrator die abgebrochenen Warenkörbe auf der Kundenkontoseite in der Commerce-Admin-Konsole für eine verknüpfte Website nicht anzeigen kann.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
source-git-commit: 35bae8cff40235957f8fea418a43ccead13536da
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---



# ACSD-58735: Eingeschränkte Administratoren können keine aufgegebenen Warenkörbe auf dem Kundenkonto für zugehörige Websites anzeigen

Der Patch ACSD-58735 behebt das Problem, dass ein Admin-Benutzer mit eingeschränkter Rolle nicht in der Lage ist, den Warenkorb verlassener Kunden über die Registerkarte Commerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]** anzuzeigen.

Das Problem tritt auf, da beim Anzeigen der Rasteransicht für mehrere Websites die zugehörige Store-ID nicht angezeigt wird, wenn ein stehender Warenkorb standardmäßig im Admin-Bedienfeld geladen wird.

Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58735. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eingeschränkte Administratoren können im Admin-Bedienfeld nicht aufgegebene Warenkörbe auf der Kundenkontoseite anzeigen.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Administratorrolle mit Zugriff auf nur eine der Websites.
1. Erstellen Sie einen abgebrochenen Warenkorb.
1. Melden Sie sich als Administrator mit vollen Berechtigungen an. Überprüfen Sie **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** und sehen Sie, dass der Warenkorb angezeigt wird.
1. Markieren Sie **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** als eingeschränkten Admin-Benutzer.

<u>Erwartete Ergebnisse</u>:

Der eingeschränkte Administrator kann verlassene Warenkörbe für die zugehörige Website sehen.

<u>Tatsächliche Ergebnisse</u>:

Der eingeschränkte Administrator sieht keine aufgegebenen Warenkörbe für die zugehörige Website.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
