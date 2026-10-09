---
title: 'ACSD-53845: Problem mit dem MySQL-Verbindungs-Timeout, wenn Consumer max_messages = 0'
description: Wenden Sie den Patch ACSD-53845 an, um das Adobe Commerce-Problem zu beheben, bei dem die MySQL-Verbindung beim Verbraucher „max_messages = 0“ eine Zeitüberschreitung aufweist.
feature: REST, Configuration
role: Admin, Developer
exl-id: 437e29f4-b11a-466c-9928-3867821d2b8d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
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
source-wordcount: '353'
ht-degree: 0%
---
# ACSD-53845: Problem mit der MySQL-Verbindungs-Zeitüberschreitung beim `max_messages = 0` von Privatkunden

Mit dem Patch ACSD-53845 wird das Problem behoben, dass die MySQL-Verbindung beim `max_messages = 0` des Verbrauchers unterbrochen wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.42 installiert ist. Die Patch-ID ist ACSD-53845. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Timeout der MySQL-Verbindung beim `max_messages = 0`.

Die Verbindung zur Datenbank wird jedoch beim Starten einer Transaktion wiederhergestellt.

<u>Schritte zur Reproduktion</u>:

1. Senden Sie eine Anfrage an Massenaktualisierungsprodukte mithilfe des `async/bulk/V1/products` REST-API-Endpunkts.
1. Überprüfen Sie den Status in der `magento_operation`.

<u>Erwartete Ergebnisse</u>:

Die Produkte werden aktualisiert.

<u>Tatsächliche Ergebnisse</u>:

1. Es wird ein Fehler protokolliert:

   ```yaml
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. *status* für diesen Vorgang bleibt *4* in der `magento_operation`.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > &#x200B;](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
