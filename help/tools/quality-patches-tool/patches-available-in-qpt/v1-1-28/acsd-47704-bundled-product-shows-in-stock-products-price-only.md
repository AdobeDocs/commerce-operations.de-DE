---
title: 'ACSD-47704: Gebündeltes Produkt zeigt nur den Preis der vorrätigen Produkte'
description: Wenden Sie den ACSD-47704 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem ein gebündeltes Produkt nur den Preis der vorrätigen Produkte anzeigt.
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
exl-id: 7f05ceed-869c-4d1a-91fd-0122dc98e65e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# ACSD-47704: Gebündeltes Produkt zeigt nur den Preis der vorrätigen Produkte

Mit dem Patch ACSD-47704 wird das Problem behoben, dass Kundensegmentpreise zwischen Kundengruppen falsch zwischengespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID ist ACSD-47704. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Preis eines gebündelten Produkts mit aktivierter dynamischer Preisfindung ist falsch, da nur Artikel auf Lager enthalten sind.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zum Commerce Admin-Bedienfeld.
1. Navigieren Sie zu **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. Setzen Sie **[UICONROL Dynamic Price]** auf **[!UICONTROL Yes]**.
1. Bundle-Elemente:
   * **[!UICONTROL Ship bundle items]** auf **[!UICONTROL Together]** festlegen
   * **[!UICONTROL Add Option]** auswählen
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Erforderliches Kontrollkästchen markieren
      * Fügen Sie ein einfaches Produkt hinzu, das auf Lager ist; zum Beispiel Joust Duffle Bag SKU 24-MB01. Bevor Sie das Produkt hinzufügen, notieren Sie seinen Preis - 34 $
   * Standardmenge: 1
   * **[!UICONTROL Add Option]** auswählen
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Erforderliches Kontrollkästchen markieren
      * Fügen Sie ein einfaches Produkt hinzu, das nicht auf Lager ist, sondern sich von dem im vorherigen Schritt hinzugefügten Produkt unterscheidet; zum Beispiel - Strive Shoulder Pack 24-MB04. Bevor Sie das Produkt hinzufügen, notieren Sie seinen Preis - $32
      * Standardmenge: 1
1. Produkt speichern.
1. Gehen Sie zur Storefront und suchen Sie das in den vorherigen Schritten erstellte Produkt. Notieren Sie sich den Preis - $66
(66 = 32 + 34).
Derzeit entspricht der Preis des Bundle-Produkts der Summe der Preise seiner Optionen.
1. Navigieren Sie zum Commerce Admin-Bedienfeld. Navigieren Sie zu **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. Suchen Sie eines der einfachen Produkte, die dem Bundle-Produkt zuvor als Option zugewiesen wurden:
SKU 24-MB01 und einem Preis von 34 $.
1. Ändern Sie die Menge in 0.
1. Speichern Sie das Produkt.
1. Gehen Sie zur Storefront und suchen Sie das in den vorherigen Schritten erstellte Produktpaket. Notieren Sie sich den Preis - $32. Zuvor lag der Preis bei $66, was der Summe von $34 aus SKU 24-MB01 und $32 aus SKU 24-MB04 entsprach. Da das Produkt 24-MB01 nicht mehr vorrätig ist, wird der Paketpreis mit 32 USD angegeben. Es ist der Preis des anderen Produkts, bei dem es sich um eine Lageroption handelt.

<u>Erwartete Ergebnisse</u>:

Der Preis von Bundle-Produkten mit aktivierter dynamischer Preisfindung wird konsistent berechnet, unabhängig davon, ob Optionen vorrätig oder nicht vorrätig sind.

<u>Tatsächliche Ergebnisse</u>:

Der Preis des Produktpakets mit aktivierter dynamischer Preisfindung ist falsch berechnet. Es werden nur Optionen berücksichtigt, die auf Lager sind, was dazu führt, dass ein niedrigerer Betrag angezeigt wird als der tatsächliche Betrag, wenn eine der Optionen nicht vorrätig ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
