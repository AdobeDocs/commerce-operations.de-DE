---
title: 'MDVA-31590: Attribute können nicht stapelweise mithilfe asynchroner MySQL-Warteschlangen aktualisiert werden'
description: Der Patch MDVA-31590 behebt das Problem, dass die Benutzer keine Attribute stapelweise mit asynchronen MySQL-Warteschlangen aktualisieren können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-31590. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
feature: Attributes, Services
role: Admin
exl-id: f8d1c3bd-e995-41ef-89e1-93eec6e8b1f1
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-31590: Attribute können nicht stapelweise mithilfe asynchroner MySQL-Warteschlangen aktualisiert werden

Der Patch MDVA-31590 behebt das Problem, dass die Benutzer keine Attribute stapelweise mit asynchronen MySQL-Warteschlangen aktualisieren können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-31590. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0-2.4.1-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzer können Attribute nicht stapelweise mit MySQL async aktualisieren.

<u>Zu reproduzierende Schritte</u>:

1. Führen Sie im Produktraster im Backend eine Massenaktion durch, um Attributwerte für einige Produkte zu aktualisieren.
   * Markieren Sie Produkte und wählen Sie **Attribute aktualisieren** aus der Dropdown-Liste Aktionen aus.
1. Legen Sie Werte für die erforderlichen Attribute fest, weisen Sie den Websites Produkte zu und speichern Sie sie.
1. Sobald die Seite neu geladen wird, wird eine Meldung wie die folgende angezeigt:
   *Aufgabe &quot;Attribute für N ausgewählte Produkte aktualisieren&quot;: 1 Element(e) wurde für eine Aktualisierung geplant.*
1. Warten Sie einige Sekunden und laden Sie die Backend-Seite neu.

<u>Erwartete Ergebnisse</u>:

1. Die Seite zeigt eine erfolgreiche Aktualisierungsmeldung an, z. B.: *1 Elemente wurden erfolgreich aktualisiert.*
1. Attributwerte für verwandte Produkte werden aktualisiert.
1. In DB werden neue Datensätze sowohl in der Tabelle `magento_bulk` als auch in der Tabelle `magento_operation` erstellt (Vorgänge im Zusammenhang mit dem Stapel).
1. Neue Datensätze werden in der Tabelle `queue_message` erstellt (bezogen auf die Warteschlangen `product_action_attribute.update` und/oder `product_action_attribute.website.update`).
1. `queue_message_status` -Tabelle enthält Datensätze mit dem Status &quot;4&quot;.
1. In `system.log` gibt es KEINE Fehler.

<u>Tatsächliche Ergebnisse</u>:

1. Auf der Seite wird weiterhin eine Meldung wie die folgende angezeigt:
   *Aufgabe &quot;Attribute für N ausgewählte Produkte aktualisieren&quot;: 1 Element(e) wurde für eine Aktualisierung geplant.*
1. Attributwerte für die Produkte werden aktualisiert.
1. Ein neuer Datensatz wird in der Tabelle `message_bulk` erstellt, aber es gibt keine zugehörigen Datensätze in der Tabelle `magento_operation`.
1. Neue Datensätze werden in den Tabellen `queue_message` und `queue_message_status` erstellt.
1. Die Tabelle `queue_message_status` enthält Datensätze mit Fehlerstatus (Statuswert &quot;6&quot;).
1. `system.log` enthält einen Fehler ähnlich dem folgenden:

   ```sql
   *main.CRITICAL: Message has been rejected: SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'operation_key' cannot be null, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?) [] []*
   ```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [In QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) verfügbare Patches.
