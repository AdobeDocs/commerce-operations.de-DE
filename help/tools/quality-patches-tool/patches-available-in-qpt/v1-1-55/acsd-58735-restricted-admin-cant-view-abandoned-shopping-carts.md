---
title: 'ACSD-58735: Ein Admin mit Zugriffsbeschränkung kann keine Transaktionsabbrüche im Kundenkonto für die zugehörige Website anzeigen.'
description: Wenden Sie den Patch ACSD-58735 an, um das Adobe Commerce-Problem zu beheben, bei dem ein eingeschränkter Administrator die abgebrochenen Warenkörbe auf der Seite Kundenkonto in Commerce Admin für eine zugehörige Website nicht anzeigen kann.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
exl-id: b5dcc12f-325d-4de5-bae5-ff938ec77b13
source-git-commit: 8a33e0aadf3aab2b267f18b20a5195538b6990ef
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-58735: Ein Admin mit Zugriffsbeschränkung kann keine Transaktionsabbrüche im Kundenkonto für die zugehörige Website anzeigen.

Mit dem Patch ACSD-58735 wird das Problem behoben, dass ein Admin-Benutzer mit einer eingeschränkten Rolle den Warenkorb von abgebrochenen Kunden nicht über die Registerkarte Commerce-**[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]** anzeigen kann.

Das Problem tritt auf, da beim Anzeigen der Rasteransicht für mehrere Websites die verknüpfte Store-ID nicht angezeigt wird, wenn ein Transaktionsabbruch standardmäßig im Admin-Bedienfeld geladen wird.

Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58735. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Administratoren mit beschränkten Zugangsrechten können keine Transaktionsabbrüche auf der Seite „Kundenkonto“ im Admin-Bedienfeld anzeigen.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Administratorrolle, die nur Zugriff auf eine der Websites hat.
1. Erstellen Sie einen Transaktionsabbruch.
1. Melden Sie sich als Administrator mit vollem Berechtigungsumfang an. Überprüfen Sie **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** und sehen Sie, ob der Warenkorb angezeigt wird.
1. Aktivieren Sie **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** als Benutzer mit eingeschränkten Administratorrechten.

<u>Erwartete Ergebnisse</u>:

Der Administrator mit Zugriffsbeschränkung kann abgebrochene Warenkörbe für die zugehörige Website sehen.

<u>Tatsächliche Ergebnisse</u>:

Der Administrator mit Zugriffsbeschränkung sieht keine Transaktionsabbrüche für die zugehörige Website.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
