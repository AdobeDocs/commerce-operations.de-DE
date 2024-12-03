---
title: 'ACSD-62485: `async.operations.all` consumer stop working when company is created'
description: Wenden Sie den Patch ACSD-62485 an, um das Adobe Commerce-Problem zu beheben, bei dem der Verbraucher "async.operations.all"nicht mehr funktioniert, wenn ein B2B-Unternehmen erstellt wird.
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
source-git-commit: 9d0925ae06c3ccf9ed6b2d89cec07f8f5fe2f94f
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485: `async.operations.all` Consumer funktioniert nicht mehr, wenn ein Unternehmen erstellt wird

Der Patch ACSD-62485 behebt das Problem, dass der `async.operations.all` -Verbraucher bei der Erstellung eines B2B-Unternehmens nicht mehr funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 installiert ist. Die Patch-ID ist ACSD-62485. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p7

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der `async.operations.all` -Verbraucher stoppt die Verarbeitung von Nachrichten, wenn ein B2B-Unternehmen asynchron erstellt wird, während der Verbraucher noch ausgeführt wird.

<u>Voraussetzungen</u>:

B2B-Module werden installiert und aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Kunden.
1. Senden Sie eine REST-Massenanfrage, um zwei Unternehmen zu erstellen und die erstellten Kunden als Unternehmensadministratoren zuzuweisen.
1. Starten Sie den Verbraucher mit dem folgenden Befehl:

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u>Erwartete Ergebnisse</u>:

Der Verbraucher verarbeitet 20.000 Nachrichten und endet erfolgreich.

<u>Tatsächliche Ergebnisse</u>:

Der Verbraucher funktioniert bei der Ausführung nicht mehr sofort.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
