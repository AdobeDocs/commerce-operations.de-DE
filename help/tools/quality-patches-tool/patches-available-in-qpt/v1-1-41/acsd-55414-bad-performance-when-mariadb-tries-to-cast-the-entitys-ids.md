---
title: 'ACSD-55414: Fehlerhafte Leistung, wenn MariaDB versucht, die entityYS_ids umzuwandeln'
description: Wenden Sie den Patch „ACSD-55414“ an, um das Adobe Commerce-Problem zu beheben, wenn MariaDB versucht, „entityYS_ids“ von einer Zeichenfolge in eine Ganzzahl zu konvertieren, was die Leistung der Neuindizierung beeinträchtigt.
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
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
source-wordcount: '362'
ht-degree: 0%
---
# ACSD-55414: Schlechte Leistung, wenn MariaDB versucht, die `entitys_ids` zu gießen

Der Patch ACSD-55414 behebt das Problem, dass die Neuindizierung beeinträchtigt wird, wenn MariaDB versucht, `entitys_ids` von Zeichenfolge in Ganzzahl zu konvertieren. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.41 installiert ist. Die Patch-ID ist ACSD-55414. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Leistung der Neuindizierung wird beeinträchtigt, wenn MariaDB versucht, die `entitys_ids` von Zeichenfolge zu Ganzzahl umzuwandeln.

<u>Schritte zur Reproduktion</u>:

1. Aktualisieren Sie `setup/performance-toolkit/profiles/ce/small.xml`, indem Sie *50000* einfache Produkte einrichten.
1. Generieren Sie dieses Profil, indem Sie den Befehl `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml` ausführen.
1. Neuindizierung ausführen: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Erwartete Ergebnisse</u>:

Die Neuindizierung benötigt eine angemessene Zeit bis zum Abschluss.

<u>Tatsächliche Ergebnisse</u>:

Die Neuindizierung dauert zu lange.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
