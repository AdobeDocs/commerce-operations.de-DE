---
title: "ACSD-52929: Redundante Anfrage zur Neuindizierung von Standardquellelementen"
description: Wenden Sie den Patch ACSD-52929 an, um das Adobe Commerce-Problem zu beheben, bei dem eine redundante Anfrage zur Neuindizierung der Standardquellelemente vorliegt, wenn der Inventarindexer im asynchronen Modus konfiguriert ist.
feature: Configuration, Inventory
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-52929: Redundante Anfrage zum Neuindizieren von Standardquellelementen

Der Patch ACSD-52929 behebt das Problem, bei dem Anforderungen an die Neuindizierung von Standardquellelementen Redundanz aufweisen, wenn der Inventarindexer im asynchronen Modus konfiguriert ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.38 installiert ist. Die Patch-ID ist ACSD-52929. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Es gibt eine Redundanz von Anforderungen zur Neuindizierung von Standardquellelementen, wenn der Inventarindexer im asynchronen Modus konfiguriert ist.

<u>Zu reproduzierende Schritte</u>:

1. Konfigurieren Sie [!DNL RabbitMQ].
1. Aktivieren Sie die asynchrone Neuindizierungsstrategie, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** gehen und **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]** festlegen.
1. Erstellen Sie eine benutzerdefinierte Inventarquelle.
1. Melden Sie sich im Dashboard [!DNL RabbitMQ] an und wechseln Sie zur Registerkarte &quot;Warteschlangen&quot;.
1. Überprüfen Sie die `inventory.indexer.sourceItem` -Warteschlange und stellen Sie sicher, dass sie keine Meldungen enthält.
1. Öffnen Sie ein einfaches Produkt aus dem Backend, fügen Sie *[!UICONTROL stock only]* zur benutzerdefinierten Quelle hinzu und speichern Sie das Produkt.
1. Laden Sie die `inventory.indexer.sourceItem` -Warteschlange in das Dashboard [!DNL RabbitMQ] und überprüfen Sie dann die Nachrichten.

<u>Erwartete Ergebnisse</u>:

Es ist nur eine Nachricht in der Warteschlange für die benutzerdefinierte Quelle vorhanden.

<u>Tatsächliche Ergebnisse</u>:

In der Warteschlange werden zwei Nachrichten angezeigt: eine für die Standardquelle und die andere für die benutzerdefinierte Quelle.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
