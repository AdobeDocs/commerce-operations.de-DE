---
title: 'ACSD-57854: Die Antwort *GraphQL* enthält deaktivierte Kategorien, die nicht in den Kategorieaggregationen aufgeführt werden sollten'
description: Wenden Sie den Patch ACSD-57854 an, um das Adobe Commerce-Problem zu beheben, bei dem die *GraphQL*-Antwort deaktivierte Kategorien enthält, die nicht in den Kategorieaggregationen aufgeführt werden sollten.
feature: GraphQL
role: Admin, Developer
exl-id: 216aad2a-f470-49f9-b8ca-79107ca07891
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
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
source-wordcount: '401'
ht-degree: 0%
---
# ACSD-57854: Die *GraphQL*-Antwort enthält deaktivierte Kategorien, die nicht in den Kategorieaggregationen aufgeführt werden sollten

Der Patch „ACSD-57854“ behebt das Problem, dass die *GraphQL*-Antwort deaktivierte Kategorien enthält, die nicht in den Kategorieaggregationen aufgeführt werden sollten. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID ist ACSD-57854. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die *GraphQL*-Antwort enthält deaktivierte Kategorien, die nicht in den Kategorieaggregationen aufgeführt werden sollten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Kategorien.
1. Erstellen Sie ein Produkt (Adobe-Produkt testen) und weisen Sie das Produkt beiden Kategorien zu.
1. Deaktivieren Sie eine der erstellten Kategorien.
1. Verwenden Sie Produkte *GraphQL*, um das Produkt zu durchsuchen.
1. Überprüfen Sie die Liste der Produktkategorien in der Antwort *GraphQL*.

<u>Erwartete Ergebnisse</u>:

Die deaktivierten Kategorien werden in der Antwort *GraphQL* nicht aufgeführt.

<u>Tatsächliche Ergebnisse</u>:

Die deaktivierten Kategorien werden in der Antwort der Kategorieaggregation *GraphQL* aufgeführt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
