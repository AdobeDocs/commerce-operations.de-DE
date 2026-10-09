---
title: 'ACSD 49843: Link zum Produktdownload ist nach der automatischen Fakturierung mit [!UICONTROL Payment Action] = [!UICONTROL Intent Sale] nicht verfügbar'
description: Wenden Sie den Patch ACSD-49843 an, um das Adobe Commerce-Problem zu beheben, bei dem der Link zum Herunterladen von Produkten nicht verfügbar ist, nachdem der bestellte Artikel von einer Online-Zahlungsmethode automatisch fakturiert wurde, wenn [!UICONTROL Payment Action] auf [!UICONTROL Intent Sale] gesetzt ist.
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%
---
# ACSD-49843: Link zum Produktdownload ist nach der automatischen Fakturierung mit [!UICONTROL Payment Action] = [!UICONTROL Intent Sale] nicht verfügbar

Mit dem Patch ACSD-49843 wird das Problem behoben, dass der Link zum Herunterladen des Produkts nicht verfügbar ist, nachdem der bestellte Artikel von einer Online-Zahlungsmethode automatisch fakturiert wurde, wenn [!UICONTROL Payment Action] auf [!UICONTROL Intent Sale] gesetzt ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-49843. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Link zum Produktdownload ist nicht verfügbar, nachdem der bestellte Artikel automatisch von einer Online-Zahlungsmethode fakturiert wurde, wenn [!UICONTROL Payment Action] auf [!UICONTROL Intent Sale] gesetzt ist.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei Adobe Commerce Admin an und navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * Wählen Sie in der Dropdown-Liste [!UICONTROL Payment Action] die Option **[!UICONTROL Intent Sale]** aus und legen Sie *[!UICONTROL Enable Card Payments]* auf *Ja* fest.

1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** und stellen Sie sicher, dass *Option „Fakturiert“*.
1. Melden Sie sich in der Storefront als Kunde an.

   * Fügen Sie ein herunterladbares Produkt und ein einfaches Produkt zum Warenkorb hinzu.
   * Verwenden Sie [!DNL Braintree Pay] , um die Bestellung mithilfe der Kartenoption aufzugeben.

1. Navigieren Sie zu **[!UICONTROL My Orders]** und stellen Sie sicher, dass die Rechnung automatisch für den Auftrag erstellt wird und dass beide Artikelstatus &quot;*&quot;*.
1. Navigieren Sie zu **[!UICONTROL My Downloadable Products]** und stellen Sie fest, dass der Download-Link noch nicht verfügbar ist.
1. Wechseln Sie in der Admin zu dieser Bestellung und erstellen Sie eine Sendung dafür.
1. Navigieren Sie in der Storefront zu **[!UICONTROL My Downloadable Products]** und beachten Sie, dass der Download-Link jetzt verfügbar ist.

<u>Erwartete Ergebnisse</u>:

Der Download-Link ist verfügbar, wenn der herunterladbare Produktstatus „In Rechnung gestellt“ **.

<u>Tatsächliche Ergebnisse</u>:

Der Download-Link ist auch dann nicht verfügbar, wenn im Status des herunterladbaren Produkts &quot;*&quot; steht*. Sie ist erst verfügbar, nachdem eine Lieferung für das physische Produkt erstellt wurde.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
