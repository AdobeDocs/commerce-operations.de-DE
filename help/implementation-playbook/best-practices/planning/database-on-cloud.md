---
title: Best Practices für die Datenbankkonfiguration für Cloud-Bereitstellungen
description: Erfahren Sie, wie Sie Datenbank- und Anwendungseinstellungen konfigurieren, um die Leistung bei der Bereitstellung von Adobe Commerce in der Cloud-Infrastruktur zu verbessern.
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Best Practices für die Datenbankkonfiguration

Erfahren Sie mehr über Best Practices zur Verbesserung der Datenbankleistung und zur effizienten Verwendung der Datenbank bei der Bereitstellung von Adobe Commerce in der Cloud-Infrastruktur.

## Betroffene Produkte

Adobe Commerce auf Cloud-Infrastruktur

## Alle MyISAM-Tabellen in InnoDB konvertieren

Adobe empfiehlt die Verwendung der InnoDB-Datenbank-Engine. Bei einer standardmäßigen Adobe Commerce-Installation werden alle Datenbanktabellen mithilfe der InnoDB-Engine gespeichert. Einige Module von Drittanbietern (Erweiterungen) können jedoch Tabellen im MyISAM-Format einführen. Überprüfen Sie nach der Installation eines Drittanbietermoduls die Datenbank, um Tabellen in `myisam` formatieren und in konvertieren `innodb` Format.

### Bestimmen, ob ein Modul MyISAM-Tabellen enthält

Sie können den Drittanbieter-Modulcode vor der Installation analysieren, um festzustellen, ob MyISAM-Tabellen verwendet werden.

Wenn Sie bereits eine Erweiterung installiert haben, führen Sie die folgende Abfrage aus, um zu ermitteln, ob die Datenbank über MyISAM-Tabellen verfügt:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### Ändern Sie die Speicher-Engine in InnoDB

Im `db_schema.xml` -Datei, die die Tabelle deklariert, legen Sie die `engine` -Attributwert für die entsprechende `table` Knoten zu `innodb`. Weitere Informationen finden Sie unter [Deklaratives Schema > Tabellenknoten konfigurieren](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) in unserer Entwicklerdokumentation.

Das deklarative Schema wurde in Adobe Commerce in der Cloud-Infrastruktur-Version 2.3 eingeführt.

## Die empfohlene Suchmaschine für die native MySQL-Suche konfigurieren

Adobe empfiehlt, immer Elasticsearch oder OpenSearch für Ihr Adobe Commerce-Projekt in der Cloud-Infrastruktur einzurichten, selbst wenn Sie ein Suchwerkzeug eines Drittanbieters für Ihre Adobe Commerce-Anwendung konfigurieren möchten. Diese Konfiguration bietet eine Fallback-Option für den Fall, dass das Suchtool eines Drittanbieters fehlschlägt.

Die von Ihnen verwendete Suchmaschine hängt von der installierten Adobe Commerce-Cloud-Version ab:

- Verwenden Sie für Adobe Commerce 2.4.4 und höher den OpenSearch-Dienst für die native MySQL-Suche.

- Verwenden Sie für frühere Adobe Commerce-Versionen Elasticsearch.

Führen Sie den folgenden Befehl aus, um zu bestimmen, welche Suchmaschine derzeit verwendet wird:

```bash
./bin/magento config:show catalog/search/engine
```

Konfigurationsanweisungen finden Sie im Entwicklerhandbuch für Adobe Commerce in Cloud:

- [Einrichten des OpenSearch-Dienstes](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [Einrichten des Elasticsearch-Dienstes](https://devdocs.magento.com/cloud/project/services-elastic.html)

## Vermeiden benutzerdefinierter Trigger

Vermeiden Sie nach Möglichkeit die Verwendung von benutzerdefinierten Triggern.

Trigger werden verwendet, um Änderungen in Audit-Tabellen zu protokollieren. Adobe empfiehlt, das Programm so zu konfigurieren, dass es direkt in die Prüftabellen geschrieben wird, anstatt die Trigger-Funktion aus diesen Gründen zu verwenden:

- Trigger werden als Code interpretiert und MySQL stellt sie nicht vorkompiliert. Wenn Sie sich auf die Transaktionsplatzierung Ihrer Abfrage konzentrieren, wird der Mehraufwand für jede mit der Tabelle ausgeführte Abfrage zu einem Parser und Interpreter hinzugefügt.
- Die Trigger teilen sich denselben Transaktionsraum wie die ursprünglichen Abfragen. Während diese Abfragen um Sperren in der Tabelle konkurrieren, konkurrieren die Trigger unabhängig voneinander mit Sperren in einer anderen Tabelle.

Weitere Informationen zu Alternativen zur Verwendung benutzerdefinierter Trigger finden Sie unter [MySQL-Trigger](mysql-configuration.md#triggers).

## Upgrade [!DNL ECE-Tools] auf Version 2002.0.21 oder höher {#ece-tools-version}

Um potenzielle Probleme mit Cron-Deadlocks zu vermeiden, aktualisieren Sie ECE-Tools auf Version 2002.0.21 oder höher. Anweisungen finden Sie unter [Aktualisieren `ece-tools` version](https://devdocs.magento.com/cloud/project/ece-tools-update.html) in unserer Entwicklerdokumentation.

## Indexmodus sicher wechseln

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

Indexer wechseln generiert [!DNL data definition language] (DDL)-Anweisungen zum Erstellen von Triggern, die Datenbanksperren verursachen können. Sie können dieses Problem verhindern, indem Sie Ihre Website in den Wartungsmodus versetzen und Cron-Aufträge deaktivieren, bevor Sie die Konfiguration ändern.
Anweisungen finden Sie unter [Indexer konfigurieren](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) im *Adobe Commerce-Konfigurationshandbuch*.

## Führen Sie keine DDL-Anweisungen in der Produktion aus

Vermeiden Sie das Ausführen von DDL-Anweisungen in der Produktionsumgebung, um Konflikte (wie Tabellenänderungen und -erstellungen) zu vermeiden. Die `setup:upgrade` -Prozess ist eine Ausnahme.

Wenn Sie eine DDL-Anweisung ausführen müssen, stellen Sie die Website in den Wartungsmodus und deaktivieren Sie Cron (siehe Anweisungen zum sicheren Wechsel von Indizes im vorherigen Abschnitt).

## Bestellarchivierung aktivieren

Aktivieren Sie die Bestellarchivierung über den Administrator, um den für Verkaufstabellen erforderlichen Speicherplatz zu reduzieren, wenn Ihre Bestelldaten zunehmen. Durch die Archivierung wird MySQL-Speicherplatz gespart und die Checkout-Leistung verbessert.

Siehe [Aktivieren der Archivierung](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) in der Adobe Commerce Merchant-Dokumentation.

## Zusätzliche Informationen

- [MySQL-Speichermaschinen](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Voraussetzungen für das Adobe Commerce 2.3.5-Upgrade für MariaDB](../maintenance/mariadb-upgrade.md)
- [Best Practices zur Lösung von Problemen mit der Datenbankleistung](../maintenance/resolve-database-performance-issues.md)
