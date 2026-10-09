---
title: 'ACSD-56246: Planen von Produktaktualisierungen Löschen von Mehrfachauswahl-Attributwerten'
description: Wenden Sie den Patch ACSD-56246 an, um das Adobe Commerce-Problem zu beheben, bei dem die Planung von Produktaktualisierungen Mehrfachauswahl-Attributwerte löscht.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: 1751a03d-2610-423f-be2f-b9d060452904
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
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
source-wordcount: '432'
ht-degree: 5%
---
# ACSD-56246: Durch die Planung von Produktaktualisierungen werden Mehrfachauswahl-Attributwerte gelöscht

Der Patch ACSD-56246 behebt das Problem, dass bei der Planung von Produktaktualisierungen Mehrfachauswahl-Attributwerte gelöscht werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.44 installiert ist. Die Patch-ID ist ACSD-56246. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die geplanten Produktaktualisierungen löschen die Mehrfachauswahl-Attributwerte.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und erstellen Sie das folgende Attribut:

   * Standardbezeichnung: Programm
   * Katalogeingabetyp für Store-Inhaber: Mehrfachauswahl
   * Optionen verwalten (Werte Ihres Attributs): choice, sunscape, safetyShield
   * Attributcode: customer_program
   * Bereich: Global
   * Zu Spaltenoptionen hinzufügen: Nein
   * Verwendung in Filteroptionen: Nein
   * Storefront-Eigenschaften
   * Position: *333*
   * HTML-Tags in Storefront zulassen: Nein

1. Ausführen
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Ausführen
   `bin/magento setup:upgrade`.
1. Gehen Sie zu **[!UICONTROL Admin]** > Ein beliebiges einfaches Produkt wählen > Alle Elemente im Programmattribut auswählen > Klicken Sie auf **[!UICONTROL Save the product]**.
1. Planen Sie in der nächsten Minute ein Update für dieses Produkt und führen Sie den folgenden Befehl aus, um das Inhalts-Staging zu aktivieren:
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>Erwartete Ergebnisse</u>:

Das **[!UICONTROL program]** des Produkts sollte sich nicht ändern.

<u>Tatsächliche Ergebnisse</u>:

Das **[!UICONTROL program]** des Produkts wird gelöscht.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
