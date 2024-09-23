---
title: "ACSD-48044: Das Anwenden mehrerer Geschenkkarten verhindert, dass Bestellungen aufgegeben werden"
description: Wenden Sie den Patch ACSD-48044 an, um das Adobe Commerce-Problem zu beheben, bei dem die Anwendung mehrerer Geschenkkarten auf eine einzige Bestellung mit mehreren Sendungen verhindert, dass Bestellungen aufgegeben werden.
feature: Admin Workspace, Gift, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# ACSD-48044: Das Anwenden mehrerer Geschenkkarten verhindert, dass Bestellungen aufgegeben werden

Der Patch ACSD-48044 behebt das Problem, dass das Anwenden mehrerer Geschenkkarten auf eine einzige Bestellung mit mehreren Sendungen verhindert, dass Bestellungen aufgegeben werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 installiert ist. Die Patch-ID lautet ACSD-48044. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Durch die Anwendung mehrerer Geschenkkarten auf eine einzige Bestellung mit mehrfachem Versand wird verhindert, dass Bestellungen aufgegeben werden.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie eine saubere Version von Adobe Commerce.
1. Erstellen Sie ein einfaches Produkt mit einem Preis von 100 $ und ein weiteres einfaches Produkt mit einem Preis von 10 $.
1. Melden Sie sich bei [!UICONTROL Admin panel] an und erstellen Sie zwei Geschenkkarten.

   * 02 KB8M0H0GRD = 50 USD
   * 00GXM6SUGBLW = 25 USD

1. Erstellen Sie einen Kunden mit zwei Adressen.
1. Fügen Sie zwei Produkte zum Warenkorb hinzu.

   * Fügen Sie zuerst das 10-Dollar-Produkt hinzu und fügen Sie dann das 100-Dollar-Produkt hinzu. Das Problem kann nicht reproduziert werden, wenn das 100-Dollar-Produkt zuerst hinzugefügt wird.

1. Gehen Sie zum Warenkorb und fügen Sie die beiden von Ihnen erstellten Geschenkkarten hinzu.
1. Klicken Sie auf **[!UICONTROL Ship to Multiple Addresses]** auf der Warenkorbseite.
1. Weisen Sie jedes Produkt einer anderen Adresse zu.
1. Gehen Sie zur Seite &quot;**[!UICONTROL Shipping information]**&quot;.
1. Gehen Sie zur Seite &quot;**[!UICONTROL Billing information]**&quot;.
1. Gehen Sie zur Seite &quot;**[!UICONTROL Review Your Order]**&quot;, auf der das Problem angezeigt wird.
1. Versuchen Sie, die Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

* Geschenkkarten werden korrekt auf den Gesamtbetrag angewendet.
* Bestellungen werden platziert.

<u>Tatsächliche Ergebnisse</u>:

Die Geldbeträge der Geschenkkarte werden mit dem Fehler *&quot;Bitte korrigieren Sie den Geschenkkartencode.&quot;* beim Platzieren der Bestellung.

* Erstes Produkt:

   * Entfernen Sie die Geschenkkarte (00GXM6SUGBLW) - $15.00
   * Gift-Karte entfernen (02 KB8M0H0GRD) - 0,00 USD

* Zweites Produkt:

   * Entfernen Sie die Geschenkkarte (00GXM6SUGBLW) - 25,00 $
   * Gift-Karte entfernen (02 KB8M0H0GRD) - 35,00 USD

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
