---
title: 'ACSD-45424: Fehlerhafter Buchungsausgleich nach teilweiser Rückerstattung'
description: Der Patch von ACSD-45424 behebt das Problem, dass nach einer teilweisen Rückerstattung eine falsche Reservierungskompensation erstellt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID ist ACSD-45424. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
feature: Orders
role: Admin
exl-id: 94435816-9f4a-40f9-be80-05836ed7781f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424: Fehlerhafter Buchungsausgleich nach teilweiser Rückerstattung

Der Patch von ACSD-45424 behebt das Problem, dass nach einer teilweisen Rückerstattung eine falsche Reservierungskompensation erstellt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID ist ACSD-45424. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nach einer teilweisen Rückerstattung wird ein falscher Buchungsausgleich erstellt.

<u>Schritte zur Reproduktion</u>:

1. Versandmethode für den Versand im Geschäft aktivieren.
1. Erstellen Sie drei Inventarquellen und stellen Sie sicher, dass der Abholort in jeder Quelle aktiv ist (Quelle1, Quelle2, Quelle3).
1. Erstellen Sie ein neues Lager und weisen Sie dem neuen Lager die drei Quellen zu.
   * Dieser Bestand sollte der Haupt-Website zugewiesen werden.
1. Erstellen Sie ein einfaches Produkt, P3, und weisen Sie ihm alle Quellen zu.
1. Fügen Sie die folgenden Mengen für die Quellen des einfachen Produkts hinzu und aktivieren Sie Nachbestellungen:
   * Standardquelle - 100
   * Quelle 1 - 0
   * Quelle2 - 10
   * Quelle3 - 0
1. Fügen Sie das einfache Produkt aus dem Frontend zum Warenkorb hinzu und fahren Sie mit dem Versandformular fort.
1. Wählen Sie als Versandort „source1“ aus.
1. Füllen Sie die Reihenfolge aus und führen Sie die folgende Abfrage in der Datenbank aus:

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   Der Datensatz für die Auftragserteilung wird in der `inventory_reservation` Tabelle angezeigt. Die Menge ist 10, was korrekt ist.
1. Diese Bestellung über das Backend fakturieren.
1. Erstellen Sie jetzt eine Gutschrift für nur ein Produkt. Aktivieren Sie NICHT das *Zurück an Lager*.
1. Führen Sie dieselbe Abfrage aus Schritt 8 aus.

<u>Erwartete Ergebnisse</u>:

Wenn Sie bei der Erstellung der Gutschrift nicht *Auf Lager zurückgeben* ausgewählt haben, verfügt die `inventory_reservation`-Tabelle über keinen Datensatz, der der Gutschrift entspricht.

<u>Tatsächliche Ergebnisse</u>:

Obwohl Sie bei der Erstellung der Gutschrift nicht die Option *Zurück an Lager* ausgewählt haben, wird `inventory_reservation` Tabelle mit `creditmemo_created` Ereignistyp ein Datensatz hinzugefügt. Außerdem hat der in der `inventory_reservation` hinzugefügte Gutschriftsdatensatz eine Menge von 10, obwohl Sie die Gutschrift nur für eine Menge erstellt haben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
