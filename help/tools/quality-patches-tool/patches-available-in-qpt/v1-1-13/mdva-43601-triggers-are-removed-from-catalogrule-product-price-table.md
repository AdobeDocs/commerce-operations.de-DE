---
title: 'MDVA-43601: Trigger werden nach vollständiger Neuindizierung aus der Tabelle „catalogrule_product_price“ entfernt'
description: Der Patch MDVA-43601 behebt das Problem, dass Trigger aus der Tabelle „catalogrule_product_price“ nach einer vollständigen Neuindizierung von „catalogrule_rule“ oder „catalogrule_product“ entfernt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43601. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Catalog Management, Orders, Products
role: Admin
exl-id: b9580806-ac35-4c86-8eee-c9f16d654171
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '427'
ht-degree: 0%
---
# MDVA-43601: Trigger werden nach vollständiger Neuindizierung aus der Tabelle „catalogrule_product_price“ entfernt

Der Patch MDVA-43601 behebt das Problem, dass Trigger nach einer vollständigen Neuindizierung von `catalogrule_rule` oder `catalogrule_product` aus `catalogrule_product_price` Tabelle entfernt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.13 installiert ist. Die Patch-ID lautet MDVA-43601. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Trigger werden nach einer vollständigen Neuindizierung von `catalogrule_rule` oder `catalogrule_product` aus `catalogrule_product_price` Tabelle entfernt.

<u>Schritte zur Reproduktion</u>:

1. Setzen Sie alle Indexer auf *Nach Zeitplan aktualisieren*.
1. Überprüfen Sie die für `catalogrule_product_price` Tabelle erstellten Trigger, indem Sie die folgende SQL-Anfrage ausführen:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Indizieren Sie `catalogrule_rule` oder `catalogrule_product` manuell neu, indem Sie den folgenden Befehl ausführen: `bin/magento indexer:reindex catalogrule_rule`
1. Überprüfen Sie die Trigger `catalogrule_product_price` Tabelle erneut.

<u>Erwartete Ergebnisse</u>:

Trigger in `catalogrule_product_price` Tabelle bleiben nach einer vollständigen Neuindizierung erhalten.

<u>Tatsächliche Ergebnisse</u>:

Für `catalogrule_product_price` Tabelle wurden keine Trigger gefunden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
