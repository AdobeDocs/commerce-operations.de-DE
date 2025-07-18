---
title: 'ACSD-66212: Beim zweimaligen Importieren einer CSV-Datei des Kunden traten bei zweiten und nachfolgenden Versuchen Fehler auf'
description: Wenden Sie den Patch ACSD-66212 an, um das Adobe Commerce-Problem zu beheben, bei dem der Import einer CSV-Kundendatei beim zweiten und nachfolgenden Versuch zweimal zu Fehlern führte.
feature: Data Import/Export, Customers
role: Admin, Developer
source-git-commit: 97a5979a189e43b737c44cfe7a65025effae711c
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# ACSD-66212: Beim zweimaligen Importieren einer CSV-Datei des Kunden traten bei zweiten und nachfolgenden Versuchen Fehler auf

Mit dem Patch „ACSD-66212“ wird das Problem behoben, dass der doppelte Import einer CSV-Datei des Kunden beim zweiten und nachfolgenden Versuch zu Fehlern führte. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 installiert ist. Die Patch-ID ist ACSD-66212. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Import einer CSV-Datei eines Kunden führte zweimal zu Fehlern beim zweiten und nachfolgenden Versuchen.

<u>Schritte zur Reproduktion</u>:

Importieren Sie eine CSV-Datei, die Kundendaten einschließlich des Kundenstatus enthält.

<u>Erwartete Ergebnisse</u>:

Der Status wird korrekt importiert und exportiert.

<u>Tatsächliche Ergebnisse</u>:

Beim Import tritt ein Fehler auf:

```
General system exception happened
Additional data: <div class="messages"><div class="message message-error error"><div data-ui-id="messages-message-error" >SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near " at line 1, query was: INSERT INTO company_advanced_customer_entity (customer_id*) VALUES </div></div></div>
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
