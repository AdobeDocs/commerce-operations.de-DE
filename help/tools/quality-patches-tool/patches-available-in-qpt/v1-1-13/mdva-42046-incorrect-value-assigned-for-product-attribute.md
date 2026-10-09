---
title: 'MDVA-42046: Falscher Wert für Produktattribut zugewiesen'
description: Der Patch MDVA-42046 behebt das Problem, dass beim Aktualisieren eines Produkts mit einem Datumseingabefeld für das Produktattribut ein falscher Wert zugewiesen wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42046. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Attributes, Products
role: Admin
exl-id: ff5903ff-70b3-4274-a8a1-450c2fde9750
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%
---
# MDVA-42046: Falscher Wert für Produktattribut zugewiesen

Der Patch MDVA-42046 behebt das Problem, dass beim Aktualisieren eines Produkts mit einem Datumseingabefeld für das Produktattribut ein falscher Wert zugewiesen wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-42046. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.3.5-p2 und 2.4.0 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nach dem Speichern eines Produkts mit `news_from_date`- und/oder `news_to_date` Feldern werden die Werte in diesen Feldern auf den Standardwert zurückgesetzt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein einfaches Produkt.
1. Exportieren Sie das in Schritt 1 erstellte Produkt.
1. Fügen Sie in die exportierte CSV-Datei einige Werte in die Felder `news_from_date` und `news_to_date` ein. Beispiel: 15. Februar 2021 und 18. Juni 2021.
1. Importieren Sie das Produkt mit der geänderten CSV-Datei.
1. Fügen Sie zusätzliche Spalten „Produkt als neues Startdatum festlegen“ und „Produkt als neues Startdatum festlegen“ zum Produktraster hinzu.
1. Öffnen Sie die Bearbeitungsseite für das Produkt und klicken Sie ohne Änderungen auf **Speichern**.
1. Kehren Sie zum Produktraster zurück und überprüfen Sie die Daten für das Produkt.

<u>Erwartete Ergebnisse</u>:

„Produkt als neues Startdatum festlegen“ und „Produkt als neues Datum festlegen“ sind dieselben wie vor dem Speichern.

<u>Tatsächliche Ergebnisse</u>:

* Die Werte in den Spalten „Produkt als neues Startdatum festlegen“ und „Produkt als neues Datum festlegen“ werden geändert.

* Die Spalte „Produkt als neues Startdatum festlegen“ zeigt das aktuelle Datum an, und die Spalte „Produkt als neues Startdatum festlegen“ ist leer.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
