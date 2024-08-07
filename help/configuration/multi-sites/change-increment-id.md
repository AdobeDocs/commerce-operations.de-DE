---
title: Inkrement-ID ändern
description: Ändern Sie die Inkrement-ID für eine Commerce-Datenbankentität.
exl-id: 039fc34c-d9cf-42f4-af5d-16a26a3e8171
source-git-commit: 2a45fe77d5a6fac089ae2c55d0ad047064dd07b0
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Inkrement-ID ändern

In diesem Artikel wird beschrieben, wie Sie die Inkrement-ID für eine Commerce-Datenbank-Entität (DB) (Bestellung, Rechnung, Credit Memo usw.) in einem bestimmten Commerce-Store mithilfe der SQL-Anweisung `ALTER TABLE` ändern.

## Betroffene Versionen

- Adobe Commerce (vor Ort): 2.x.x
- Adobe Commerce in Cloud-Infrastruktur: 2.x.x
- MySQL: [Jede unterstützte Version](../../installation/prerequisites/database/mysql.md)

## Wann müssen Sie die Inkrement-ID ändern?

In diesen Fällen müssen Sie möglicherweise die Inkrement-ID für neue DB-Entitäten ändern:

- Nach einer Sicherung auf einer Live-Site
- Einige Bestelldatensätze sind verloren gegangen, aber ihre IDs werden bereits von Payment Gateways (wie PayPal) für Ihr aktuelles Merchant-Konto verwendet. In diesem Fall stoppen die Zahlungswege die Verarbeitung neuer Bestellungen mit denselben IDs und geben den Fehler &quot;Rechnungskennung duplizieren&quot;zurück

>[!INFO]
>
>Sie können auch das Problem mit dem Payment Gateway für PayPal beheben, indem Sie mehrere Zahlungen pro Rechnungskennung in PayPal&#39;s Payment Receiving Preferences zulassen. Siehe [Zurückgewiesene Anfrage des PayPal-Gateways - Problem mit doppelter Rechnung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/paypal-gateway-rejected-request-duplicate-invoice-issue.html) in der _Wissensdatenbank_.

## Erforderliche Schritte

1. Suchen Sie Stores und Entitäten, für die die neue Inkrement-ID geändert werden soll.
1. Stellen Sie eine Verbindung zu Ihrer MySQL DB her.
Bei Adobe Commerce in der Cloud-Infrastruktur müssen Sie zunächst über SSH eine Verbindung zu Ihrer Umgebung herstellen.
1. Überprüfen Sie den aktuellen `auto_increment` -Wert für die Entitätssequenztabelle mithilfe der folgenden Abfrage:

   ```sql
   SHOW TABLE STATUS FROM `{database_name}` WHERE `name` LIKE 'sequence_{entity_type}_{store_id}';
   ```

Wenn Sie eine automatische Inkrementierung für eine Bestellung im Speicher mit ID=1 überprüfen, lautet der Tabellenname &quot;sequence_order_1&quot;.

Wenn der Wert der Spalte `auto_increment` &quot;1234&quot;ist, hat die nächste Bestellung, die im Speicher mit `ID=1` platziert wird, die Kennung &quot;#100001234&quot;.

## Entität aktualisieren, um die Inkrement-ID zu ändern

Aktualisieren Sie die Entität mithilfe der folgenden Abfrage:

```sql
ALTER TABLE sequence_{entity_type}_{store_id} AUTO_INCREMENT = {new_increment_value};
```

>[!INFO]
>
>Wichtig: Der neue Inkrementwert muss größer als der aktuelle sein.

Nach Ausführung der folgenden Abfrage:

```sql
ALTER TABLE sequence_order_1 AUTO_INCREMENT = 2000;
```

Die nächste Bestellung, die im Store mit &quot;`ID=1`&quot; platziert wird, hat die Kennung &quot;#100002000&quot;.

## Zusätzliche empfohlene Schritte für Cloud-Produktionsumgebungen

Bevor Sie die `ALTER TABLE` -Abfrage in einer Produktionsumgebung von Adobe Commerce in der Cloud-Infrastruktur ausführen, empfehlen wir dringend, die folgenden Schritte auszuführen:

- Testen Sie das gesamte Verfahren zum Ändern der Inkrement-ID in Ihrer Staging-Umgebung.
- [Erstellen Sie eine DB-Sicherung], um im Falle eines Fehlers Ihre Produktions-DB wiederherzustellen.

<!-- Link Definitions -->

[PayPal gateway rejected request - duplicate invoice issue]: https://support.magento.com/hc/en-us/articles/115002457473
[DB-Backup erstellen]: https://support.magento.com/hc/en-us/articles/360003254334
[Jede unterstützte Version]
