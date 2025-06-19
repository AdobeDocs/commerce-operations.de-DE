---
title: 'ACSD-48293: Composite-Produkte nicht vorrätig, wenn ausverkauft Kinderprodukte wieder vorrätig'
description: Wenden Sie den Patch ACSD-48293 an, um das Adobe Commerce-Problem zu beheben, dass die zusammengesetzten Produkte nicht mehr vorrätig sind, wenn die ausverkauften untergeordneten Produkte wieder auf Lager sind.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 2aa75e97-373e-4e4a-a545-69bce807ca4d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48293: Composite-Produkte nicht vorrätig, wenn ausverkauft Kinderprodukte wieder vorrätig

Mit dem Patch ACSD-48293 wird das Problem behoben, dass die zusammengesetzten Produkte nicht mehr vorrätig sind, wenn die ausverkauften untergeordneten Produkte wieder auf Lager sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48293. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Zusammengesetzte Produkte sind nicht mehr vorrätig, wenn die untergeordneten Produkte, die ausverkauft waren, wieder auf Lager sind.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine sekundäre Website-, Store- und Store-Ansicht.
1. Erstellen Sie zwei Quellen und Lager und weisen Sie sie jeder Website zu.
1. Aktivieren Sie die Option Nicht vorrätige Produkte anzeigen unter **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Erstellen Sie ein konfigurierbares Produkt mit einem zugehörigen Produkt unter Verwendung der Lagerquelle der primären Website (Menge = 1 festlegen).
1. Geben Sie eine Bestellung für das konfigurierbare Produkt auf.
1. Lauf die Cron.
1. Öffnen Sie das konfigurierbare Produkt in der Storefront und bestätigen Sie, dass es nicht vorrätig ist.
1. Öffnen Sie das konfigurierbare Produkt über die [!UICONTROL Admin] und legen Sie die **[!UICONTROL Manage Stock Option]** auf *[!UICONTROL No]* fest.
1. Lauf die Cron.
1. Versenden Sie die Bestellung und fügen Sie die Menge zu dem einfachen Produkt hinzu, das es auf Lager macht.
1. Lauf die Cron.
1. Überprüfen Sie die Produktverfügbarkeit in der Storefront.

<u>Erwartete Ergebnisse</u>:

Das konfigurierbare Produkt ist vorrätig.

<u>Tatsächliche Ergebnisse</u>:

Das konfigurierbare Produkt ist nicht vorrätig.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
