---
title: 'ACSD-48044: Durch mehrere Geschenkgutscheine wird verhindert, dass Bestellungen aufgegeben werden'
description: Wenden Sie den Patch ACSD-48044 an, um das Adobe Commerce-Problem zu beheben, bei dem das Anwenden mehrerer Geschenkgutscheine auf eine Bestellung mit Mehrfachversand verhindert, dass Bestellungen aufgegeben werden.
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%
---
# ACSD-48044: Durch mehrere Geschenkgutscheine wird verhindert, dass Bestellungen aufgegeben werden

Mit dem Patch ACSD-48044 wird das Problem behoben, dass das Anwenden mehrerer Geschenkkarten auf eine Bestellung mit Mehrfachversand verhindert, dass Bestellungen aufgegeben werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25 installiert ist. Die Patch-ID ist ACSD-48044. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

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

Die Beträge der Geschenkkarte werden mit dem Fehler *Bitte korrigieren Sie den Geschenkkartencode“* bei Auftragserteilung.

* Erstes Produkt:

  * Geschenkkarte entfernen (00GXM6SUGBLW) - $15.00
  * Geschenkkarte entfernen (02KB8M0H0GRD) - $0.00

* Zweites Produkt:

  * Geschenkkarte entfernen (00GXM6SUGBLW) - $25.00
  * Geschenkkarte entfernen (02KB8M0H0GRD) - $35.00

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
