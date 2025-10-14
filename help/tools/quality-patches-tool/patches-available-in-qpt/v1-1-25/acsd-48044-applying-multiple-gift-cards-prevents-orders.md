---
title: 'ACSD-48044: Durch mehrere Geschenkgutscheine wird verhindert, dass Bestellungen aufgegeben werden'
description: Wenden Sie den Patch ACSD-48044 an, um das Adobe Commerce-Problem zu beheben, bei dem das Anwenden mehrerer Geschenkgutscheine auf eine Bestellung mit Mehrfachversand verhindert, dass Bestellungen aufgegeben werden.
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-48044: Durch mehrere Geschenkgutscheine wird verhindert, dass Bestellungen aufgegeben werden

Mit dem Patch ACSD-48044 wird das Problem behoben, dass das Anwenden mehrerer Geschenkkarten auf eine Bestellung mit Mehrfachversand verhindert, dass Bestellungen aufgegeben werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48044. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Sie mehrere Geschenkgutscheine auf eine Bestellung mit mehreren Versandarten anwenden, wird verhindert, dass Bestellungen aufgegeben werden.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine neue Version von Adobe Commerce.
1. Erstellen Sie ein einfaches Produkt mit einem Preis von 100 $ und ein weiteres einfaches Produkt mit einem Preis von 10 $.
1. Melden Sie sich bei der [!UICONTROL Admin panel] an und erstellen Sie zwei Geschenkkarten.

   * 02KB8M0H0GRD = $50
   * 00GXM6SUGBLW = $25

1. Erstellen Sie einen Kunden mit zwei Adressen.
1. Fügen Sie zwei Produkte zum Warenkorb hinzu.

   * Fügen Sie zuerst das Produkt $10 und dann das Produkt $100 hinzu. Das Problem kann nicht reproduziert werden, wenn zuerst das 100-Dollar-Produkt hinzugefügt wird.

1. Gehen Sie zum Warenkorb und fügen Sie die beiden von Ihnen erstellten Geschenkkarten hinzu.
1. Klicken Sie auf der Warenkorbseite auf **[!UICONTROL Ship to Multiple Addresses]** .
1. Weisen Sie jedes Produkt einer anderen Adresse zu.
1. Navigieren Sie zur Seite **[!UICONTROL Shipping information]** .
1. Navigieren Sie zur Seite **[!UICONTROL Billing information]** .
1. Navigieren Sie zur Seite **[!UICONTROL Review Your Order]** , auf der Sie das Problem sehen können.
1. Versuchen Sie, die Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

* Geschenkgutscheine werden korrekt auf den Gesamtbetrag aufgetragen.
* Bestellungen werden aufgegeben.

<u>Tatsächliche Ergebnisse</u>:

Die Beträge der Geschenkkarte werden mit dem Fehler &quot;*korrigieren Sie den Geschenkkartencode.“ gemischt.* bei der Bestellung.

* Erstes Produkt:

   * Geschenkkarte entfernen (00GXM6SUGBLW) - $15.00
   * Geschenkkarte entfernen (02KB8M0H0GRD) - $0.00

* Zweites Produkt:

   * Geschenkkarte entfernen (00GXM6SUGBLW) - $25.00
   * Geschenkkarte entfernen (02KB8M0H0GRD) - $35.00

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
