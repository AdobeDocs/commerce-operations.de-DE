---
title: 'ACSD-65164: Fehlermeldung bei der Neuanordnung eines konfigurierbaren Produkts mit einer einzelnen benutzerdefinierten Checkbox-Option'
description: Wenden Sie den Patch ACSD-65164 an, um das Adobe Commerce-Problem zu beheben, bei dem die Fehlermeldung *Einige der ausgewählten Elementoptionen sind derzeit nicht verfügbar* angezeigt wird, wenn ein konfigurierbares Produkt mit einer einzigen benutzerdefinierten Kontrollkästchenoption neu bestellt wird.
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-65164: Fehlermeldung bei der Neuanordnung eines konfigurierbaren Produkts mit einer einzelnen benutzerdefinierten Checkbox-Option

Mit dem Patch ACSD-65164 wird das Problem behoben, dass die Fehlermeldung *Einige der ausgewählten Elementoptionen sind derzeit nicht verfügbar* beim Neuanordnen eines konfigurierbaren Produkts mit einer einzelnen benutzerdefinierten Kontrollkästchenoption auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 installiert ist. Die Patch-ID ist ACSD-65164. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei der Neuanordnung eines konfigurierbaren Produkts mit einer einzelnen ausgewählten benutzerdefinierten Kontrollkästchen-Option gibt das System eine Fehlermeldung zurück: *Einige der ausgewählten Elementoptionen sind derzeit nicht verfügbar*.

### Schritte zur Replikation:

1. Navigieren Sie im Admin-Bedienfeld zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]**.
1. Fügen Sie unter **[!UICONTROL Customizable Options]** eine Option *Kontrollkästchen* hinzu.
   * Aktivieren Sie die Option Kontrollkästchen *Erforderlich*.
   * Zwei Optionswerte hinzufügen.
1. Navigieren Sie zur Storefront und melden Sie sich als registrierter Kunde an.
1. Fügen Sie das Produkt zum Warenkorb hinzu, wenn eine Kontrollkästchen-Option ausgewählt ist.
1. Navigieren Sie zu **[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]**.
1. Gehen Sie zu **[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]** , um dasselbe Produkt hinzuzufügen.

**Erwartete Ergebnisse:**

Das Produkt sollte erfolgreich zum Warenkorb hinzugefügt werden.

**Tatsächliche Ergebnisse:**

Eine Fehlermeldung wird angezeigt:

*Das Produkt mit SKU „24-MB01“ konnte nicht zum Warenkorb hinzugefügt werden: Einige der ausgewählten Artikeloptionen sind derzeit nicht verfügbar.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
