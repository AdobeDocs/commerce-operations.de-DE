---
title: "B2B-2674: Fügt der GraphQL-Abfrage customAttributeMetadata eine Caching-Funktion hinzu."
description: Wenden Sie den Patch B2B-2674 an, um der GraphQL-Abfrage customAttributeMetadata eine Caching-Funktion hinzuzufügen.
feature: Attributes, B2B, Cache, GraphQL
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# B2B-2674: Fügt der GraphQL-Abfrage die Caching-Funktion hinzu.`customAttributeMetadata`

Der Patch B2B-2674 fügt den `customAttributeMetadata` GraphQL-Abfragen eine Caching-Funktion hinzu. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID lautet B2B-2674. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7-Beta1 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

`customAttributeMetadata` GraphQL-Abfrage kann nicht zwischengespeichert werden.

<u>Voraussetzungen</u>:

* Der Server verweist auf [!DNL Varnish] proxying to Adobe Commerce Backend.
* Die Konfigurationseinstellung `system/full_page_cache/caching_application` ist auf *2} ([!DNL Varnish]) festgelegt oder navigieren Sie zu Adobe Commerce Admin >**[!UICONTROL Stores]**>**[!UICONTROL System]**>**[!UICONTROL Full Page Cache]**>**[!UICONTROL Caching Application]**und legen Sie sie auf [!DNL Varnish] fest.*

Nachdem der Patch angewendet wurde, führen Sie die folgenden Schritte aus, um sicherzustellen, dass die Zwischenspeicherungsfunktion jetzt verfügbar ist:

1. Senden Sie eine `GET` -Anfrage an die oben aufgeführte GraphQL-Abfrage mit beliebigen Feldern.
1. Senden Sie die Anfrage ohne Änderungen erneut. Sie werden feststellen, dass sie viel schneller ist. Beachten Sie, dass die Anfrage nicht an das Backend gesendet wird, aber vollständig von [!DNL Varnish] als Cache-Treffer verarbeitet wird.
1. Wenn ein weiterer Testversand erforderlich ist, kommentieren Sie die in unserem [VCL](https://github.com/magento/magento2/blob/2.4-develop/app/code/Magento/PageCache/etc/varnish6.vcl#L239) vorhandene Nicht-Header `X-Magento-Debug` aus, starten Sie [!DNL Varnish] neu und führen Sie die oben genannten Schritte erneut aus.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
