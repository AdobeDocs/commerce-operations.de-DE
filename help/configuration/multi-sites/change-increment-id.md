---
title: Inkrement-ID ändern
description: Ändern der Inkrement-ID für eine Commerce-Datenbankentität.
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Inkrement-ID ändern

In diesem Artikel wird beschrieben, wie Sie die Inkrement-ID für eine Commerce-Datenbankentität (DB) (Bestellung, Rechnung, Gutschrift usw.) für einen bestimmten Commerce Store mithilfe der `ALTER TABLE` SQL-Anweisung ändern.

## Betroffene Versionen

- Adobe Commerce (On-Premise): 2.x.x
- Adobe Commerce auf Cloud-Infrastruktur: 2.x.x
- MySQL: [Beliebige unterstützte Version](../../installation/prerequisites/database/mysql.md)

## Wann müssten Sie die Inkrement-ID ändern?

Möglicherweise müssen Sie in folgenden Fällen die Inkrement-ID für neue DB-Entitäten ändern:

- Nach einer Hard Backup-Wiederherstellung auf einer Live Site
- Einige Auftragsdatensätze sind verloren gegangen, aber ihre IDs werden bereits von Zahlungs-Gateways (wie PayPal) für Ihr aktuelles Händlerkonto verwendet. In diesem Fall verarbeiten die Zahlungs-Gateways keine neuen Bestellungen mehr, die dieselben IDs haben, sondern geben den Fehler „Rechnungsduplikat-ID“ zurück

>[!INFO]
>
>Sie können das Problem mit dem Zahlungs-Gateway für PayPal auch beheben, indem Sie in den Zahlungseingangsvoreinstellungen von PayPal mehrere Zahlungen pro Rechnungs-ID zulassen. Siehe [PayPal-Gateway-Anfrage abgelehnt - Problem mit doppelter Rechnung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html) in _Wissensdatenbank_.

## Vorausgesetzte Schritte

1. Suchen Sie nach Stores und Entitäten, für die die neue Inkrement-ID geändert werden soll.
1. Verbinden Sie sich mit Ihrer MySQL-DB.
Für Adobe Commerce in der Cloud-Infrastruktur müssen Sie zunächst eine Verbindung mit Ihrer Umgebung über SSH herstellen.
1. Überprüfen Sie den aktuellen `auto_increment` für die Entitätssequenztabelle mithilfe der folgenden Abfrage:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Wenn Sie eine automatische Inkrementierung für eine Bestellung im Store mit der ID=1 überprüfen, wäre der Tabellenname „sequence_order_1“.

Wenn der Wert der `auto_increment` Spalte „1234“ ist, hat die nächste Bestellung im Store mit `ID=1` die ID &quot;#100001234“.

## Entität aktualisieren, um Inkrement-ID zu ändern

Aktualisieren Sie die Entität mithilfe der folgenden Abfrage:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>Wichtig: Der neue Inkrementwert muss größer als der aktuelle Wert sein.

Nach dem Ausführen der folgenden Abfrage:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

Die nächste Bestellung, die mit `ID=1` im Geschäft aufgegeben wird, hat die ID &quot;#100002000“.

## Zusätzliche empfohlene Schritte für Cloud-Produktionsumgebungen

Bevor Sie die `ALTER TABLE` Abfrage in einer Produktionsumgebung von Adobe Commerce in der Cloud-Infrastruktur ausführen, empfehlen wir dringend die folgenden Schritte:

- Testen des gesamten Verfahrens zur Änderung der Inkrement-ID in der Staging-Umgebung
- [Erstellen eines DB-Backups], um die Produktions-DB bei einem Fehler wiederherzustellen

<!-- Link Definitions -->

[PayPal gateway rejected request - duplicate invoice issue]: https://support.magento.com/hc/en-us/articles/115002457473
[Erstellen eines DB-Backups]: https://support.magento.com/hc/en-us/articles/360003254334
[Beliebige unterstützte Version]
