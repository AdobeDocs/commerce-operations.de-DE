---
title: 'ACSD-45424: Falsche Reservierungsentschädigung nach teilweiser Rückerstattung'
description: Der Patch ACSD-45424 behebt das Problem, dass nach einer teilweisen Rückerstattung eine falsche Reservierungsentschädigung entsteht. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-45424. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.
feature: Orders
role: Admin
exl-id: 94435816-9f4a-40f9-be80-05836ed7781f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424: Falsche Reservierungsentschädigung nach teilweiser Rückerstattung

Der Patch ACSD-45424 behebt das Problem, dass nach einer teilweisen Rückerstattung eine falsche Reservierungsentschädigung entsteht. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID lautet ACSD-45424. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach einer teilweisen Rückerstattung wird eine falsche Reservierungsentschädigung erstellt.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie die Versandmethode für den In-Store-Versand.
1. Erstellen Sie drei Inventarquellen und stellen Sie sicher, dass der Erfassungsort in jedem (Quelle1, Quelle2, Quelle3) aktiv ist.
1. Erstellen Sie ein neues Lager und weisen Sie dem neuen Lager die drei Quellen zu.
   * Dieser Bestand sollte der Haupt-Website zugewiesen werden.
1. Erstellen Sie ein einfaches Produkt, P3, und weisen Sie ihm alle Quellen zu.
1. Fügen Sie die folgenden Mengen für die Quellen des einfachen Produkts hinzu und aktivieren Sie Backorder:
   * Standardquelle - 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. Fügen Sie das einfache Produkt vom Frontend zum Warenkorb hinzu und fahren Sie mit dem Versandformular fort.
1. Wählen Sie &quot;source1&quot;als Versandort aus.
1. Führen Sie die Bestellung aus und führen Sie die folgende Abfrage in der Datenbank aus:

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   Sie erhalten den aufgegebenen Bestelldatensatz in der Tabelle `inventory_reservation`. Die Menge ist 10, was richtig ist.
1. Invotieren Sie diese Bestellung vom Backend aus.
1. Erstellen Sie nun ein Kreditmemo für nur ein Produkt. Aktivieren Sie NICHT das Kontrollkästchen *Zurück auf Lager* .
1. Führen Sie dieselbe Abfrage aus Schritt 8 aus.

<u>Erwartete Ergebnisse</u>:

Wenn Sie die *Zurück auf Lager* während der Erstellung des Kreditmemos nicht ausgewählt haben, enthält die Tabelle `inventory_reservation` keinen Datensatz, der dem Kreditmemo entspricht.

<u>Tatsächliche Ergebnisse</u>:

Auch wenn Sie während der Erstellung des Credit Memos die Option *Zurück auf Lager* nicht ausgewählt haben, wird der Tabelle `inventory_reservation` ein Datensatz mit dem Ereignistyp `creditmemo_created` hinzugefügt. Außerdem hat der in der Tabelle `inventory_reservation` hinzugefügte Credit Memo-Datensatz eine Menge von 10, obwohl Sie das Credit Memo für nur eine Menge erstellt haben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
