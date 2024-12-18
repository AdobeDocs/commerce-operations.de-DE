---
title: 'ACSD-61103: Fehleranzahl wird nach erfolgreicher Kundenanmeldung über die API nicht auf null zurückgesetzt'
description: Wenden Sie den Patch ACSD-61103 an, um das Adobe Commerce-Problem zu beheben, bei dem die Fehleranzahl in der Tabelle „customer_entity“ nicht auf null zurückgesetzt wird, nachdem sich ein Kunde erfolgreich über API-Endpunkte angemeldet hat.
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
source-git-commit: acb5ff9656d7391de1e9b936909ce5a8a73d5d67
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61103: Fehleranzahl wird nach erfolgreicher Kundenanmeldung über die API nicht auf null zurückgesetzt

Mit dem Patch ACSD-61103 wird das Problem behoben, dass die Fehleranzahl in der `customer_entity`-Tabelle nicht auf null zurückgesetzt wird, nachdem sich eine Kundin oder ein Kunde erfolgreich über API-Endpunkte angemeldet hat. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61103. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Fehleranzahl in der `customer_entity`-Tabelle wird auch dann nicht auf null zurückgesetzt, wenn sich ein Kunde erfolgreich über API-Endpunkte anmeldet.

<u>Schritte zur Reproduktion</u>:

1. Kundenkonto erstellen.
1. Generieren Sie über die API ein Kunden-Token mit falschen Details.
1. Überprüfen Sie die Spalte `failures_num` in der Tabelle `customer_entity` DB für den oben genannten Kunden.
1. Generieren Sie ein Kunden-Token über die API mit den richtigen Details.
1. Überprüfen Sie die Spalte `failures_num` in der Tabelle `customer_entity` DB für den oben genannten Kunden.

<u>Erwartete Ergebnisse</u>:

Die Spalte `failures_num` sollte auf 0 zurückgesetzt werden, nachdem die richtigen Anmeldeinformationen verwendet wurden, um ein Kunden-Token über die API zu generieren.

<u>Tatsächliche Ergebnisse</u>:

Die Spalte `failures_num` wird nicht auf 0 zurückgesetzt, nachdem die richtigen Anmeldeinformationen verwendet wurden, um ein Kunden-Token über die API zu generieren.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
