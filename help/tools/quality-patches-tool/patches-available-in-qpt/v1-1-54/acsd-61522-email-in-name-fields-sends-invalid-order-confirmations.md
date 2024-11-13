---
title: "ACSD-61522: E-Mail-Adressen in den Feldern *Vorname und Nachname* senden ungültige Bestellbestätigungen."
description: Wenden Sie den Patch ACSD-61522 an, um das Adobe Commerce-Problem zu beheben, bei dem E-Mail-Adressen in die Felder *[!UICONTROL First Name]* und *[!UICONTROL Last Name]* eines Gastkunden eingegeben werden können, was dazu führt, dass ungültige E-Mails zur Bestellbestätigung gesendet werden.
feature: Checkout, Customers
role: Admin, Developer
source-git-commit: d56f4fda007c1499bdba82ac3db9ac5ea1d34b0e
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# ACSD-61522: E-Mail-Adressen in den Feldern *Vorname und Nachname* senden ungültige Bestellbestätigungen

Der Patch ACSD-61522 behebt das Problem, dass es möglich ist, E-Mail-Adressen in die Felder *[!UICONTROL First Name]* und *[!UICONTROL Last Name]* eines Gastkunden einzugeben, was dazu führt, dass ungültige E-Mails zur Bestellbestätigung gesendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61522. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p9

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das System ermöglicht die Eingabe von E-Mail-Adressen in die Felder *[!UICONTROL First Name]* und *[!UICONTROL Last Name]* eines Gastkunden, was zum Senden ungültiger E-Mails zur Bestellbestätigung führt.

<u>Zu reproduzierende Schritte</u>:

1. Fügen Sie beliebige Produkte als Gastkunden zum Warenkorb hinzu.
1. Wechseln Sie zu &quot;**[!UICONTROL Checkout]**&quot;.
1. Füllen Sie das Feld *[!UICONTROL Email Address]* mit *test1@example.com* aus.
1. Füllen Sie das Feld *[!UICONTROL First Name]* mit *<test2@example.com>* aus.
1. Füllen Sie *[!UICONTROL Last Name]* mit *<test3@example.com>*.
1. Füllen Sie andere erforderliche Felder aus.
1. Platzieren Sie die Bestellung.

<u>Erwartete Ergebnisse</u>:

E-Mail-Adressen können nicht in den Feldern *[!UICONTROL First Name]* und *[!UICONTROL Last Name]* verwendet werden.

<u>Tatsächliche Ergebnisse</u>:

1. Die Bestellung wird aufgegeben.
1. Die Felder *[!UICONTROL First Name]* und *[!UICONTROL Last Name]* werden wie eingegeben gespeichert.
1. An alle drei E-Mails werden Bestellbestätigungs-E-Mails gesendet.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
