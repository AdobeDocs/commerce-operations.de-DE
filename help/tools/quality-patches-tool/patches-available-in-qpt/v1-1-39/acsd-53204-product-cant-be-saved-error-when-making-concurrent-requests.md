---
title: 'ACSD-53204: *Das Produkt kann nicht gespeichert werden* Fehler bei gleichzeitigen Anfragen, Bilder zur Galerie hinzuzufügen'
description: Wenden Sie den ACSD-53204-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler „Das Produkt kann nicht gespeichert werden“ ausgegeben wird, wenn gleichzeitige Anfragen zum Hinzufügen von Bildern zur Produktgalerie mithilfe des REST/V1/products/&lt;sku&gt;/media-Endpunkts gestellt werden.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: 7fdf41e5-46ef-4505-b8ce-c330bd899fa1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53204: Fehler *Das Produkt kann nicht gespeichert werden* bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Galerie

Der Patch ACSD-53204 behebt das Problem, dass der Fehler &quot;*Das Produkt kann nicht gespeichert werden*&quot; ausgegeben wird, wenn gleichzeitige Anfragen zum Hinzufügen von Bildern zur Produktgalerie mithilfe des `rest/V1/products/<sku>/media`-Endpunkts gestellt werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.39 installiert ist. Die Patch-ID ist ACSD-53204. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei *Anfragen zum Hinzufügen von Bildern zur Produktgalerie mithilfe des `rest/V1/products/<sku>/media`-Endpunkts wird der Fehler &quot;* Produkt kann nicht gespeichert werden“ ausgelöst.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Admin Panel an.
1. Erstellen Sie ein Produkt mit SKU p1.
1. Stellen Sie mehrere gleichzeitige Anfragen an den `rest/V1/products/<sku>/media`-Endpunkt, um mehrere Bilder gleichzeitig hochzuladen.

<u>Erwartete Ergebnisse</u>:

Die Bilder werden fehlerfrei gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der *„Das Produkt kann nicht gespeichert werden*&quot; wird von Zeit zu Zeit zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
