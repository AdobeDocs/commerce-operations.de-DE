---
title: 'ACSD 49843: Link zum Produktdownload ist nach der automatischen Fakturierung mit [!UICONTROL Payment Action] = [!UICONTROL Intent Sale] nicht verfügbar'
description: Wenden Sie den Patch ACSD-49843 an, um das Adobe Commerce-Problem zu beheben, bei dem der Link zum Herunterladen von Produkten nicht verfügbar ist, nachdem der bestellte Artikel von einer Online-Zahlungsmethode automatisch fakturiert wurde, wenn [!UICONTROL Payment Action] auf [!UICONTROL Intent Sale] gesetzt ist.
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
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
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
