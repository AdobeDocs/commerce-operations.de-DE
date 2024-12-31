---
title: 'ACSD-52929: Redundante Anfrage zur Neuindizierung standardmäßiger Quellelemente'
description: Wenden Sie den ACSD-52929-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem eine redundante Anfrage zur Neuindizierung der standardmäßigen Quellelemente vorliegt, wenn der Inventar-Indexer im asynchronen Modus konfiguriert ist.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 904aed0e-a6cd-4a0f-949d-bb32fcd77356
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-52929: Redundante Anfrage zur Neuindizierung standardmäßiger Quellelemente

Mit dem Patch „ACSD-52929“ wird das Problem behoben, dass redundante Anfragen zur Neuindizierung von standardmäßigen Quellelementen auftreten, wenn der Inventarindexer im asynchronen Modus konfiguriert ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.38 installiert ist. Die Patch-ID ist ACSD-52929. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es gibt eine Redundanz von Anfragen zur Neuindizierung von standardmäßigen Quellelementen, wenn der Inventarindizierer im asynchronen Modus konfiguriert ist.

<u>Schritte zur Reproduktion</u>:

1. Konfigurieren Sie [!DNL RabbitMQ].
1. Aktivieren Sie die asynchrone Neuindizierungsstrategie, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** wechseln und **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]** festlegen.
1. Erstellen Sie eine benutzerdefinierte Inventarquelle.
1. Melden Sie sich beim [!DNL RabbitMQ]-Dashboard an und wechseln Sie zur Registerkarte Warteschlangen .
1. Überprüfen Sie `inventory.indexer.sourceItem` Warteschlange und stellen Sie sicher, dass sie keine Nachrichten enthält.
1. Öffnen Sie ein einfaches Produkt aus dem Backend, fügen Sie *[!UICONTROL stock only]* zur benutzerdefinierten Quelle hinzu und speichern Sie das Produkt.
1. Laden Sie die `inventory.indexer.sourceItem` Warteschlange im [!DNL RabbitMQ] Dashboard und überprüfen Sie dann die Nachrichten.

<u>Erwartete Ergebnisse</u>:

Für die benutzerdefinierte Quelle befindet sich in der Warteschlange nur eine Nachricht.

<u>Tatsächliche Ergebnisse</u>:

In der Warteschlange werden zwei Meldungen angezeigt: eine für die Standardquelle und die andere für die benutzerdefinierte Quelle.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
