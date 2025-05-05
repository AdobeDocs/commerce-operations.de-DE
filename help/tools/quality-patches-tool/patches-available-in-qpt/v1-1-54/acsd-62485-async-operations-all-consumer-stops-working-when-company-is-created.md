---
title: 'ACSD-62485: Verbraucher „async.operations.all“ funktioniert nicht mehr, wenn ein Unternehmen erstellt wird'
description: Wenden Sie den Patch ACSD-62485 an, um das Adobe Commerce-Problem zu beheben, bei dem der Verbraucher „async.operations.all“ nicht mehr funktioniert, wenn ein B2B-Unternehmen erstellt wird.
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
source-git-commit: 9d0925ae06c3ccf9ed6b2d89cec07f8f5fe2f94f
workflow-type: tm+mt
source-wordcount: '315'
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

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u>Erwartete Ergebnisse</u>:

Der Verbraucher verarbeitet 20.000 Nachrichten und endet erfolgreich.

<u>Tatsächliche Ergebnisse</u>:

Der Verbraucher funktioniert nach der Ausführung nicht mehr sofort.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
