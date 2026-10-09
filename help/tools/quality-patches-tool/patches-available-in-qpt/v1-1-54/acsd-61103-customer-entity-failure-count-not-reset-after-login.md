---
title: 'ACSD-61103: Fehleranzahl wird nach erfolgreicher Kundenanmeldung über die API nicht auf null zurückgesetzt'
description: Wenden Sie den Patch ACSD-61103 an, um das Adobe Commerce-Problem zu beheben, bei dem die Fehleranzahl in der Tabelle „customer_entity“ nicht auf null zurückgesetzt wird, nachdem sich ein Kunde erfolgreich über API-Endpunkte angemeldet hat.
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '398'
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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
