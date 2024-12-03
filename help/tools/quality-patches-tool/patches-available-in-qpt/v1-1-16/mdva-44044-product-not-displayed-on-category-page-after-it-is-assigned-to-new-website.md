---
title: 'MDVA-44044: Produkt wird nicht auf der Kategorieseite angezeigt, nachdem es einer neuen Website zugewiesen wurde'
description: Der Patch MDVA-44044 behebt das Problem, dass ein Produkt nicht auf der Kategorieseite angezeigt wird, nachdem es einer neuen Website zugewiesen wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44044. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
feature: Categories, Products
role: Admin
exl-id: ae797cdc-5977-40b8-82da-ccf364466bdf
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44044: Produkt wird nicht auf der Kategorieseite angezeigt, nachdem es einer neuen Website zugewiesen wurde

Der Patch MDVA-44044 behebt das Problem, dass ein Produkt nicht auf der Kategorieseite angezeigt wird, nachdem es einer neuen Website zugewiesen wurde. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44044. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produkt wird nicht auf der Kategorieseite angezeigt, nachdem es einer neuen Website zugewiesen wurde.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie den Indexermodus auf den Zeitplan fest.
1. Erstellen Sie eine sekundäre Website-, Store- und Store-Ansicht.
1. Fügen Sie einen sekundären Store-Code in `index.php` hinzu:

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. Erstellen Sie eine neue Kategorie.
1. Erstellen Sie ein neues Produkt, das der neu erstellten Kategorie zugewiesen ist. Stellen Sie sicher, dass Sie ihn nur der primären Website zuweisen.
1. Führen Sie den Cron aus.
1. Öffnen Sie die Kategorie in der Storefront.
1. Weisen Sie das Produkt der sekundären Website zu.
1. Führen Sie den Cron erneut aus.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird auf der Kategorieseite nach einem geplanten Indexer angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird erst bei vollständiger Neuindizierung auf der Kategorieseite angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
