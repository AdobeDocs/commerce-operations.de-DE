---
title: 'ACSD-51238: Die Inventarquelle wird entfernt, wenn ein konfigurierbares Produkt aktualisiert und der Preis bearbeitet wird'
description: Wenden Sie den Patch ACSD-51238 an, um das Adobe Commerce-Problem zu beheben, bei dem die Inventarquelle entfernt wird, wenn ein konfigurierbares Produkt aktualisiert und der Preis bearbeitet wird.
feature: Configuration, Inventory, Orders, Products
role: Admin
exl-id: 785f012f-e064-4ac6-b559-9e9aa42c679c
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51238: Die Inventarquelle wird entfernt, wenn ein konfigurierbares Produkt aktualisiert und der Preis bearbeitet wird

Mit dem Patch ACSD-51238 wird das Problem behoben, dass die Inventarquelle entfernt wird, wenn ein konfigurierbares Produkt aktualisiert und der Preis bearbeitet wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.32 installiert ist. Die Patch-ID ist ACSD-51238. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Bestandsquelle wird beim Aktualisieren eines konfigurierbaren Produkts und Bearbeiten des Preises entfernt.

<u>Schritte zur Reproduktion</u>:

1. Installieren von **[!DNL Adobe Commerce]** mit **[!DNL Inventory module]**
1. Gehen Sie zu **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** und erstellen Sie *zwei Quellen* und *zwei Lager*.
1. Erstellen Sie eine **[!UICONTROL configurable product]** und weisen Sie sie **[!UICONTROL default sources]** oder **[!UICONTROL newly created sources]** zu.
1. Klicken Sie auf die **[!UICONTROL next button]** und *speichern* das Produkt.
1. Bearbeiten Sie nun denselben **[!UICONTROL Configurable Product]** und klicken Sie in der **[!UICONTROL Configuration tab]** auf **[!UICONTROL Edit Configuration]** .
1. Ändern Sie `Step 3: Bulk Images,Price and Quantity` die `price` und lassen Sie `Quantity` und `Images` auf `Skip quantity at this time` bzw. `Skip image uploading at this time`.
1. Klicken Sie auf **[!UICONTROL next button]** und generieren Sie das Produkt.

<u>Erwartete Ergebnisse</u>

Die Menge pro Quelle im **[!UICONTROL Configuration tab]** darf nicht leer sein.

<u>Tatsächliche Ergebnisse</u>

Die Menge pro Quelle im **[!UICONTROL Configuration tab]** ist leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>) im [!DNL Quality Patches Tool].
