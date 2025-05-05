---
title: 'ACSD-56790: Die Option **[!UICONTROL move out of stock to bottom]** funktioniert nicht beim Sortieren von Produkten in der  [!DNL Visual Merchandiser]'
description: Wenden Sie den Patch ACSD-56790 an, um das Adobe Commerce-Problem zu beheben, bei dem die Option „Von Lager nach unten verschieben“ beim Sortieren von Produkten im Visual Merchandiser nicht funktioniert.
feature: Products, Categories
role: Admin, Developer
exl-id: a5e5f208-793d-45a5-a000-f8ff1c31d049
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-56790: **[!UICONTROL move out of stock to bottom]** Option funktioniert nicht beim Sortieren von Produkten in der [!DNL Visual Merchandiser]

Mit dem Patch ACSD-56790 wird das Problem behoben, dass die Option Von Lager nach unten nicht funktioniert, wenn Produkte im [!DNL Visual Merchandiser] sortiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 installiert ist. Die Patch-ID ist ACSD-56790. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Option **[!UICONTROL move out of stock to bottom]** funktioniert nicht beim Sortieren von Produkten in der [!DNL Visual Merchandiser]

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und erstellen Sie die folgenden Attribute.
1. Erstellen Sie eine neue Website: **Nicht-Haupt**.
1. Erstellen Sie auf **neuen Website einen „Nicht** Haupt-Store“.
1. Erstellen Sie zwei Stores:

   * Zuerst im **Main Website Store**.
   * Zweite im **Nicht-Haupt-Store**.

1. Erstellen Sie zwei Quellen:
   * Briefe
   * Zahlen.

1. Erstellen Sie zwei Lager:
   * First Main - Vertriebskanäle: Main Website - Zugewiesene Quellen: Briefe.
   * Zweite Nicht-Hauptquelle - Vertriebskanäle: Nicht-Hauptquelle - Zugewiesene Quellen: Zahlen.

1. Erstellen Sie drei einfache Produkte auf beiden Websites, alle in der Standardkategorie, die beiden Quellen zugewiesen sind:

   * ProduktA - Menge *10* in Buchstaben, Menge *0* in Zahlen.
   * Produkt1 - Menge *0* in Buchstaben, Menge *10* in Zahlen.
   * ProductA1 - *10* in Buchstaben, *10* in Zahlen.

1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** und wählen Sie **[!UICONTROL Default category]**.
1. Ändern Sie den Bereich in **Erste**.
1. Erweitern Sie die Produkte im Abschnitt Kategorie .
1. Wählen Sie die Sortierreihenfolge wie folgt: **[!UICONTROL move out of stock to bottom]**

<u>Erwartete Ergebnisse</u>:

Die Liste der Produkte mit den **nicht vorrätigen** Produkten wird nach unten verschoben.

<u>Tatsächliche Ergebnisse</u>:

Die Produkte können nicht geladen werden. Eine Seite wird mit folgender Fehlermeldung zum Admin-Dashboard weitergeleitet: `Invalid security or form key. Please refresh the page`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
