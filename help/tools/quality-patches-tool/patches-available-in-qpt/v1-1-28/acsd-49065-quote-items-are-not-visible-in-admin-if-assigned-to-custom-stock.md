---
title: 'ACSD-49065: Angebotselemente sind in Admin nicht sichtbar'
description: Wenden Sie den ACSD-49065 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die Angebotselemente in der Admin nicht sichtbar sind, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind.
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-49065: Angebotselemente sind in Admin nicht sichtbar

Mit dem Patch ACSD-49065 wird das Problem behoben, dass die Angebotselemente im Administrator nicht sichtbar sind, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID ist ACSD-49065. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Angebotselemente sind im Admin nicht sichtbar, wenn sie nur dem benutzerdefinierten Lager zugewiesen sind.

Voraussetzungen:

**[!UICONTROL B2B]** und **[!UICONTROL Inventory]** Module müssen installiert werden.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie **[!UICONTROL Company]** und **[!UICONTROL B2B Quote]** unter **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Erstellen Sie eine sekundäre **[!UICONTROL Inventory Source]** und weisen Sie sie einem sekundären **[!UICONTROL Inventory Stock]** zu.
1. Erstellen Sie ein neues Produkt, indem Sie nur das sekundäre (nicht standardmäßige) **[!UICONTROL Inventory Source]** zuweisen.
1. Gehen Sie zum StoreFront und erstellen Sie ein neues Unternehmenskonto. Melden Sie sich als **[!UICONTROL Company Admin]** an und fügen Sie das erstellte Produkt zum Warenkorb hinzu.
1. Navigieren Sie zum Warenkorb und *[!UICONTROL Request a Quote]* Sie .
1. Rufen Sie den Administrator auf und zeigen Sie das gewünschte Angebot unter **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** an.

<u>Erwartete Ergebnisse</u>:

In dem neuen Angebot, das mit neuen Produkten erstellt wurde, sind die Elemente sichtbar, ohne dass die Produkte erneut gespeichert werden müssen.

<u>Tatsächliche Ergebnisse</u>:

Der *[!UICONTROL Items Quoted]* ist leer. Wenn Sie das neu erstellte Produkt erneut speichern, werden die Elemente angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
