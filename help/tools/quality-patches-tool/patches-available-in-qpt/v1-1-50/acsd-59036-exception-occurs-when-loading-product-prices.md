---
title: 'ACSD-59036: Eine Ausnahme tritt auf, wenn die Produktpreise mit unteren und oberen Grenzen von $0 geladen werden'
description: Wenden Sie den Patch ACSD-59036 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Laden der Produktpreise eine Ausnahme auftritt, bei der die unteren und oberen Grenzen auf *$0* festgelegt sind.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
exl-id: a7d05108-0b03-4eb4-84ab-0dc5601530cb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
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
source-wordcount: '465'
ht-degree: 0%
---
# ACSD-59036: Eine Ausnahme tritt auf, wenn die Produktpreise mit unteren und oberen Grenzen von *$0 geladen werden*

Der Patch ACSD-59036 behebt das Problem, dass eine Ausnahme auftritt, wenn die Produktpreise mit unteren und oberen Grenzen von *$0* geladen werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-59036. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine Ausnahme tritt auf, wenn die Produktpreise mit unteren und oberen Grenzen von *$0* geladen werden.

Das Problem tritt auf, weil der Algorithmus beim Laden der Abfrage mit Preisbereichen keine NULL-Werte berücksichtigt. Um dies zu beheben, können wir überprüfen, ob sowohl der untere als auch der obere Bereich NULL sind, und wenn sie NULL sind, weisen Sie einen Wert von *0* für beide Limits zu. Dies sollte verhindern, dass Fehler ausgelöst werden.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie *13* einfache Produkte.
1. Weisen Sie alle *13*-Produkte einer Kategorie zu.
1. Setzen Sie den Preis für ein Produkt auf *$1322.94*.
1. Setzen Sie den Preis aller anderen Produkte auf *$0*.
1. Konfigurieren Sie [!DNL OpenSearch] als Suchmaschine.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** und setzen Sie die **[!UICONTROL PLP]** auf *16*.
1. Setzen Sie **[!UICONTROL Price Navigation Step Calculation]** auf *Automatisch (gleicht die Produktzahl an)*.
1. Vollständige Neuindizierung ausführen.
1. Öffnen Sie die *[!UICONTROL Category]*.

<u>Erwartete Ergebnisse</u>:

Auf der Seite *[!UICONTROL Category]* werden alle Produkte angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Ein Fehler tritt auf:

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
