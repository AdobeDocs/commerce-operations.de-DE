---
title: 'ACSD-52906: Beheben des Problems mit X-Magento-Vary-Cookies für das Caching angemeldeter Kunden'
description: Wenden Sie den Patch ACSD-52906 an, um das Adobe Commerce-Problem zu beheben, bei dem das X-Magento-Vary-Cookie für angemeldete Kunden falsch gesetzt ist.
feature: Cache
role: Admin, Developer
exl-id: 487b7588-7131-4502-b714-05f37520991f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-52906: Beheben des Problems mit X-Magento-Vary-Cookies für angemeldete Kunden

Mit dem Patch ACSD-52906 wird das Problem behoben, dass das Cookie X-Magento-Vary für angemeldete Kunden falsch festgelegt ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.36 installiert ist. Die Patch-ID ist ACSD-52906. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das X-Magento-Vary-Cookie wird für angemeldete Kunden, die zum selben Kundensegment gehören, falsch gesetzt, was bei einigen Seiten zu einer fehlerhaften Zwischenspeicherung führt.

<u>Voraussetzungen</u>:

Adobe Commerce Inventory management (MSI)-Module sind installiert und aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie [!DNL Varnish]- oder [!DNL Fastly]-Cache.
1. Erstellen Sie ein neues Kundensegment und weisen Sie es den (*)* Kunden zu.
1. Erstellen Sie zwei Kunden, z. B. customer1 und customer2.
1. Löschen Sie den Cache.
1. Melden Sie sich als customer1 an und gehen Sie zur Startseite.
1. Öffnen Sie eine Inkognito-Seite in Ihrem Browser.
1. Wechseln Sie zu einer beliebigen Seite außer der Startseite.
1. Melden Sie sich als customer2 an.
1. Navigieren Sie zur Startseite.
1. Überprüfen Sie, ob die Seite in der Entwicklungs-Konsole des Browsers zwischengespeichert ist.

<u>Erwartete Ergebnisse</u>:

Die Seite wird aus dem Cache abgerufen.

<u>Tatsächliche Ergebnisse</u>:

Die Seite wird nicht zwischengespeichert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
