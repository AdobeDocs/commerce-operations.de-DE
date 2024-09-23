---
title: "ACSD-56546: Konfigurierbare und gebündelte Produkte werden auf der Storefront als nicht vorrätig angezeigt."
description: Wenden Sie den Patch ACSD-56546 an, um das Adobe Commerce-Problem zu beheben, bei dem die konfigurierbaren und Bundle-Produkte auf der Storefront als nicht vorrätig angezeigt werden, wenn die Konfigurationsoption *[!UICONTROL Display Out of Stock Products]* deaktiviert ist.
feature: Storefront, Products
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-56546: Konfigurierbare und gebündelte Produkte werden auf der Storefront als nicht vorrätig angezeigt

Der Patch ACSD-56546 behebt das Problem, dass die konfigurierbaren und Bundle-Produkte auf der Storefront als nicht vorrätig angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48 installiert ist. Die Patch-ID ist ACSD-56546. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Konfigurierbare und gebündelte Produkte werden auf der Storefront als nicht vorrätig angezeigt, wenn die Option *[!UICONTROL Display Out of Stock Products]* deaktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Setzen Sie die Option **[!UICONTROL Display Out of Stock Products]** auf *Nein*.
1. Erstellen Sie eine Website, einen Store und einen Store.
1. Erstellen Sie eine Quelle und ein Lager und weisen Sie es der zweiten Website zu.
1. Erstellen Sie ein *konfigurierbares Produkt* mit zwei untergeordneten Produkten. Weisen Sie beide untergeordneten Produkte beiden Quellen und beiden Websites zu.
1. Aktualisieren Sie das erste untergeordnete Produkt, sodass es in beiden Quellen *qty=0* enthält.
1. Aktualisieren Sie das zweite untergeordnete Produkt und deaktivieren Sie es auf der zweiten Website.
1. Führen Sie eine vollständige Neuindizierung durch.
1. Überprüfen Sie die Kategorie, die das konfigurierbare Produkt auf der zweiten Website enthält.

<u>Erwartete Ergebnisse</u>:

Die konfigurierbaren Nicht-Lager-Produkte sind auf der Storefront nicht sichtbar.

<u>Tatsächliche Ergebnisse</u>:

Die konfigurierbaren, nicht vorrätigen Produkte sind auch dann auf der Storefront sichtbar, wenn die Option *[!UICONTROL Display Out of Stock Products]* deaktiviert ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
