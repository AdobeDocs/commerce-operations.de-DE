---
title: 'ACSD-61522: E-Mail-Adressen in den Feldern *Vor- und Nachname* senden ungültige Bestellbestätigungen'
description: Wenden Sie den Patch ACSD-61522 an, um das Adobe Commerce-Problem zu beheben, bei dem es möglich ist, E-Mail-Adressen in die Felder *[!UICONTROL First Name]* und *[!UICONTROL Last Name]* eines Gastkunden einzugeben, was dazu führt, dass ungültige E-Mails zur Bestellbestätigung gesendet werden.
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-61522: E-Mail-Adressen in *Feldern „Vor- und*&quot; senden ungültige Bestellbestätigungen

Mit dem Patch ACSD-61522 wird das Problem behoben, dass E-Mail-Adressen in die *[!UICONTROL First Name]*- und *[!UICONTROL Last Name]*-Felder eines Gastkunden eingegeben werden können, was dazu führt, dass ungültige E-Mails zur Bestellbestätigung gesendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61522. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p9

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das System ermöglicht die Eingabe von E-Mail-Adressen in die *[!UICONTROL First Name]*- und *[!UICONTROL Last Name]* eines Gastkunden, was zum Versand von ungültigen E-Mails zur Bestellbestätigung führt.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie ein beliebiges Produkt als Gastkunde zum Warenkorb hinzu.
1. Gehe zu **[!UICONTROL Checkout]**.
1. Füllen Sie das *[!UICONTROL Email Address]* Feld mit *test1@example.com* aus.
1. Füllen Sie das *[!UICONTROL First Name]* Feld mit *<test2@example.com>* aus.
1. *[!UICONTROL Last Name]* mit *<test3@example.com>* füllen.
1. Füllen Sie andere erforderliche Felder aus.
1. Bestellung aufgeben.

<u>Erwartete Ergebnisse</u>:

Es ist nicht möglich, E-Mail-Adressen in den Feldern *[!UICONTROL First Name]* und *[!UICONTROL Last Name]* zu verwenden.

<u>Tatsächliche Ergebnisse</u>:

1. Die Bestellung wird aufgegeben.
1. *[!UICONTROL First Name]* und *[!UICONTROL Last Name]* Felder werden wie eingegeben gespeichert.
1. E-Mails zur Bestellbestätigung werden an alle drei E-Mails gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
