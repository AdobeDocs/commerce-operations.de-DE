---
title: 'ACSD-54966: Fehlerbehebung bei der Wiederverwendung von Gutscheincodes nach fehlgeschlagenen Bestellungen'
description: Wenden Sie den Patch ACSD-54966 an, um das Adobe Commerce-Problem zu beheben, das die Wiederverwendung von Gutscheincodes verhindert, die nach einer zuvor fehlgeschlagenen Bestellung pro Werbeaktion und Warenkorb begrenzt sind.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: e08062e5-62ff-4da6-918f-896af36edccc
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-54966: Fehlerbehebung bei der Wiederverwendung von Gutscheincodes nach fehlgeschlagenen Bestellungen

Mit dem Patch ACSD-54966 wird das Problem behoben, das die Wiederverwendung von Couponcodes pro Kunde nach einer zuvor fehlgeschlagenen Bestellung verhindert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 installiert ist. Die Patch-ID ist ACSD-54966. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Couponcode, der auf den einmaligen Gebrauch pro Kunde beschränkt ist, kann nach einer fehlgeschlagenen vorherigen Bestellung nicht wiederverwendet werden.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie eine Warenkorb-Preisregel mit *[!UICONTROL Uses per Customer]* = *1* ein.
1. Machen Sie einen Kauf mit dem zugewiesenen Gutscheincode.
1. Stornieren Sie die Bestellung im Admin-Panel oder führen Sie die Bestellung mit einem Zahlungsfehler aus.
1. Führen Sie den folgenden Befehl aus: `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Versuchen Sie, eine nachfolgende Bestellung mit demselben Couponcode für denselben Kunden aufzugeben.

<u>Erwartete Ergebnisse</u>:

Nach Stornierung der Bestellung oder einem Zahlungsfehler kann der Kunde den Couponcode erfolgreich für einen neuen Kauf wiederverwenden.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde kann den Gutscheincode nicht wiederverwenden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
