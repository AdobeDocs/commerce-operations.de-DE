---
title: 'MDVA-39163: Versandmethoden für neu registrierte Benutzer mit Produkten aus der Gastsitzung nicht verfügbar'
description: Der MDVA-39163 Patch löst das Problem, dass die Versandmethoden nicht verfügbar sind, wenn ein neuer Benutzer registriert ist und Produkte im Warenkorb aus der Gastsitzung stammen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-39163. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
exl-id: 781b466b-7d8f-4ad1-9fb4-5404cd02f7d8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# MDVA-39163: Versandmethoden für neu registrierte Benutzer mit Produkten aus der Gastsitzung nicht verfügbar

Der MDVA-39163 Patch löst das Problem, dass die Versandmethoden nicht verfügbar sind, wenn ein neuer Benutzer registriert ist und Produkte im Warenkorb aus der Gastsitzung stammen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-39163. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Versandmethoden sind nicht verfügbar, wenn der neue Benutzer registriert ist, und Produkte im Warenkorb stammen aus der Gastsitzung.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie **Admin** > **Stores** > **Konfiguration** > **Verkauf** > **Versandmethoden**. Aktivieren Sie nur die Versandmethode **Flat Rate** und deaktivieren Sie alles andere.
1. Wählen Sie in der Versandart **Flat Rate** die Option **Specific** country, die in der Einstellung **In zutreffende Länder versenden** verfügbar ist, und wählen Sie ein Land aus der Liste aus (z. B. Vereinigte Staaten).
1. Gehen Sie zu **Admin** > **Stores** > **Configuration** > **Customer** > **Customer Configuration** und setzen Sie **Require email confirmation** auf _Yes_.
1. Erstellen Sie eine neue E-Mail-Vorlage unter **Admin** > **Marketing** > **E-Mail-**, laden Sie `Footer (magento/luma)` Vorlage und ersetzen Sie den Vorlageninhalt durch einen CMS-Block.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Gehen Sie **Admin** > **Inhalt** > **Design** > **Konfiguration** und wählen Sie das Design aus, das sich auf Ihre Frontend-Website bezieht. Legen Sie die „Fußzeilen-Vorlage“ auf die neu erstellte E-Mail-Vorlage fest.
1. Gehen Sie zum Frontend und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Kunden erstellen; Sie erhalten eine E-Mail zur Bestätigung der E-Mail-Adresse. Klicken Sie auf den Bestätigungs-Link. Sie werden bei der Website eingeloggt.
1. Gehen Sie zu **Mein Konto** und fügen Sie eine Adresse hinzu. Legen Sie die Länderadresse auf das Versandland fest, das Sie zuvor in der Admin-Konfiguration festgelegt haben.
1. Zur Kasse gehen.

<u>Erwartete Ergebnisse</u>:

Die Versandart ist verfügbar, da der Kunde eine Adresse hat, die mit dem Versandland kompatibel ist.

<u>Tatsächliche Ergebnisse</u>:

Versandart ist nicht verfügbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
