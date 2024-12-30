---
title: Best Practices für die Datenbankkonfiguration bei Cloud-Bereitstellungen
description: Erfahren Sie, wie Sie Datenbank- und Anwendungseinstellungen konfigurieren, um die Leistung bei der Bereitstellung von Adobe Commerce in Cloud-Infrastrukturen zu verbessern.
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Best Practices für die Datenbankkonfiguration

Erfahren Sie mehr über Best Practices zur Verbesserung der Datenbankleistung und zum effizienten Arbeiten mit der Datenbank bei der Bereitstellung von Adobe Commerce in der Cloud-Infrastruktur.

## Betroffene Produkte

Adobe Commerce auf Cloud-Infrastruktur

## Alle MyISAM-Tabellen in InnoDB konvertieren

Adobe empfiehlt die Verwendung der InnoDB-Datenbank-Engine. Bei einer Standardinstallation von Adobe Commerce werden alle Tabellen in der Datenbank mit der InnoDB-Engine gespeichert. Einige Drittanbietermodule (Erweiterungen) können jedoch Tabellen im MyISAM-Format einführen. Überprüfen Sie nach der Installation eines Drittanbietermoduls die Datenbank, um alle Tabellen im `myisam`-Format zu identifizieren und in `innodb` Format zu konvertieren.

### Prüfen, ob ein Modul MyISAM-Tabellen enthält

Sie können den Drittanbietermodul-Code vor der Installation analysieren, um festzustellen, ob er MyISAM-Tabellen verwendet.

Wenn Sie bereits eine Erweiterung installiert haben, führen Sie die folgende Abfrage aus, um festzustellen, ob die Datenbank über MyISAM-Tabellen verfügt:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Ändern der Speicher-Engine in InnoDB

Legen Sie in der `db_schema.xml`-Datei, die die Tabelle deklariert, den `engine` Attributwert für den entsprechenden `table` auf `innodb` fest. Weitere Informationen finden Sie unter [Konfigurieren eines deklarativen Schemas > Tabellenknoten](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) in unserer Entwicklerdokumentation.

Das deklarative Schema wurde in Adobe Commerce in der Cloud-Infrastrukturversion 2.3 eingeführt.

## Konfigurieren der empfohlenen Suchmaschine für die native MySQL-Suche

Adobe empfiehlt, Elasticsearch oder OpenSearch immer für Ihr Adobe Commerce on Cloud-Infrastrukturprojekt einzurichten, auch wenn Sie ein Drittanbieter-Suchwerkzeug für Ihr Adobe Commerce-Programm konfigurieren möchten. Diese Konfiguration bietet eine Fallback-Option für den Fall, dass das Drittanbieter-Such-Tool fehlschlägt.

Welche Suchmaschine Sie verwenden, hängt von der installierten Version von Adobe Commerce on Cloud ab:

- Verwenden Sie für Adobe Commerce 2.4.4 und höher den OpenSearch-Service für die native MySQL-Suche.

- Verwenden Sie für frühere Adobe Commerce-Versionen Elasticsearch.

Um festzustellen, welche Suchmaschine derzeit verwendet wird, führen Sie den folgenden Befehl aus:

```bash
./bin/magento config:show catalog/search/engine
```

Konfigurationsanweisungen finden Sie im Entwicklerhandbuch für Adobe Commerce in Cloud Manager:

- [Einrichten des OpenSearch-Service](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/opensearch)

- [Einrichten des Elasticsearch-Service](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)

## Benutzerdefinierte Trigger vermeiden

Verwenden Sie nach Möglichkeit keine benutzerdefinierten Trigger.

Trigger werden verwendet, um Änderungen in Audit-Tabellen zu protokollieren. Adobe empfiehlt aus den folgenden Gründen, die Anwendung so zu konfigurieren, dass sie direkt in die Audit-Tabellen schreibt, anstatt die Trigger-Funktion zu verwenden:

- Trigger werden als Code interpretiert und von MySQL nicht vorkompiliert. Durch das Anbinden an den Transaktionsbereich Ihrer Abfrage wird der Overhead für jede mit der Tabelle durchgeführte Abfrage einem Parser und Interpreter hinzugefügt.
- Die Trigger nutzen denselben Transaktionsbereich wie die Originalabfragen. Während diese Abfragen um Tabellensperren konkurrieren, konkurrieren die Trigger unabhängig voneinander um Sperren in einer anderen Tabelle.

Weitere Informationen zu Alternativen zur Verwendung benutzerdefinierter Trigger finden Sie unter [MySQL-Trigger ](mysql-configuration.md#triggers).

## Upgrade von [!DNL ECE-Tools] auf Version 2002.0.21 oder höher {#ece-tools-version}

Um potenzielle Probleme mit Cron-Deadlocks zu vermeiden, aktualisieren Sie ECE-Tools auf Version 2002.0.21 oder höher. Anweisungen finden Sie unter [Aktualisieren `ece-tools` Version](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package) in unserer Entwicklerdokumentation.

## Indexermodus sicher wechseln

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

Beim Wechsel des Indexers werden [!DNL data definition language] (DDL)-Anweisungen generiert, um Trigger zu erstellen, die zu Datenbanksperren führen können. Sie können dieses Problem verhindern, indem Sie Ihre Website in den Wartungsmodus versetzen und Cron-Aufträge deaktivieren, bevor Sie die Konfiguration ändern.
Anweisungen finden Sie [Konfigurieren von ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1)) im *Adobe Commerce-Konfigurationshandbuch*.

## DDL-Anweisungen nicht in Produktion ausführen

Vermeiden Sie die Ausführung von DDL-Anweisungen in der Produktionsumgebung, um Konflikte (wie Tabellenänderungen und -erstellungen) zu vermeiden. Der `setup:upgrade` bildet eine Ausnahme.

Wenn Sie eine DDL-Anweisung ausführen müssen, setzen Sie die Website in den Wartungsmodus und deaktivieren Sie Cron (siehe die Anweisungen zum sicheren Wechseln der Indizes im vorherigen Abschnitt).

## Auftragsarchivierung aktivieren

Aktivieren Sie die Auftragsarchivierung vom Administrator aus, um den Platz für Verkaufstabellen zu reduzieren, wenn Ihre Auftragsdaten wachsen. Die Archivierung spart MySQL Speicherplatz und verbessert die Checkout-Leistung.

Siehe [Archivierung aktivieren](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) in der Dokumentation zu Adobe Commerce Merchant.

## Weitere Informationen

- [MySQL-Speicher-Engines](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Voraussetzungen für die Aktualisierung auf Adobe Commerce 2.3.5 für MariaDB](../maintenance/mariadb-upgrade.md)
- [Best Practices zum Beheben von Problemen mit der Datenbankleistung](../maintenance/resolve-database-performance-issues.md)
