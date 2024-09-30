---
title: "ACSD-53204: *Das Produkt kann nicht gespeichert werden* Fehler bei gleichzeitigen Anfragen zum Hinzufügen von Bildern zur Galerie."
description: Wenden Sie den Patch ACSD-53204 an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler *Das Produkt kann nicht gespeichert werden* ausgegeben wird, wenn gleichzeitige Anfragen zum Hinzufügen von Bildern zur Produktgalerie mit dem Endpunkt rest/V1/products/&lt;sku&gt;/media gesendet werden.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53204: Fehler &quot;*Das Produkt kann nicht gespeichert werden*&quot; bei gleichzeitigen Anforderungen zum Hinzufügen von Bildern zur Galerie

Der Patch ACSD-53204 behebt das Problem, bei dem der Fehler &quot;*Das Produkt kann nicht gespeichert werden*&quot; ausgegeben wird, wenn gleichzeitige Anfragen zum Hinzufügen von Bildern zur Produktgalerie mithilfe des Endpunkts `rest/V1/products/<sku>/media` gestellt werden. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.39 installiert ist. Die Patch-ID ist ACSD-53204. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Fehler &quot;*Das Produkt kann nicht gespeichert werden*&quot; wird ausgegeben, wenn gleichzeitige Anfragen zum Hinzufügen von Bildern zur Produktgalerie mithilfe des `rest/V1/products/<sku>/media` -Endpunkts gestellt werden.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich beim Admin Panel an.
1. Erstellen Sie ein Produkt mit SKU p1.
1. Stellen Sie mehrere gleichzeitige Anfragen an den `rest/V1/products/<sku>/media` -Endpunkt, um mehrere Bilder gleichzeitig hochzuladen.

<u>Erwartete Ergebnisse</u>:

Die Bilder werden fehlerfrei gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der Fehler &quot;*Das Produkt kann nicht gespeichert werden*&quot; wird von Zeit zu Zeit zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
