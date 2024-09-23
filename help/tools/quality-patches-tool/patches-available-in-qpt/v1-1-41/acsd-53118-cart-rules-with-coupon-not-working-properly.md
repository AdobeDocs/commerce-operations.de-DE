---
title: "ACSD-53118: Warenkorbregeln mit Coupon funktionieren nicht ordnungsgemäß"
description: Wenden Sie den Patch ACSD-53118 an, um das Adobe Commerce-Problem zu beheben, bei dem die Preisregel für den Warenkorb mit einem Coupon-Code angewendet wird, während das Produkt im Warenkorb über ein leeres übereinstimmendes Attribut verfügt.
feature: Shopping Cart, Price Rules
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-53118: Warenkorbregeln mit Coupon funktionieren nicht ordnungsgemäß

Der Patch ACSD-53118 behebt das Problem, dass die Preisregel für den Warenkorb mit einem Coupon-Code angewendet wird, während das Produkt im Warenkorb über ein leeres übereinstimmendes Attribut verfügt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41 installiert ist. Die Patch-ID ist ACSD-53118. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Preisregel für Warenkorb wird mit einem Coupon-Code angewendet, während das Produkt im Warenkorb über ein leeres entsprechendes Attribut verfügt.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Preisattribut und fügen Sie es zum Attributsatz hinzu. Machen Sie das Attribut in Bedingungen für Angebotsregeln nutzbar.
1. Erstellen Sie ein Produkt und lassen Sie das neue Attribut leer.
1. Erstellen Sie eine Preisregel für den Warenkorb mit einem bestimmten Coupon und der folgenden Bedingung:

   * Wenn ein Artikel im Warenkorb mit ALLEN dieser Bedingungen gefunden wird: Attribut1 ist 0.

1. Fügen Sie das in Schritt 2 erstellte Produkt zum Warenkorb hinzu.
1. Verwenden Sie den Gutscheincode für die in Schritt 3 erstellte Warenkorbregel.

<u>Erwartete Ergebnisse</u>:

Der Rabatt gilt nicht für den Warenkorb.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt gilt für den Warenkorb.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
