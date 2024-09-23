---
title: "ACSD-45488: Konfigurierbares Produkt mit mehreren Quellen, die nicht automatisch auf Lager sind"
description: Der Patch ACSD-45488 behebt das Problem, dass ein konfigurierbares Produkt mit mehreren Quellen nicht automatisch auf Lager zurückgegeben wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-45488. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-45488: Konfigurierbares Produkt mit mehreren Quellen, die nicht automatisch auf Lager sind

Der Patch ACSD-45488 behebt das Problem, dass ein konfigurierbares Produkt mit mehreren Quellen nicht automatisch auf Lager zurückgegeben wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID lautet ACSD-45488. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein konfigurierbares Produkt mit mehreren Quellen wird nicht automatisch auf Lager zurückgegeben.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine sekundäre Lagerquelle.
1. Erstellen Sie ein konfigurierbares Produkt mit zwei zugehörigen virtuellen Produkten.
1. Weisen Sie die verknüpften Produkte der Standardlagerquelle zu und setzen Sie die Menge auf 1.
1. Überprüfen Sie die `stock_status` von `cataloginventory_stock_status`.
1. Setzen Sie beide verknüpften Produkte auf *nicht vorrätig*.
1. Überprüfen Sie die `stock_status` von `cataloginventory_stock_status`.
1. Setzen Sie beide verknüpften Produkte auf &quot;*auf Lager*&quot;.
1. Überprüfen Sie die `stock_status` von `cataloginventory_stock_status`.

<u>Erwartete Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts wird auf *auf Lager* aktualisiert, wenn die verknüpften Produkte auf Lager eingestellt sind.

<u>Tatsächliche Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts wird nicht auf *in stock* aktualisiert, wenn die verknüpften Produkte auf &quot;stock&quot;eingestellt sind.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
