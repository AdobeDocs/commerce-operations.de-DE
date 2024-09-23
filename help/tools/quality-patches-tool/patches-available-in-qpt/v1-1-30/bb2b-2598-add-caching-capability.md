---
title: 'BB2B-2598: Fügt Caching-Funktion zu storeConfig, Währung, Land, Ländern, verfügbaren Stores GraphQl-Abfragen hinzu.'
description: Wenden Sie den Patch BB2B-2598 an, um die GraphQl-Abfragen von storeConfig, Währung, Land, Ländern und availableStores um eine Caching-Funktion hinzuzufügen.
feature: B2B, GraphQL, Cache
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# BB2B-2598: Fügt die Caching-Funktion zu den GraphQl-Abfragen `storeConfig`, `currency`, `country`, `countries` und `availableStores` hinzu.

Der Patch BB2B-2598 fügt die Caching-Funktion zu den GraphQl-Abfragen `storeConfig`, `currency`, `country`, `countries` und `availableStores` hinzu. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID lautet BB2B-2598. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7-Beta1 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die GraphQL-Abfragen `availableStores`, `countries`, `country`, `currency`, `storeConfig` und `customAttributeMetadata` können nicht zwischengespeichert werden.

<u>Voraussetzungen</u>:

* Der Server verweist auf [!DNL Varnish] proxying to Adobe Commerce Backend.
* Die Konfigurationseinstellung `system/full_page_cache/caching_application` ist auf *2} ([!DNL Varnish]) festgelegt oder navigieren Sie zu Adobe Commerce Admin >**[!UICONTROL Stores]**>**[!UICONTROL System]**>**[!UICONTROL Full Page Cache]**>**[!UICONTROL Caching Application]**und legen Sie sie auf [!DNL Varnish] fest.*

Nachdem der Patch angewendet wurde, führen Sie die folgenden Schritte aus, um sicherzustellen, dass die Zwischenspeicherungsfunktion jetzt verfügbar ist:

1. Senden Sie eine `GET` -Anfrage an eine der oben aufgeführten GraphQL-Abfragen, wobei Sie beliebige Felder verwenden.
1. Senden Sie die Anfrage ohne Änderungen erneut. Sie werden feststellen, dass sie viel schneller ist. Beachten Sie, dass die Anfrage nicht an das Backend gesendet wird, aber vollständig von [!DNL Varnish] als Cache-Treffer verarbeitet wird.
1. Wenn ein weiterer Testversand erforderlich ist, kommentieren Sie die in unserem [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227) vorhandene Nicht-Header `X-Magento-Debug` aus, starten Sie [!DNL Varnish] neu und führen Sie die oben genannten Schritte erneut aus.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
