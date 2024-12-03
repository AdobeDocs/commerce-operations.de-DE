---
title: 'MDVA-41399: Zugriff auf den Warenkorb verwalten nicht möglich, wenn ein Kunde Produkte auf die Wunschliste setzt'
description: Der Patch MDVA-41399 behebt das Problem, dass Admin-Benutzer nicht auf die Seite "Warenkorb verwalten"zugreifen können, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-41399. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41399: Zugriff auf den Warenkorb verwalten nicht möglich, wenn ein Kunde Produkte auf die Wunschliste setzt

Der Patch MDVA-41399 behebt das Problem, dass Admin-Benutzer nicht auf die Seite &quot;Warenkorb verwalten&quot;zugreifen können, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-41399. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Admin-Benutzer können nicht auf die Seite &quot;Warenkorb verwalten&quot;zugreifen, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt.

<u>Voraussetzungen</u>:

1. Erstellen Sie zwei oder mehr Produkte.
1. Erstellen Sie einen Kunden.
1. Aktivieren Sie den Entwicklermodus.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zur Storefront und melden Sie sich als Kunde unter den Voraussetzungen an.
1. Fügen Sie ein Produkt zur Wunschliste hinzu.
1. Navigieren Sie zum Admin-Bedienfeld, navigieren Sie zur erstellten Seite zur Kundenbearbeitung und klicken Sie auf die Schaltfläche **Warenkorb verwalten** .

<u>Erwartete Ergebnisse</u>:

Der Admin-Benutzer kann den Warenkorb verwalten.

<u>Tatsächliche Ergebnisse</u>:

Der Admin-Benutzer erhält eine Fehlermeldung: *Es ist ein Fehler aufgetreten. Weitere Informationen finden Sie unter Fehlerprotokoll .*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
