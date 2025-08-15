---
title: 'MDVA-44100: Alle FPTs werden dem letzten Produkt im Warenkorb zugeordnet'
description: Der MDVA-44100 Patch löst das Problem, dass alle FTPs dem letzten Produkt im Warenkorb zugeordnet sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44100. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: b370dcbb-cbe9-4f5d-9b8f-1722ab521fcb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-44100: Alle FPTs werden dem letzten Produkt im Warenkorb zugeordnet

Der MDVA-44100 Patch löst das Problem, dass alle FTPs dem letzten Produkt im Warenkorb zugeordnet sind. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-44100. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Alle FPTs werden dem letzten Produkt im Warenkorb zugewiesen und die FPT-Werte für die übrigen Produkte werden zurückgesetzt.

<u>Schritte zur Reproduktion</u>:

1. Wechseln Sie zu **Stores** > **Konfiguration** > **Verkauf** > **Steuer** und legen Sie Folgendes fest:
   * FTP aktivieren = Ja
   * Steuer auf FTP anwenden = Ja
   * FPT in Zwischensumme einschließen = ja
1. Wechseln Sie zu **Stores** > **Attribut** > **Produkt** und erstellen Sie ein neues Attribut mit dem Typ = Feste Produktsteuer.
1. Fügen Sie das -Attribut zu einem Attributsatz hinzu.
1. Erstellen Sie zwei Produkte aus dem Attributsatz und konfigurieren Sie das FTP-Attribut für Ihr Land und Ihr Bundesland.
1. Fügen Sie beide Artikel zur Bestellung hinzu.
1. Geben Sie eine Adresse ein, für die FTP bezahlt werden muss.
1. Bestellung aufgeben.
1. Überprüfen Sie die Artikelliste auf der Bestellung.

<u>Erwartete Ergebnisse</u>:

Die FPTs werden unter jedem Produkt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die FTP-Werte beider Elemente werden unter dem zweiten Element angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
