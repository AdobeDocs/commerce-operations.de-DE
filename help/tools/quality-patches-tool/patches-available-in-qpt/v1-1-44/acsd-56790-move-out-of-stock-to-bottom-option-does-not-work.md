---
title: 'Die Option "ACSD-56790: **[!UICONTROL move out of stock to bottom]*** funktioniert nicht beim Sortieren von Produkten in der  [!DNL Visual Merchandiser]"'
description: Wenden Sie den Patch ACSD-56790 an, um das Adobe Commerce-Problem zu beheben, bei dem die Option "Von Lager zu Ende wechseln"beim Sortieren von Produkten im Visual Merchandiser nicht funktioniert.
feature: Products, Categories
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-56790: Die Option **[!UICONTROL move out of stock to bottom]** funktioniert beim Sortieren von Produkten in [!DNL Visual Merchandiser] nicht

Der Patch ACSD-56790 behebt das Problem, dass die Option &quot;Von Lager zu Ende wechseln&quot;beim Sortieren von Produkten in der [!DNL Visual Merchandiser] nicht funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 installiert ist. Die Patch-ID ist ACSD-56790. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Option **[!UICONTROL move out of stock to bottom]** funktioniert nicht beim Sortieren von Produkten in der [!DNL Visual Merchandiser]

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Adobe Commerce.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und erstellen Sie die folgenden Attribute.
1. Erstellen Sie eine neue Website: **Non-main**.
1. Erstellen Sie einen **Nicht-Hauptspeicher** auf dieser neuen Website.
1. Erstellen Sie zwei Stores:

   * Zuerst im **Hauptwebsite-Store**.
   * Zweitens im **Nicht-Hauptspeicher**.

1. Erstellen Sie zwei Quellen:
   * Briefe
   * Zahlen.

1. Erstellen Sie zwei Lager:
   * First Main - Vertriebskanäle: Haupt-Website - zugewiesene Quellen: Briefe.
   * Zweite Nicht-Haupt- Absatzkanäle: Nicht-Haupt - zugewiesene Quellen: Zahlen.

1. Erstellen Sie auf beiden Websites drei einfache Produkte, alle in der Kategorie Standard , die beiden Quellen zugeordnet sind:

   * ProductA - Menge *10* in Briefen, Menge *0* in Zahlen.
   * Produkt1 - Menge *0* in Briefen, Menge *10* in Zahlen.
   * ProductA1 - Menge *10* in Briefen, Menge *10* in Zahlen.

1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** und wählen Sie **[!UICONTROL Default category]** aus.
1. Ändern Sie den Umfang in &quot;**Erste**&quot;.
1. Erweitern Sie die Produkte im Abschnitt Kategorie .
1. Wählen Sie die Sortierreihenfolge aus als: **[!UICONTROL move out of stock to bottom]**

<u>Erwartete Ergebnisse</u>:

Die Liste der Produkte mit den **nicht vorrätigen** Produkten wird nach unten verschoben.

<u>Tatsächliche Ergebnisse</u>:

Die Produkte werden nicht geladen. Eine Seite leitet Sie zum Admin-Dashboard mit der Fehlermeldung um: `Invalid security or form key. Please refresh the page`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
