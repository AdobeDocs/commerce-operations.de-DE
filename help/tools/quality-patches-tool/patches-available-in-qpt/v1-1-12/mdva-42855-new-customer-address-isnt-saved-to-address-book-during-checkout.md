---
title: 'MDVA-42855: Beim Checkout wird keine neue Kundenadresse im Adressbuch gespeichert '
description: Mit dem Patch MDVA-42855 wird das Problem behoben, dass die neue Kundenadresse beim Checkout nicht im Adressbuch gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42855. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Checkout, Orders, Shipping/Delivery
role: Admin
exl-id: 924b8f57-1fec-4e62-bf0e-1f9cafa75cab
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-42855: Beim Checkout wird keine neue Kundenadresse im Adressbuch gespeichert

Mit dem Patch MDVA-42855 wird das Problem behoben, dass die neue Kundenadresse beim Checkout nicht im Adressbuch gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42855. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die neue Kundenadresse wird beim Checkout nicht im Adressbuch gespeichert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Kundenkonto und aktualisieren Sie die standardmäßige Versand- und Rechnungsadresse.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und navigieren Sie zur Kasse .
1. Klicken Sie beim Versand auf **+ Neue Adresse**.
1. Geben Sie Ihre neue Adresse ein, und lassen Sie **Kontrollkästchen „Im Adressbuch**&quot; aktiviert.
1. Aktivieren Sie bei Zahlung das Kontrollkästchen **Meine Rechnungs- und Lieferadresse sind identisch**.
1. Bestellung aufgeben.
1. Schau ins Adressbuch.

<u>Erwartete Ergebnisse</u>:

Die neue Lieferadresse wird im Adressbuch gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Die neue Lieferadresse wird nicht im Adressbuch gespeichert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
