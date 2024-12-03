---
title: 'MDVA-43102: Verkaufsmenge nicht korrekt aktualisiert'
description: Der Patch MDVA-43102 behebt das Problem, dass die Verkaufsmenge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43102. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.
feature: Variables
role: Admin
exl-id: 6a10f586-bbde-4252-9b8e-9b2b712f0fb3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-43102: Verkaufsmenge nicht korrekt aktualisiert

Der Patch MDVA-43102 behebt das Problem, dass die Verkaufsmenge nicht korrekt aktualisiert wird, wenn eine Rückerstattung über die REST-API erfolgt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43102. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.5 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Verkaufsmenge wird nicht korrekt aktualisiert, wenn eine Rückerstattung mithilfe der REST-API erfolgt.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie dem Warenkorb einen Artikel hinzu.
1. Überprüfen Sie die Lagermenge und die Verkaufsmenge.
1. Erstellen Sie eine Bestellung.
1. Erstellen Sie bei Bedarf eine Rechnung.
1. Senden Sie eine REST-Anfrage zur Rückerstattung der Rechnung mit der folgenden Payload:

   * Offline-Methode/Bestellung/`<order_id>`/Rückgabe
   * Online-Methode/Rechnung/`<invoice_id>`/Erstattung

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. Versenden Sie die Artikel nicht.
1. Vergleichen Sie die Lagermenge und die Salable Qty von vorher. Beide sollten um denselben Betrag aktualisiert werden.

<u>Erwartete Ergebnisse</u>:

Die Verkaufsmenge wird korrekt aktualisiert, wenn eine Rückerstattung vor dem Versand der Bestellung erteilt wird und das Produkt wieder auf den Lager zurückgegeben wird.

<u>Tatsächliche Ergebnisse</u>:

Die Verkaufsmenge wird nicht aktualisiert, wenn eine Rückerstattung vor dem Versand der Bestellung erteilt wird, und das Produkt wird an den Lager zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
