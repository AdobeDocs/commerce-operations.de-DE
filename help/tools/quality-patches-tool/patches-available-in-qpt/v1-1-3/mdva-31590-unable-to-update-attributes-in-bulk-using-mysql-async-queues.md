---
title: 'MDVA-31590: Attribute können nicht stapelweise über asynchrone MySQL-Warteschlangen aktualisiert werden'
description: Der Patch MDVA-31590 löst das Problem, dass die Benutzer Attribute nicht stapelweise über asynchrone MySQL-Warteschlangen aktualisieren können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-31590. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
feature: Attributes, Services
role: Admin
exl-id: f8d1c3bd-e995-41ef-89e1-93eec6e8b1f1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-31590: Attribute können nicht stapelweise über asynchrone MySQL-Warteschlangen aktualisiert werden

Der Patch MDVA-31590 löst das Problem, dass die Benutzer Attribute nicht stapelweise über asynchrone MySQL-Warteschlangen aktualisieren können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-31590. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Benutzer können Attribute nicht stapelweise mithilfe von MySQL asynchron aktualisieren.

<u>Schritte zur Reproduktion</u>:

1. Führen Sie im Produktraster im Backend eine Massenaktion durch, um Attributwerte für einige Produkte zu aktualisieren.
   * Markieren Sie Produkte und wählen **Attribute aktualisieren** aus dem Dropdown-Menü Aktionen aus.
1. Legen Sie Werte für die erforderlichen Attribute fest und weisen Sie Produkte Websites zu und speichern Sie sie.
1. Nachdem die Seite neu geladen wurde, wird eine Meldung wie die folgende angezeigt:
   *Aufgabe „Attribute für N ausgewählte Produkte aktualisieren“: Für eine Aktualisierung wurde(n) 1 Element(e) geplant.*
1. Warten Sie einige Sekunden und laden Sie die Backend-Seite neu.

<u>Erwartete Ergebnisse</u>:

1. Auf der Seite wird eine Meldung über eine erfolgreiche Aktualisierung angezeigt wie: *1 Element(e) wurde(n) erfolgreich aktualisiert.*
1. Attributwerte für zugehörige Produkte werden aktualisiert.
1. In der DB werden neue Datensätze sowohl in `magento_bulk` Tabelle als auch in `magento_operation` Tabelle erstellt (Vorgänge im Zusammenhang mit der Massenverarbeitung).
1. Neue Datensätze werden in der `queue_message`-Tabelle erstellt (bezogen auf die Warteschlangen-`product_action_attribute.update` und/oder -`product_action_attribute.website.update`).
1. `queue_message_status` Tabelle enthält Datensätze mit Status „4“.
1. Es gibt KEINE Fehler in `system.log`.

<u>Tatsächliche Ergebnisse</u>:

1. Auf der Seite wird weiterhin eine Meldung wie die folgende angezeigt:
   *Aufgabe „Attribute für N ausgewählte Produkte aktualisieren“: Für eine Aktualisierung wurde(n) 1 Element(e) geplant.*
1. Attributwerte für die Produkte werden aktualisiert.
1. In `message_bulk` Tabelle wird ein neuer Datensatz erstellt, es gibt jedoch keine verknüpften Datensätze in `magento_operation` Tabelle.
1. In `queue_message` und `queue_message_status` Tabellen werden neue Datensätze erstellt.
1. `queue_message_status` Tabelle enthält einen Datensatz mit Fehlerstatus (Statuswert „6„).
1. `system.log` enthält Fehler ähnlich dem folgenden:

   ```sql
   *main.CRITICAL: Message has been rejected: SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'operation_key' cannot be null, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?) [] []*
   ```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
