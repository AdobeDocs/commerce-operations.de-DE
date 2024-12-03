---
title: 'MDVA-42855: Neue Kundenadresse wird beim Checkout nicht im Adressbuch gespeichert '
description: Der Patch MDVA-42855 behebt das Problem, dass die neue Kundenadresse beim Checkout nicht im Adressbuch gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42855. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Checkout, Orders, Shipping/Delivery
role: Admin
exl-id: 924b8f57-1fec-4e62-bf0e-1f9cafa75cab
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-42855: Neue Kundenadresse wird beim Checkout nicht im Adressbuch gespeichert

Der Patch MDVA-42855 behebt das Problem, dass die neue Kundenadresse beim Checkout nicht im Adressbuch gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42855. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die neue Kundenadresse wird beim Checkout nicht im Adressbuch gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Kundenkonto und aktualisieren Sie die standardmäßige Versand- und Rechnungsadresse.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und navigieren Sie zur Checkout-Seite.
1. Klicken Sie beim Versand auf **+ Neue Adresse**.
1. Geben Sie Ihre neue Adresse ein und lassen Sie das Kontrollkästchen **Im Adressbuch speichern** angekreuzt.
1. Wenn Sie zahlen, kreuzen Sie das Kontrollkästchen **Meine Abrechnungs- und Lieferadresse sind dieselben** an.
1. Platzieren Sie die Bestellung.
1. Überprüfen Sie das Adressbuch.

<u>Erwartete Ergebnisse</u>:

Die neue Lieferadresse wird im Adressbuch gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Die neue Lieferadresse wird nicht im Adressbuch gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
