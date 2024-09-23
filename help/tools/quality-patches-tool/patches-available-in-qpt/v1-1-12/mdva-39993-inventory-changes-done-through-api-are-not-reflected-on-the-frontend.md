---
title: "MDVA-39993: Über API vorgenommene Bestandsänderungen werden in Storefront nicht berücksichtigt"
description: Der Patch MDVA-39993 behebt das Problem, dass die durch die API vorgenommenen Bestandsänderungen nicht in der Storefront angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39993. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: REST, Inventory, Orders, Storefront
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-39993: Über API durchgeführte Bestandsänderungen werden nicht auf der Storefront angezeigt

Der Patch MDVA-39993 behebt das Problem, dass die durch die API vorgenommenen Bestandsänderungen nicht in der Storefront angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-39993. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.3.7-p2 und 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Bestandsänderungen, die über die API vorgenommen werden, werden nicht auf der Produktseite der Storefront angezeigt.

<u>Voraussetzungen</u>:

Inventarmodule installiert.

<u>Zu reproduzierende Schritte</u>:

1. Stellen Sie sicher, dass die Warteschlange so eingestellt ist, dass sie mit Cron ausgeführt wird und Cron installiert und ausgeführt wird.
1. Erstellen Sie ein konfigurierbares Produkt (COC001) mit zwei Farben (Schwarz und Rot) und zwei Größen (M und L).
1. Eine Option aus dem Lager entfernen (COC001-Red-M).
1. Laden Sie die konfigurierbare Produktseite in die Storefront und versuchen Sie, auf jede Farbe zu klicken. Wenn Sie auf **Rot** klicken, sollte die Größe **M** durchkreuzt werden, da sie nicht vorrätig ist.
1. Machen Sie COC001-Red-M mit dem folgenden API-Endpunkt und der Payload auf Lager:

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. Überprüfen Sie dieses einfache Produkt aus dem Backend und stellen Sie sicher, dass es auf &quot;In Stock&quot;aktualisiert wurde.
1. Laden Sie das konfigurierbare Produkt vom Frontend und klicken Sie auf jede Farbe. Beachten Sie die Größe **M**, wenn Sie auf **Rot** klicken.

<u>Erwartete Ergebnisse</u>:

Die Option COC001-Red-M ist nicht durchkreuzt, da sie über die API auf In Stock aktualisiert wurde.

<u>Tatsächliche Ergebnisse</u>:

Die Option COC001-Red-M ist immer noch ausgekreuzt, obwohl sie auf Lager ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
