---
title: "ACSD-54966: Fix for reuse coupon codes after failed orders"
description: Wenden Sie den Patch ACSD-54966 an, um das Adobe Commerce-Problem zu beheben, das die Wiederverwendung von Coupon-Codes verhindert, die pro Promotion und Warenkorb nach einer zuvor fehlgeschlagenen Bestellung begrenzt sind.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-54966: Fehlerkorrektur - Verwendung von Couponcodes nach fehlgeschlagenen Bestellungen

Der Patch ACSD-54966 behebt das Problem, das die Wiederverwendung von Coupon-Codes verhindert, die pro Kunde nach einer zuvor fehlgeschlagenen Bestellung begrenzt sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 installiert ist. Die Patch-ID ist ACSD-54966. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Ein Gutscheincode, der für die einmalige Verwendung pro Kunde begrenzt ist, kann nicht nach einer fehlgeschlagenen vorherigen Bestellung wiederverwendet werden.

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie eine Preisregel für den Warenkorb mit *[!UICONTROL Uses per Customer]* = *1* ein.
1. Fahren Sie mit dem zugewiesenen Couponcode fort, um einen Kauf zu tätigen.
1. Brechen Sie die Bestellung im Admin Panel ab oder führen Sie die Bestellung bei einem Zahlungsfehler aus.
1. Führen Sie den Befehl aus: `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Versuchen Sie, eine nachfolgende Bestellung mit demselben Couponcode für denselben Kunden aufzugeben.

<u>Erwartete Ergebnisse</u>:

Nachdem die Bestellung storniert wurde oder ein Zahlungsfehler auftritt, kann der Kunde den Gutscheincode erfolgreich für einen neuen Kauf wiederverwenden.

<u>Tatsächliche Ergebnisse</u>:

Der Kunde kann den Gutscheincode nicht wiederverwenden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
