---
title: 'MDVA-37364: Benutzerdefiniertes Kundenattribut des Datentyps unterbricht die Rasterbenutzeroberfläche'
description: Der Patch MDVA-37364 löst das Problem, dass das benutzerdefinierte Kundenattribut vom Datentyp die Benutzeroberfläche des Kundenrasters beschädigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-37364. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce Version 2.4.4 behoben wird.
feature: Attributes, Cache
role: Developer
exl-id: 5bd64004-06c4-49fd-8e56-e2c44008ca82
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%
---
# MDVA-37364: Benutzerdefiniertes Kundenattribut des Datentyps unterbricht die Rasterbenutzeroberfläche

Der Patch MDVA-37364 löst das Problem, dass das benutzerdefinierte Kundenattribut vom Datentyp die Benutzeroberfläche des Kundenrasters beschädigt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-37364. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce Version 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0-2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim benutzerdefinierten Kundenattribut des Datentyps ist die Benutzeroberfläche des Kundenrasters nicht mehr verfügbar.

<u>Schritte zur Reproduktion</u>:

1. Benutzerdefiniertes Attribut mit Datentyp erstellen:
   * Navigieren Sie **Stores** > **Attribute** > **Attribut hinzufügen**.
   * Legen Sie den Eingabetyp auf „Datum“ fest.
   * Legen Sie die Option Zu Spaltenoptionen hinzufügen auf Ja fest.
   * Speichern Sie das Attribut.
1. Navigieren Sie **Admin** > **Kunden** > **Alle Kunden**.
   * Fügen Sie das neu hinzugefügte benutzerdefinierte Attribut dem Raster aus der Option Spalten hinzu.
1. Erstellen/Bearbeiten eines Kunden und Festlegen des Werts des erstellten benutzerdefinierten Datumsattributfelds.
1. Speichern, neu indizieren und den Cache löschen.
1. Navigieren Sie **Kunden** > **Alle Kunden**.
   * Überprüfen Sie das Kundenraster.

<u>Erwartete Ergebnisse</u>:

Das Admin-Kundenraster zeigt alle Daten an, einschließlich des neuen benutzerdefinierten Datumsattributs, ohne dass die Benutzeroberfläche des Kundenrasters beschädigt wird.

<u>Tatsächliche Ergebnisse</u>:

Die Admin-Benutzeroberfläche für Kundenraster ist fehlerhaft.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mit dem Quality Patches Tool, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
