---
title: 'B2B-2598: Fügt Caching-Funktion zu storeConfig, Währung, Land, Ländern, availableStores GraphQL-Abfragen hinzu'
description: Wenden Sie den B2B-2598-Patch an, um den GraphQL-Abfragen „storeConfig“, „currency“, „country“, „countries“ und „availableStores“ Zwischenspeicherungsfunktionen hinzuzufügen.
feature: B2B, GraphQL, Cache
role: Admin
type: Troubleshooting
autotag-review: '2026-05-22T20:21:20.687Z'
TQID: 'https://experienceleague.adobe.com/DQWkSrUHcUhOTn3fWdnRPVQUK6jRkPGCAnIKPRHkebQ'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: c32adafa-ed01-4b31-997e-2413013911b0
subfeature_v2: id: e396cff5-f586-484c-89f0-7f1da3308f92
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: d378ca77-2da1-4f39-ad92-1917fe974a38
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: c1579802-ddd4-4214-8a91-97b2066abe11
industry_v2: id: aad1e361-483a-40cf-9a88-144325515074
source-git-commit: 17c3f587a16209876a9713881eff0034d872581e
workflow-type: tm+mt
source-wordcount: 457
ht-degree: 0%

---

# B2B-2598: Fügt `storeConfig`-, `currency`-, `country`-, `countries`- und `availableStores`-GraphQL-Abfragen Cache-Funktionen hinzu

Der Patch B2B-2598 fügt `storeConfig`-, `currency`-, `country`-, `countries`- und `availableStores`-GraphQL-Abfragen Cache-Funktionen hinzu. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist B2B-2598. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7-beta1 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die `availableStores`-, `countries`-, `country`-, `currency`-, `storeConfig`- und `customAttributeMetadata`-Abfragen von GraphQL können nicht zwischengespeichert werden.

<u>Voraussetzungen</u>:

* Der Server verweist auf [!DNL Varnish] Proxyserver für das Adobe Commerce-Backend.
* Die Konfigurationseinstellung `system/full_page_cache/caching_application` ist auf *2* ([!DNL Varnish]) festgelegt. Alternativ können Sie zu Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > wechseln und sie auf [!DNL Varnish] setzen.

Nachdem der Patch angewendet wurde, führen Sie die folgenden Schritte aus, um sicherzustellen, dass die Caching-Funktion jetzt verfügbar ist:

1. Senden Sie `GET` Anfrage mithilfe beliebiger Felder an eine der oben aufgeführten GraphQL-Abfragen.
1. Senden Sie die Anfrage erneut, ohne Änderungen vorzunehmen. Sie werden feststellen, dass sie viel schneller ist. Beachten Sie, dass die Anfrage nicht an das Backend gesendet wird, sondern vollständig von [!DNL Varnish] als Cache-Treffer verarbeitet wird.
1. Wenn ein weiterer Korrekturabzug erforderlich ist, kommentieren Sie den in unserer [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227) vorhandenen Satz `X-Magento-Debug` Kopfzeile aus, starten Sie [!DNL Varnish] dann neu und führen Sie die oben genannten Schritte erneut aus.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool]
