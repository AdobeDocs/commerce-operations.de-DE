---
title: 'MDVA-38852: Kataloginventar sperrt Tabellen, was die Leistung verringert'
description: Der MDVA-38852 Patch löst das Problem, dass die Kataloginventartabellen für Aktualisierungen gesperrt sind, was die Leistung bei mehreren parallelen Bestellungen erheblich verringert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38852. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.
feature: Catalog Management, Inventory, Orders
role: Admin
exl-id: ce93130b-8d96-47b8-96c6-da5988b34ae0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-38852: Kataloginventar sperrt Tabellen, was die Leistung verringert

Der MDVA-38852 Patch löst das Problem, dass die Kataloginventartabellen für Aktualisierungen gesperrt sind, was die Leistung bei mehreren parallelen Bestellungen erheblich verringert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-38852. Beachten Sie, dass das Problem in Adobe Commerce 2.3.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Katalogbestand sperrt Tabellen für Aktualisierungen, was die Leistung in Fällen, in denen mehrere parallele Bestellungen aufgegeben werden, erheblich verringert.

<u>Schritte zur Reproduktion</u>:

1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Fahren Sie mit der Kasse fort und versuchen Sie, eine Bestellung aufzugeben.

<u>Erwartete Ergebnisse</u>:

* Es gibt keine Deadlocks.
* Die Leistung wird nicht verringert, wenn mehrere parallele Bestellungen aufgegeben werden.

<u>Tatsächliche Ergebnisse</u>:

* Eine Bestellung aufzugeben ist extrem langsam, wenn mehrere gleichzeitige Benutzer vorhanden sind.
* Es treten Deadlock-Fehler auf, die wie folgt aussehen:

```SQL
"SQLSTATE[40001]: Serialization failure: 1213 Deadlock found when trying to get lock; try restarting transaction, query was:
INSERT INTO `quote_payment` (`quote_id`, `method`, `additional_information`) VALUES (?, ?, ?)"
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md)-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch [!DNL Quality Patches Tool] Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
