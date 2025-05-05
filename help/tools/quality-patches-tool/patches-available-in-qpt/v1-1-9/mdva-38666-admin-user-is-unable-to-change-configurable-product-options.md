---
title: 'MDVA-38666: Admin-Benutzer kann konfigurierbare Produktoptionen nicht ändern'
description: Der Patch MDVA-38666 löst das Problem, dass der Administrator bzw. die Administratorin nicht in der Lage ist, konfigurierbare Produktoptionen im Warenkorb des Kunden zu ändern. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-38666. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Admin Workspace, Configuration, Products
role: Admin
exl-id: 8e72f6a4-b36f-4fe4-bc01-2254984dd512
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-38666: Admin-Benutzer kann konfigurierbare Produktoptionen nicht ändern

Der Patch MDVA-38666 löst das Problem, dass der Administrator bzw. die Administratorin nicht in der Lage ist, konfigurierbare Produktoptionen im Warenkorb des Kunden zu ändern. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-38666. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator bzw. die Administratorin kann die konfigurierbaren Produktoptionen im Warenkorb des Kunden nicht ändern.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie den Kundenkontobereich auf „Global“ fest.
1. Erstellen Sie zwei Websites mit Stores.
1. Erstellen Sie zwei konfigurierbare Produkte und weisen Sie sie jeder Website zu.
1. Erstellen Sie ein Kundenkonto im Frontend und melden Sie sich an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und checken Sie es aus (dies erfolgt, um die Angebots-IDs auf jeder Website zu verändern).
1. Fügen Sie ein Produkt zum Warenkorb hinzu und lassen Sie es.
1. Wechseln Sie zur zweiten Website und fügen Sie das Produkt zum Warenkorb hinzu (die gleiche Anmeldung sollte funktionieren, da der Umfang des Kundenkontos auf „global“ festgelegt ist).
1. Öffnen Sie den Kunden über die Admin Console und navigieren Sie zur Registerkarte Warenkorb .
1. Wechseln Sie den Store aus der Dropdown-Liste und versuchen Sie, die Konfiguration zu ändern.

<u>Erwartete Ergebnisse</u>:

Der Benutzer erhält ein Popup mit konfigurierbaren Optionen.

<u>Tatsächliche Ergebnisse</u>:

Es wird kein Popup-Formular angezeigt. Der/die Benutzende kann die Konfiguration nicht ändern.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
