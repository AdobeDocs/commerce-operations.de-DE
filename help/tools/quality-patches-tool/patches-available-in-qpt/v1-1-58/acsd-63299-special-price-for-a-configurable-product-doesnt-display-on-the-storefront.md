---
title: 'ACSD-63299: Sonderpreis für ein konfigurierbares Produkt wird nicht auf der Storefront angezeigt'
description: Wenden Sie den Patch ACSD-63299 an, um das Adobe Commerce-Problem zu beheben, bei dem das Sonderpreisattribut die Anzeige von Sonderpreisen für konfigurierbare Produkte nicht mehr beeinflusst.
feature: Catalog Management
Role: Admin, Developer
exl-id: cd1775c5-783e-4ed5-a148-1dae0b7542f8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299: Sonderpreis für ein konfigurierbares Produkt wird nicht auf der Storefront angezeigt

Der Patch ACSD-63299 behebt das Problem, dass das Sonderpreisattribut die Anzeige von Sonderpreisen für konfigurierbare Produkte nicht mehr beeinflusst. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-63299. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL Adobe Commerce] wirkt sich die Änderung des *Wird in der Produktliste verwendet* für das Sonderpreisattribut nicht mehr darauf aus, wie Sonderpreise für konfigurierbare Produkte angezeigt werden.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]**.
1. Suchen Sie das ***[!UICONTROL special_price]*** Attribut und navigieren Sie zu **[!UICONTROL Storefront Properties]**.
1. Ändern Sie ***[!UICONTROL Used in Product Listing]*** in ***[!UICONTROL No]***.
1. Erstellen Sie ein konfigurierbares Produkt mit einem untergeordneten Element:
   * Name und SKU: Test
   * Preis: $159.00
   * Generieren Sie eine auf der Farbe basierende Option. Neue Farbe hinzufügen: Blau
   * Speichern
1. Öffnen Sie das untergeordnete Produkt und führen Sie die folgenden Schritte aus:
   * Setzen Sie einen Sonderpreis auf $99.90 in **[!UICONTROL Advanced Pricing]**
   * Ändern Sie [!UICONTROL Visibility] in **[!UICONTROL Catalog, Search]**.
1. Öffnen Sie die einfache Produktseite und bestätigen Sie, dass der Sonderpreis sichtbar ist.
1. Öffnen Sie die konfigurierbare Produktseite.
1. Wählen Sie das blaue Produkt aus.

<u>Erwartete Ergebnisse</u>:

Der Sonderpreis ist genauso sichtbar wie für das einfache Produkt.

<u>Tatsächliche Ergebnisse</u>:

1. Der vollständige Preis wird angezeigt, wenn ein konfigurierbares Produkt ausgewählt wird.
1. Es gibt eine Diskrepanz zwischen den Abschnitten *So niedrig wie…* ($99.90) und dem tatsächlichen Preis ($99.90 + $59.10 = $159.00).

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
