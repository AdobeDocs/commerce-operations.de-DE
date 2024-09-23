---
title: "MDVA-39163: Versandmethoden nicht für neu registrierte Benutzer mit Produkten aus Gastsitzungen verfügbar"
description: Der Patch MDVA-39163 behebt das Problem, dass die Versandmethoden nicht verfügbar sind, wenn ein neuer Benutzer registriert wird und Produkte aus der Gastsitzung stammen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-39163. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# MDVA-39163: Versandmethoden für neu registrierte Benutzer mit Produkten aus Gastsitzungen nicht verfügbar

Der Patch MDVA-39163 behebt das Problem, dass die Versandmethoden nicht verfügbar sind, wenn ein neuer Benutzer registriert wird und Produkte aus der Gastsitzung stammen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-39163. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Versandmethoden sind nicht verfügbar, wenn der neue Benutzer registriert wird und Produkte im Warenkorb aus der Gastsitzung stammen.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **Admin** > **Stores** > **Konfiguration** > **Verkauf** > **Bereitstellungsmethoden**. Aktivieren Sie nur die Versandmethode **Pauschalsatz** und deaktivieren Sie alle anderen Optionen.
1. Wählen Sie in der Versandmethode **Pauschalsatz** die Option **Spezifisches Land** aus, die in der Einstellung **In Gültige Länder versenden** verfügbar ist, und wählen Sie ein Land aus der Liste aus (z. B. USA).
1. Wechseln Sie zu **Admin** > **Geschäfte** > **Konfiguration** > **Kunde** > **Kundenkonfiguration** und legen Sie **E-Mail-Bestätigung erforderlich** auf _Ja_ fest.
1. Erstellen Sie eine neue E-Mail-Vorlage in &quot;**Admin**&quot;> &quot;**Marketing**&quot;> &quot;**E-Mail-Vorlagen**&quot;, laden Sie die Vorlage &quot;`Footer (magento/luma)`&quot; und ersetzen Sie den Vorlageninhalt durch einen CMS-Block.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Navigieren Sie zu **Admin** > **Inhalt** > **Design** > **Konfiguration** und wählen Sie das Design aus, das sich auf Ihre Frontend-Website bezieht. Wählen Sie für die Fußzeilenvorlage die neu erstellte E-Mail-Vorlage aus.
1. Gehen Sie zum Frontend und fügen Sie dem Warenkorb ein Produkt hinzu.
1. Erstellen Sie einen Kunden. Sie erhalten eine E-Mail, um die E-Mail-Adresse zu bestätigen. Klicken Sie auf den Verifizierungslink. Sie werden auf der Webseite angemeldet.
1. Gehen Sie zu **Mein Konto** und fügen Sie eine Adresse hinzu. Legen Sie das Adressland auf das Versandland fest, das Sie zuvor in der Admin-Konfiguration festgelegt haben.
1. Gehen Sie zum Checkout.

<u>Erwartete Ergebnisse</u>:

Versandmethode ist verfügbar, da der Kunde eine Adresse hat, die mit dem Versandland kompatibel ist.

<u>Tatsächliche Ergebnisse</u>:

Die Versandmethode ist nicht verfügbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
