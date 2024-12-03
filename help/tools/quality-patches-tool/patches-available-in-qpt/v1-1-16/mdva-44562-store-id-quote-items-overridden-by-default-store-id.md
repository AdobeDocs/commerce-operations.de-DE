---
title: 'MDVA-44562: Store-ID für Anführungselemente, die durch die standardmäßige Store-ID überschrieben werden'
description: Der Patch MDVA-44562 behebt das Problem, dass die standardmäßige Store-ID die Store-ID für Anführungselemente für GraphQL-Anforderungen überschreibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44562. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562: Store-ID für Anführungselemente, die durch die standardmäßige Store-ID überschrieben werden

Der Patch MDVA-44562 behebt das Problem, dass die standardmäßige Store-ID die Store-ID für Anführungselemente für GraphQL-Anforderungen überschreibt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 installiert ist. Die Patch-ID lautet MDVA-44562. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Store-ID für Anführungselemente wird von der standardmäßigen Store-ID für GraphQL-Anforderungen überschrieben.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Store-Ansicht.
1. Erstellen Sie ein neues einfaches Produkt mit unterschiedlichen Namen pro Store-Ansicht.
1. Erstellen Sie einen neuen Kunden.
1. Besorgen Sie sich das Token für die Kundenautorisierung.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Erstellen Sie mit dem Autorisierungstoken ein neues Angebot für den Kunden.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Fügen Sie dem Warenkorb ein Produkt hinzu.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Rufen Sie den Warenkorbinhalt für die standardmäßige Store-Ansicht ab.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Rufen Sie den Warenkorbinhalt für die neue Store-Ansicht ab.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Erwartete Ergebnisse</u>:

Die Antwort aus der neuen Store-Ansicht zeigt den Produktnamen aus der neuen Store-Ansicht an.

<u>Tatsächliche Ergebnisse</u>:

Die Antwort aus der neuen Store-Ansicht zeigt die Einrichtung des Produktnamen unter der standardmäßigen Store-Ansicht an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
