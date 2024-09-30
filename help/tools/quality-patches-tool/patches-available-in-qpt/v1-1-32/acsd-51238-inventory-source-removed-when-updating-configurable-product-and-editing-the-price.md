---
title: "ACSD-51238: Inventarquelle wird beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt"
description: Wenden Sie den Patch ACSD-51238 an, um das Adobe Commerce-Problem zu beheben, bei dem die Inventarquelle beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt wird.
feature: Configuration, Inventory, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51238: Die Inventarquelle wird beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt

Der Patch ACSD-51238 behebt das Problem, dass die Inventarquelle beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-51238. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Inventarquelle wird beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie **[!DNL Adobe Commerce]** mit **[!DNL Inventory module]**
1. Gehen Sie zu &quot;**[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]**&quot;und erstellen Sie *zwei Quellen* und *zwei Lager*.
1. Erstellen Sie eine **[!UICONTROL configurable product]** und weisen Sie sie **[!UICONTROL default sources]** oder **[!UICONTROL newly created sources]** zu.
1. Klicken Sie auf die Werte **[!UICONTROL next button]** und *save* für das Produkt.
1. Bearbeiten Sie nun denselben **[!UICONTROL Configurable Product]** und klicken Sie auf **[!UICONTROL Edit Configuration]** innerhalb des **[!UICONTROL Configuration tab]**.
1. Ändern Sie in `Step 3: Bulk Images,Price and Quantity` die `price` und lassen Sie `Quantity` und `Images` auf `Skip quantity at this time` bzw. `Skip image uploading at this time`.
1. Klicken Sie auf **[!UICONTROL next button]** und generieren Sie das Produkt.

<u>Erwartete Ergebnisse</u>

Die Menge pro Quelle innerhalb der **[!UICONTROL Configuration tab]** sollte nicht leer sein.

<u>Tatsächliche Ergebnisse</u>

Die Menge pro Quelle innerhalb der **[!UICONTROL Configuration tab]** ist leer.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](</help/tools/quality-patches-tool/usage.md>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
