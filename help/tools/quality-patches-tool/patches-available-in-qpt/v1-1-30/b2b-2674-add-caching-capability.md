---
title: 'B2B-2674: Fügt der GraphQL-Abfrage customAttributeMetadata eine Caching-Funktion hinzu'
description: Wenden Sie den Patch B2B-2674 an, um der GraphQL-Abfrage customAttributeMetadata eine Zwischenspeicherungsfunktion hinzuzufügen.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
exl-id: b49633f3-b144-405f-a21d-726e222a7bfe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# B2B-2674: Fügt der `customAttributeMetadata` GraphQL-Abfrage eine Caching-Funktion hinzu

Der Patch B2B-2674 fügt den `customAttributeMetadata` GraphQL-Abfragen Caching-Funktionen hinzu. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist B2B-2674. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7-beta1 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
