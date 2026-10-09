---
title: 'B2B-2674: Fügt der GraphQL-Abfrage customAttributeMetadata eine Caching-Funktion hinzu'
description: Wenden Sie den Patch B2B-2674 an, um der GraphQL-Abfrage customAttributeMetadata eine Zwischenspeicherungsfunktion hinzuzufügen.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: b49633f3-b144-405f-a21d-726e222a7bfe
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%
---
# B2B-2674: Fügt der `customAttributeMetadata` GraphQL-Abfrage eine Caching-Funktion hinzu

Der Patch B2B-2674 fügt den `customAttributeMetadata` GraphQL-Abfragen Caching-Funktionen hinzu. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID ist B2B-2674. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7-beta1 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

`customAttributeMetadata` GraphQL-Abfrage kann nicht zwischengespeichert werden.

<u>Voraussetzungen</u>:

* Der Server verweist auf [!DNL Varnish] Proxyserver für das Adobe Commerce-Backend.
* Die Konfigurationseinstellung `system/full_page_cache/caching_application` ist auf *2* ([!DNL Varnish]) festgelegt. Alternativ können Sie zu Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > wechseln und sie auf [!DNL Varnish] setzen.

Nachdem der Patch angewendet wurde, führen Sie die folgenden Schritte aus, um sicherzustellen, dass die Caching-Funktion jetzt verfügbar ist:

1. Senden Sie `GET` Anfrage mithilfe beliebiger Felder an die oben aufgeführte GraphQL-Abfrage.
1. Senden Sie die Anfrage erneut, ohne Änderungen vorzunehmen. Sie werden feststellen, dass sie viel schneller ist. Beachten Sie, dass die Anfrage nicht an das Backend gesendet wird, sondern vollständig von [!DNL Varnish] als Cache-Treffer verarbeitet wird.
1. Wenn ein weiterer Korrekturabzug erforderlich ist, kommentieren Sie den in unserer [VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239) vorhandenen Satz `X-Magento-Debug` Kopfzeile aus, starten Sie [!DNL Varnish] dann neu und führen Sie die oben genannten Schritte erneut aus.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
