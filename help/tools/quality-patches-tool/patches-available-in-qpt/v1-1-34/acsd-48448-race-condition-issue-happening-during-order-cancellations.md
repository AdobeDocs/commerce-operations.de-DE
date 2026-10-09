---
title: 'ACSD-48448: Race-Condition-Problem bei Auftragsstornierungen, das zu doppelten Einträgen in der Inventory_Reservation-Tabelle führt'
description: Wenden Sie den Patch ACSD-48448 an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem das Problem mit den Race-Bedingungen während der Stornierungen der Bestellung auftritt, was zu doppelten Einträgen in der Tabelle inventory_reservation führt.
feature: Orders, Checkout
role: Admin
exl-id: c1905b60-4607-454c-975b-77b0056661ad
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%
---
# ACSD-48448: *[!UICONTROL Race]* Problem mit einer Bedingung bei Stornierungen von Bestellungen, was zu einer doppelten Eingabe in `inventory_reservation` Tabelle führt

Mit dem Patch ACSD-48448 wird das Problem behoben, dass bei Auftragsstornierungen ein *[!UICONTROL Race]* auftritt, was zu doppelten Einträgen in der `inventory_reservation` führt. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.34 installiert ist. Die Patch-ID ist ACSD-48448. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2 und 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

*[!UICONTROL Race]* Problem mit Bedingungen tritt bei Stornierungen von Bestellungen auf, was zu doppelten Einträgen in der `inventory_reservation` führt.

<u>Schritte zur Reproduktion</u>:

1. Bestellung aufgeben.
1. Überprüfen Sie die `inventory_reservation`, um sicherzustellen, dass ein Datensatz für das `order_placed` Ereignis vorhanden ist.
1. Führen Sie das angehängte Skript aus, um die Bestellung parallel abzubrechen (denken Sie daran, die URL und orderID zu ändern).

`bash cancel_order.sh`

```shell
#!/bin/bash
baseUrl=" "
orderId=3
token=$(curl --location --request POST "${baseUrl}rest/V1/integration/admin/token" \
 -H 'Content-Type: application/json' \
 -d '{
  "username": "admin",
  "password": "password"
}')
echo ${token//\"/}
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
 &
sleep 0.1;
curl --location --request POST "${baseUrl}/rest/V1/orders/${orderId}/cancel" \
 -H "Authorization:Bearer ${token//\"/}" \
 -H 'Content-Type: application/json' \
wait
```

<u>Erwartete Ergebnisse</u>:

Einträge werden nicht dupliziert.

<u>Tatsächliche Ergebnisse</u>:

In der `inventory_reservation`-Tabelle werden doppelte Einträge für die `order_canceled` erstellt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
