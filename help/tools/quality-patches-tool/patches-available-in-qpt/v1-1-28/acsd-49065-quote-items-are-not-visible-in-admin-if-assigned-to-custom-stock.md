---
title: "ACSD-49065: Anführungselemente sind in Admin nicht sichtbar."
description: Wenden Sie den Patch ACSD-49065 an, um das Adobe Commerce-Problem zu beheben, bei dem die Anführungselemente nicht im Admin sichtbar sind, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind.
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-49065: Anführungselemente sind in der Admin-Konsole nicht sichtbar

Der Patch ACSD-49065 behebt das Problem, dass die Anführungselemente nicht im Admin sichtbar sind, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID ist ACSD-49065. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Anführungselemente sind im Admin nicht sichtbar, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind.

Voraussetzungen:

Die Module **[!UICONTROL B2B]** und **[!UICONTROL Inventory]** müssen installiert sein.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie **[!UICONTROL Company]** und **[!UICONTROL B2B Quote]** unter **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Erstellen Sie eine sekundäre **[!UICONTROL Inventory Source]** und weisen Sie sie einer sekundären **[!UICONTROL Inventory Stock]** zu.
1. Erstellen Sie ein neues Produkt, indem Sie nur den sekundären (nicht standardmäßigen) **[!UICONTROL Inventory Source]** zuweisen.
1. Gehen Sie zur Storefront und erstellen Sie ein neues Unternehmenskonto. Melden Sie sich als **[!UICONTROL Company Admin]** an und fügen Sie das erstellte Produkt zum Warenkorb hinzu.
1. Navigieren Sie zum Warenkorb und *[!UICONTROL Request a Quote]*.
1. Gehen Sie zum Administrator und sehen Sie sich das angeforderte Angebot unter **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** an.

<u>Erwartete Ergebnisse</u>:

Elemente werden in dem neuen Angebot angezeigt, das mit neuen Produkten erstellt wurde, ohne die Produkte erneut zu speichern.

<u>Tatsächliche Ergebnisse</u>:

Der Abschnitt *[!UICONTROL Items Quoted]* ist leer. Wenn Sie das neu erstellte Produkt erneut speichern, werden die Elemente angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
