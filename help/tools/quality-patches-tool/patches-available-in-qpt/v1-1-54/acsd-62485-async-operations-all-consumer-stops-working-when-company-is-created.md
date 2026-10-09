---
title: 'ACSD-62485: Verbraucher „async.operations.all“ funktioniert nicht mehr, wenn ein Unternehmen erstellt wird'
description: Wenden Sie den Patch ACSD-62485 an, um das Adobe Commerce-Problem zu beheben, bei dem der Verbraucher „async.operations.all“ nicht mehr funktioniert, wenn ein B2B-Unternehmen erstellt wird.
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '334'
ht-degree: 0%
---
# ACSD-62485: `async.operations.all` Verbraucher funktioniert nicht mehr, wenn ein Unternehmen erstellt wird

Mit dem Patch ACSD-62485 wird das Problem behoben, dass der `async.operations.all` Consumer nicht mehr funktioniert, wenn ein B2B-Unternehmen erstellt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-62485. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der `async.operations.all` Consumer stoppt die Verarbeitung von Nachrichten, wenn ein B2B-Unternehmen asynchron erstellt wird, während der Consumer noch ausgeführt wird.

<u>Voraussetzungen</u>:

B2B-Module sind installiert und aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Kunden.
1. Senden Sie eine REST-Massenanfrage, um zwei Unternehmen zu erstellen, wobei die erstellten Kunden als Unternehmensadministratoren zugewiesen werden.
1. Starten Sie den -Verbraucher mit dem folgenden Befehl:

   `bin/magento queue:consumer:start async.operations.all --max-messages=20000`

<u>Erwartete Ergebnisse</u>:

Der Verbraucher verarbeitet 20.000 Nachrichten und endet erfolgreich.

<u>Tatsächliche Ergebnisse</u>:

Der Verbraucher funktioniert nach der Ausführung nicht mehr sofort.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
