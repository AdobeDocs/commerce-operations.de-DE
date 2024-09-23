---
title: "ACSD-52399: Produkt mit verkaufsfähiger Menge 0 zeigt Lager an"
description: Wenden Sie den Patch ACSD-52399 an, um das Adobe Commerce-Problem zu beheben, bei dem die konfigurierbare Produktoption mit der Verkaufsmenge "0"auf der Produktseite *In Stock* angezeigt wird.
feature: Products, Configuration
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52399: Produkt mit verkaufsfähiger Menge 0 wird vorrätig angezeigt

Der Patch ACSD-52399 behebt das Problem, bei dem die konfigurierbare Produktoption mit einer verkäuflichen Menge von null (0) *Auf Lager* auf der Produktseite anzeigt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52399. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die konfigurierbare Produktoption mit einer verkäuflichen Menge von null (0) zeigt *Auf Lager* auf der Produktseite an.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einer Produktoption für eine Verkaufsmenge von null (0).
1. Gehen Sie zur Produktseite in der Storefront und wählen Sie das konfigurierbare Produkt aus, um eine Variante/Konfiguration zu überprüfen.
1. Wählen Sie **[!UICONTROL Add to Cart]** aus.

<u>Erwartete Ergebnisse</u>:

Die Schaltfläche *[!UICONTROL Add to Cart]* ist nicht verfügbar, wenn Sie die Produktkonfiguration *Nicht vorrätig* auswählen.

<u>Tatsächliche Ergebnisse</u>:

Konfigurierbare Varianten sind in der Storefront verfügbar. Sie können sie auswählen und zum Warenkorb hinzufügen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
