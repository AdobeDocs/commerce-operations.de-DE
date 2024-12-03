---
title: 'ACSD 49843: Produkt-Download-Link nach der automatischen Rechnungsstellung mit [!UICONTROL Payment Action] = [!UICONTROL Intent Sale] nicht verfügbar'
description: Wenden Sie den Patch ACSD-49843 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produkt-Download-Link nicht verfügbar ist, nachdem der bestellte Artikel automatisch von einer Online-Zahlungsmethode in Rechnung gestellt wird, wenn [!UICONTROL Payment Action] auf [!UICONTROL Intent Sale] gesetzt ist.
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-49843: Produkt-Download-Link nach der automatischen Rechnungsstellung mit [!UICONTROL Payment Action] = [!UICONTROL Intent Sale] nicht verfügbar

Der Patch ACSD-49843 behebt das Problem, bei dem der Produkt-Download-Link nicht verfügbar ist, nachdem der bestellte Artikel automatisch von einer Online-Zahlungsmethode in Rechnung gestellt wurde, wenn [!UICONTROL Payment Action] auf [!UICONTROL Intent Sale] gesetzt ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID lautet ACSD-49843. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Produkt-Download-Link ist nicht verfügbar, nachdem der bestellte Artikel von einer Online-Zahlungsmethode automatisch in Rechnung gestellt wurde, wenn [!UICONTROL Payment Action] auf [!UICONTROL Intent Sale] gesetzt ist.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Adobe Commerce-Administrator an und navigieren Sie zu &quot;**[!UICONTROL Stores]**&quot;> &quot;**[!UICONTROL Configuration]**&quot;> &quot;**[!UICONTROL Sales]**&quot;> &quot;**[!UICONTROL Configure Braintree]**&quot;.

   * Wählen Sie in der Dropdown-Liste [!UICONTROL Payment Action] die Option **[!UICONTROL Intent Sale]** aus und setzen Sie *[!UICONTROL Enable Card Payments]* auf *Ja*.

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** und stellen Sie sicher, dass der Wert auf *&quot;Invoiced&quot;* gesetzt ist.
1. Melden Sie sich in der Storefront als Kunde an.

   * Fügen Sie alle herunterladbaren Produkte und ein einfaches Produkt zum Warenkorb hinzu.
   * Verwenden Sie [!DNL Braintree Pay] , um die Bestellung mithilfe der Kartenoption zu platzieren.

1. Wechseln Sie zu **[!UICONTROL My Orders]** und sehen Sie, dass die Rechnung automatisch für die Bestellung erstellt wird und dass beide Artikelstatus *&quot;Rechnungsstellung&quot;* sind.
1. Gehen Sie zu &quot;**[!UICONTROL My Downloadable Products]**&quot;und stellen Sie fest, dass der Download-Link noch nicht verfügbar ist.
1. Gehen Sie im Admin zu dieser Bestellung und erstellen Sie eine Sendung dafür.
1. Wechseln Sie in der Storefront zu **[!UICONTROL My Downloadable Products]** und stellen Sie sicher, dass der Download-Link jetzt verfügbar ist.

<u>Erwartete Ergebnisse</u>:

Der Downloadlink ist verfügbar, wenn der herunterladbare Produktstatus *&quot;Rechnungsstellung&quot;* lautet.

<u>Tatsächliche Ergebnisse</u>:

Der Downloadlink ist auch dann nicht verfügbar, wenn der herunterladbare Produktstatus *&quot;Rechnungsstellung&quot;* lautet. Sie ist erst verfügbar, nachdem eine Sendung für das physische Produkt erstellt wurde.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
