---
title: 'MDVA-40101: Artikel bleiben nach der Bestellplatzierung Mini-Warenkorb PayPal Express Checkout'
description: Der MDVA-40101 Patch behebt das Problem, dass Artikel nach einer erfolgreichen Bestellplatzierung mit dem PayPal Express Checkout nicht aus dem Mini-Warenkorb entfernt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40101. Beachten Sie, dass das Problem in Adobe Commerce 2.4.0 behoben wurde.
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
exl-id: 8d3fa92e-39ed-4d8f-8dbe-9c08f787c6f1
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-40101: Artikel bleiben nach der Bestellplatzierung Mini-Warenkorb PayPal Express Checkout

Der MDVA-40101 Patch behebt das Problem, dass Artikel nach einer erfolgreichen Bestellplatzierung mit dem PayPal Express Checkout nicht aus dem Mini-Warenkorb entfernt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40101. Beachten Sie, dass das Problem in Adobe Commerce 2.4.0 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Artikel verbleiben auch nach erfolgreicher Bestellplatzierung per PayPal Express Checkout im Mini-Warenkorb.

<u>Schritte zur Reproduktion</u>:

Bestellen Sie per PayPal Express Checkout im Inkognito-Modus in einem Browser.

<u>Erwartete Ergebnisse</u>:

Der Mini-Warenkorb sollte nach erfolgreichem Abschluss der Bestellung leer sein.

<u>Tatsächliche Ergebnisse</u>:

* Auf der Erfolgsseite wird ein leerer Mini-Warenkorb angezeigt.
* Auf allen anderen Seiten wird ein Mini-Warenkorb mit gekauften Artikeln angezeigt.
* Ein Klick auf den Warenkorb-Link leitet Sie zu einer leeren Warenkorbseite weiter.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
