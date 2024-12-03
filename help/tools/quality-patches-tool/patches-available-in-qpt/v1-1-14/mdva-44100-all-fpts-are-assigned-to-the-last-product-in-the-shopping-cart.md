---
title: 'MDVA-44100: Alle FPTs werden dem letzten Produkt im Warenkorb zugewiesen'
description: Der Patch MDVA-44100 behebt das Problem, dass alle FPTs dem letzten Produkt im Warenkorb zugewiesen werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44100. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: b370dcbb-cbe9-4f5d-9b8f-1722ab521fcb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-44100: Alle FPTs werden dem letzten Produkt im Warenkorb zugewiesen

Der Patch MDVA-44100 behebt das Problem, dass alle FPTs dem letzten Produkt im Warenkorb zugewiesen werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44100. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Alle FPTs werden dem letzten Produkt im Warenkorb zugewiesen und die FPT-Werte für die übrigen Produkte werden zurückgesetzt.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **Stores** > **Configuration** > **Sales** > **Tax** und legen Sie Folgendes fest:
   * FPT aktivieren = Ja
   * Steuern auf FPT anwenden = Ja
   * FPT in Zwischensumme einschließen = Ja
1. Wechseln Sie zu **Stores** > **Attribut** > **Produkt** und erstellen Sie ein neues Attribut mit dem Typ = Feste Produktsteuer.
1. Fügen Sie das Attribut einem Attributsatz hinzu.
1. Erstellen Sie zwei Produkte aus dem Attributsatz und konfigurieren Sie das FPT-Attribut für Ihr Land und Ihren Staat.
1. Fügen Sie beide Elemente zur Bestellung hinzu.
1. Geben Sie eine Adresse ein, für die FPT bezahlt werden muss.
1. Platzieren Sie die Bestellung.
1. Überprüfen Sie die Elementliste in der Bestellung.

<u>Erwartete Ergebnisse</u>:

Die FPTs werden unter jedem Produkt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die FPT-Werte aus beiden Elementen werden unter dem zweiten Element angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
