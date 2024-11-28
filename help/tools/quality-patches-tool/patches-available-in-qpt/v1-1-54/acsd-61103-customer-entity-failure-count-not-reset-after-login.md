---
title: 'ACSD-61103: Fehleranzahl wird nach erfolgreicher Kundenanmeldung über die API nicht auf null zurückgesetzt.'
description: Wenden Sie den Patch ACSD-61103 an, um das Adobe Commerce-Problem zu beheben, bei dem die Fehleranzahl in der Tabelle "customer_entity"nicht auf null zurückgesetzt wird, nachdem sich ein Kunde erfolgreich über API-Endpunkte angemeldet hat.
feature: GraphQL, REST, Customers
role: Admin, Developer
source-git-commit: d53b747c3b2021e842647de5371a5f0f2a760f09
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-61103: Fehleranzahl wird nach erfolgreicher Kundenanmeldung über die API nicht auf null zurückgesetzt

Der Patch ACSD-61103 behebt das Problem, dass die Fehleranzahl in der Tabelle `customer_entity` nicht auf null zurückgesetzt wird, nachdem sich ein Kunde erfolgreich über API-Endpunkte angemeldet hat. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-61103. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p8

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Fehleranzahl in der Tabelle `customer_entity` wird nicht auf null zurückgesetzt, selbst wenn sich ein Kunde erfolgreich über API-Endpunkte anmeldet.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Kundenkonto.
1. Generieren Sie ein Kunden-Token über API mit falschen Details.
1. Überprüfen Sie die Spalte `failures_num` in der Tabelle `customer_entity` DB für den obigen Kunden.
1. Generieren Sie ein Kunden-Token über die API mit den richtigen Details.
1. Überprüfen Sie die Spalte `failures_num` in der Tabelle `customer_entity` DB für den obigen Kunden.

<u>Erwartete Ergebnisse</u>:

Die Spalte `failures_num` sollte auf 0 zurückgesetzt werden, nachdem die richtigen Anmeldeinformationen zum Generieren eines Kunden-Tokens über die API verwendet wurden.

<u>Tatsächliche Ergebnisse</u>:

Die Spalte &quot;`failures_num`&quot; wird nicht auf 0 zurückgesetzt, nachdem die richtigen Anmeldeinformationen zum Generieren eines Kunden-Tokens über die API verwendet wurden.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.

