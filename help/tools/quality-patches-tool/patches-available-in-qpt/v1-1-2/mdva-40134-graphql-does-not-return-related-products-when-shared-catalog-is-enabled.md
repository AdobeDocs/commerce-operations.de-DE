---
title: "MDVA-40134: GraphQL gibt verwandte Produkte nicht zurück, wenn der freigegebene Katalog aktiviert ist."
description: Der Patch MDVA-40134 behebt das Problem, dass GraphQL verwandte Produkte nicht zurückgibt, wenn der freigegebene Katalog aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-40134. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-40134: GraphQL gibt verwandte Produkte nicht zurück, wenn der freigegebene Katalog aktiviert ist

Der Patch MDVA-40134 behebt das Problem, dass GraphQL verwandte Produkte nicht zurückgibt, wenn der freigegebene Katalog aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-40134. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

GraphQL gibt verwandte Produkte nicht zurück, wenn der freigegebene Katalog aktiviert ist.

<u>Voraussetzungen</u>:

B2B-Module müssen installiert sein.
Die Instanz darf nur mit den Beispieldaten sauber sein.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Stores** > **Konfiguration** > **Allgemein** > **B2B-Funktionen** und aktivieren Sie **Unternehmen und freigegebener Katalog**.
1. Wechseln Sie zu **Katalog** > **Gemeinsamer Katalog** und fügen Sie alle Produkte zum **allgemeinen Katalog** hinzu.
1. Verwenden Sie die Beispieldaten und ändern Sie das Joust Duffle Bag (SKU 24-MB01).
1. Fügen Sie unter **Zugehörige Produkte** die beiden Duffle-Taschen hinzu (ID 7 und 13).
1. Senden Sie eine **Post** -Anfrage:

<pre>{
  products(filter: {sku: {eq: "24-MB01"}, sort: {name: ASC}) {
    items {
      related_products {
        uid
        name
      }
    }
  }
}</pre>

<u>Erwartete Ergebnisse</u>:

Zugehörige Produkte werden in der GraphQL-Antwort angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Benutzer erhalten den folgenden Fehler:

<pre>Der Rückgabewert von Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() muss vom Typ int, null return {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Der Rückgabewert von Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() muss vom Typ int, null zurückgegeben sein </pre>

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
