---
title: 'ACSD-66865: Durch Speichern eines [!UICONTROL Catalog Price Rule] werden Indexer ungültig gemacht. Dies bietet eine Alternative zur Neuindizierung nur betroffener Produkte'
description: Wenden Sie den ACSD-66865 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem  Durch Speichern eines [!UICONTROL Catalog Price Rules] werden Indexer ungültig und eine Alternative zur Neuindizierung nur betroffener Produkte bereitgestellt.
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-66865: Durch Speichern eines **[!UICONTROL Catalog Price Rule]** werden Indexer ungültig gemacht. Dies bietet eine Alternative zur Neuindizierung nur betroffener Produkte

Mit dem Patch ACSD-66865 wird das Problem behoben, dass beim Speichern eines **[!UICONTROL Catalog Price Rule]** Indexer ungültig gemacht werden und eine Alternative zur Neuindizierung nur betroffener Produkte bereitgestellt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-66865. Beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Speichern eines **[!UICONTROL Catalog Price Rule]** werden alle Indexer ungültig gemacht. Dadurch werden vollständige Neuindizierungen ausgelöst, anstatt nur die betroffenen Produkte neu zu indizieren.

<u>Schritte zur Reproduktion</u>:

1. Stellen Sie sicher, dass cron nicht ausgeführt wird und alle Indexer so eingestellt sind, dass sie planmäßig aktualisiert werden (mit Ausnahme von `customer_grid`, die beim Speichern aktualisiert werden können).
2. Führen Sie eine vollständige manuelle Neuindizierung mit dem folgenden Befehl aus: `php bin/magento indexer:reindex`.
3. Überprüfen Sie, ob alle Indizes *[!UICONTROL Ready]* mit *0* Elementen im Rückstand anzeigen.
4. Navigieren Sie in der Seitenleiste Admin zu **[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]**. Erstellen Sie eine aktive Katalogpreisregel für ein einzelnes Produkt (z. B. mit einer *SKU*-Bedingung).
5. Führen Sie den Befehl `php bin/magento indexer:status` aus, um den Indexerstatus zu überprüfen.
6. Beachten Sie, dass mehrere Indizes als **[!UICONTROL Reindex Required]** markiert sind, obwohl nur ein Produkt betroffen ist.

<u>Erwartete Ergebnisse</u>:

Es werden nur die betroffenen Produktdaten identifiziert, und anstelle einer vollständigen Neuindizierung über alle Indexer hinweg wird eine partielle Neuindizierung ausgelöst.

<u>Tatsächliche Ergebnisse</u>:

Für alle Indexer wird eine vollständige Neuindizierung ausgelöst, auch wenn nur ein einziges Produkt von der **[!UICONTROL Catalog Price Rule]** betroffen ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
