---
title: 'ACSD-53583: Verbessern der partiellen Neuindizierungsleistung für [!UICONTROL Category Products]- und [!UICONTROL Product Categories]'
description: Wenden Sie den Patch ACSD-53585 an, um die partielle Neuindizierungsleistung für Kategorieprodukte und Produktkategorieindexer zu verbessern.
feature: Products, Categories
role: Admin, Developer
exl-id: 11e60cc2-1f7e-4e4a-a5eb-0f1dbe399ef2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
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
source-wordcount: '409'
ht-degree: 0%
---
# ACSD-53583: Verbessern der partiellen Neuindizierungsleistung für Indexer für Kategorie- und Produktkategorien

Der Patch ACSD-53583 verbessert die partielle Neuindizierungsleistung von *Kategorieprodukten* und *Produktkategorien* Indexern. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.39 installiert ist. Die Patch-ID ist ACSD-53583. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3
* Nicht kompatibel mit [!DNL Live Search] Modul. Um diesen Patch auf [!DNL Live Search] Installation anwenden zu können, fordern Sie bitte einen zusätzlichen ACSD-55719 Patch an.

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die teilweise Neuindizierung dauert länger als die vollständige Neuindizierung.

<u>Schritte zur Reproduktion</u>:

1. Drehen Sie alle Indexer auf *Nach Zeitplan aktualisieren*.
1. Generieren von Daten mit dem [!DNL Performance Toolkit] (mittleres Profil).
1. Nehmen Sie Änderungen an allen Produkten und Kategorien vor, sodass sie sich im Indexrückstand befinden und alle Indizes inaktiv sind.
1. Führen Sie eine partielle Neuindizierung für *Kategorieprodukte* und *Produktkategorien* Indexer durch.

<u>Erwartete Ergebnisse</u>:

Die teilweise Neuindizierung wird einmal pro Produkt aufgerufen und dauert fast genauso lange wie die vollständige Neuindizierung, da alle Produkte und Kategorien geändert wurden.

<u>Tatsächliche Ergebnisse</u>:

Eine teilweise Neuindizierung wird oft pro Produkt aufgerufen und dauert länger als eine vollständige Neuindizierung.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
