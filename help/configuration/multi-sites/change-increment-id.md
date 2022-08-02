---
title: Inkrement-ID ändern
description: Ändern Sie die Inkrement-ID für eine Commerce-Datenbankentität.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---


# Inkrement-ID ändern

In diesem Artikel wird beschrieben, wie Sie die Inkrement-ID für eine Commerce-Datenbank-Entität (DB) (Bestellung, Rechnungsstellung, Credit Memo usw.) in einem bestimmten Commerce-Store ändern, indem Sie die `ALTER TABLE` SQL-Anweisung.

## Betroffene Versionen

- Adobe Commerce (vor Ort): 2.x.x
- Adobe Commerce über Cloud-Infrastruktur: 2.x.x
- MySQL: [Jede unterstützte Version]

## Wann müssen Sie die Inkrement-ID ändern?

In diesen Fällen müssen Sie möglicherweise die Inkrement-ID für neue DB-Entitäten ändern:

- Nach einer Sicherung auf einer Live-Site
- Einige Bestelldatensätze sind verloren gegangen, aber ihre IDs werden bereits von Payment Gateways (wie PayPal) für Ihr aktuelles Merchant-Konto verwendet. In diesem Fall stoppen die Zahlungswege die Verarbeitung neuer Bestellungen mit denselben IDs und geben den Fehler &quot;Rechnungskennung duplizieren&quot;zurück

>[!INFO]
>
>Sie können auch das Problem mit dem Payment Gateway für PayPal beheben, indem Sie mehrere Zahlungen pro Rechnungskennung in PayPal&#39;s Payment Receiving Preferences zulassen. Siehe [PayPal Gateway Anfrage abgelehnt - Problem mit doppelten Rechnungen] im _Wissensdatenbank_.

## Erforderliche Schritte

1. Suchen Sie Stores und Entitäten, für die die neue Inkrement-ID geändert werden soll.
1. Stellen Sie eine Verbindung zu Ihrer MySQL DB her.
Bei Adobe Commerce in der Cloud-Infrastruktur müssen Sie zunächst über SSH eine Verbindung zu Ihrer Umgebung herstellen.
1. Überprüfen Sie die aktuelle `auto_increment` -Wert für die Entitätssequenztabelle mithilfe der folgenden Abfrage angeben:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Wenn Sie eine automatische Inkrementierung für eine Bestellung im Speicher mit ID=1 überprüfen, lautet der Tabellenname &quot;sequence_order_1&quot;.

Wenn der Wert der `auto_increment` Spalte ist &quot;1234&quot;, die nächste Bestellung, die im Speicher mit `ID=1` weist die Kennung &#39;#100001234&#39; auf.

## Entität aktualisieren, um die Inkrement-ID zu ändern

Aktualisieren Sie die Entität mithilfe der folgenden Abfrage:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
Wichtig: Der neue Inkrementwert muss größer als der aktuelle sein.

Nach Ausführung der folgenden Abfrage:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

Die nächste Bestellung, die im Geschäft mit `ID=1` weist die Kennung &#39;#100002000&#39; auf.

## Zusätzliche empfohlene Schritte für Cloud-Produktionsumgebungen

Vor der Ausführung des `ALTER TABLE` in einer Produktionsumgebung von Adobe Commerce in der Cloud-Infrastruktur abfragen, empfehlen wir dringend, die folgenden Schritte auszuführen:

- Testen Sie das gesamte Verfahren zum Ändern der Inkrement-ID in Ihrer Staging-Umgebung.
- [DB-Backup erstellen] Wiederherstellung der Produktions-DB im Falle eines Fehlers

<!-- Link Definitions -->

[PayPal Gateway Anfrage abgelehnt - Problem mit doppelten Rechnungen]: https://support.magento.com/hc/en-us/articles/115002457473
[DB-Backup erstellen]: https://support.magento.com/hc/en-us/articles/360003254334
[Jede unterstützte Version]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/mysql.html
