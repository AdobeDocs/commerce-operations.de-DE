---
title: "ACSD-52906: Beheben eines X-Magento-Vary-Cookie-Problems beim angemeldeten Kunden-Caching"
description: Wenden Sie den Patch ACSD-52906 an, um das Adobe Commerce-Problem zu beheben, bei dem das X-Magento-Vary-Cookie für angemeldete Kunden falsch gesetzt wurde.
feature: Cache
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-52906: Beheben eines Cookie-Problems mit X-Magento-Vary für angemeldete Kunden

Der Patch ACSD-52906 behebt das Problem, dass das X-Magento-Vary-Cookie für angemeldete Kunden falsch gesetzt wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.36 installiert ist. Die Patch-ID ist ACSD-52906. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das X-Magento-Vary-Cookie wird für angemeldete Kunden, die zum selben Kundensegment gehören, falsch gesetzt, was bei einigen Seiten zu unsachgemäßem Caching führt.

<u>Voraussetzungen</u>:

Adobe Commerce Inventory management (MSI)-Module werden installiert und aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie den Cache [!DNL Varnish] oder [!DNL Fastly].
1. Erstellen Sie ein neues Kundensegment und weisen Sie es den *Registrierten* -Kunden zu.
1. Erstellen Sie zwei Kunden, z. B. customer1 und customer2.
1. Löschen Sie den Cache.
1. Melden Sie sich als customer1 an und rufen Sie die Startseite auf.
1. Öffnen Sie eine Inkognito-Seite in Ihrem Browser.
1. Navigieren Sie zu einer anderen Seite als der Startseite.
1. Melden Sie sich als customer2 an.
1. Rufen Sie die Startseite auf.
1. Überprüfen Sie, ob die Seite in der Browser-Entwicklungskonsole zwischengespeichert ist.

<u>Erwartete Ergebnisse</u>:

Die Seite wird aus dem Cache abgerufen.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird nicht zwischengespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
