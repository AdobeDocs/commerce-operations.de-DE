---
title: 'ACSD-51845: Nachfolgende Produkte können nicht mit Stufenpreisen und verschiedenen Attributsätzen über asynch bulk aktualisiert werden [!DNL API]'
description: Wenden Sie den Patch ACSD-51845 an, um das Adobe Commerce-Problem zu beheben, bei dem Sie nachfolgende Produkte nicht mit Stufenpreisen und verschiedenen Attributsätzen über asynchrones Bulk aktualisieren können [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: 83d97946-83da-4c1b-8f2a-21a64ee84e93
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-51845: Nachfolgende Produkte können nicht mit Stufenpreisen und verschiedenen Attributsätzen über asynchrone Stapel aktualisiert werden [!DNL API]

Der Patch ACSD-51845 behebt das Problem, dass Sie nachfolgende Produkte nicht mit Stufenpreisen und verschiedenen Attributsätzen über asynchrones Massen [!DNL REST API] aktualisieren können. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-51845. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Aktualisierung schlägt für nachfolgende Produkte mit Stufenpreisen und verschiedenen Attributsätzen über asynchronen Stapel [!DNL REST API] fehl.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie [!DNL RabbitMQ].
1. Erstellen Sie zwei Attributsätze.
1. Erstellen Sie zwei **einfache Produkte**, indem Sie jedes Produkt einem anderen Attributsatz zuweisen.
1. Fügen Sie für jedes Produkt einen **Kundengruppenpreis** hinzu.
1. Aktualisieren Sie beide Produkte im selben Batch-Update [!DNL API] .
1. Stellen Sie sicher, dass der Befehl `bin/magento queue:consumers:start async.operations.all` ausgeführt wird.
1. Überprüfen Sie den Bulk-Status [!DNL API] .

<u>Erwartete Ergebnisse</u>:

Die Ausführung des Dienstes ist erfolgreich.

<u>Tatsächliche Ergebnisse</u>:

Das System gibt die Fehlermeldung zurück: *Das Produkt konnte nicht gespeichert werden. Versuchen Sie es erneut.*

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
