---
title: Best Practices zur Lösung von Problemen mit der Datenbankleistung
description: Erfahren Sie, wie Sie Datenbankprobleme beheben, die die Leistung auf Adobe Commerce-Sites verlangsamen, die in der Cloud-Infrastruktur bereitgestellt werden.
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# Best Practices zur Lösung von Problemen mit der Datenbankleistung

In diesem Artikel wird beschrieben, wie Datenbankprobleme behoben werden, die sich negativ auf die Datenbankleistung in Adobe Commerce auf Cloud-Infrastruktur-Sites auswirken.

## Betroffene Versionen

Adobe Commerce auf Cloud-Infrastruktur

## Identifizieren und Auflösen langwieriger Abfragen

Bestimmen Sie, ob MySQL-Abfragen langsam ausgeführt werden. Je nach Adobe Commerce-Plan zur Cloud-Infrastruktur und somit der Verfügbarkeit von Tools können Sie Folgendes tun:

### Datenbankabfragen mit MySQL analysieren

Sie können MySQL verwenden, um langwierige Abfragen in Adobe Commerce in Cloud-Infrastrukturprojekten zu identifizieren und zu beheben.

1. Führen Sie die [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) -Anweisung.
1. Wenn langwierige Abfragen angezeigt werden, führen Sie [MySQL `EXPLAIN` und `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) für jeden dieser Profile, um herauszufinden, was die Abfrage über einen langen Zeitraum ausführt.
1. Führen Sie je nach den gefundenen Problemen Schritte aus, um die Abfrage zu korrigieren, damit sie schneller ausgeführt werden kann.

### Abfragen mit dem Percona Toolkit analysieren (nur für Pro-Architektur)

Wenn Ihr Adobe Commerce-Projekt in der Pro-Architektur bereitgestellt wird, können Sie die Abfragen mit dem Percona Toolkit analysieren.

1. Führen Sie die `pt-query-digest --type=slowlog` -Befehl für langsame MySQL-Abfrageprotokolle.
   * Informationen zum Speicherort der langsamen Abfrageprotokolle finden Sie unter **[!UICONTROL Log locations > Service Logs]**(https://devdocs.magento.com/cloud/project/log-locations.html#service-logs) in unserer Entwicklerdokumentation.
   * Siehe [Percona Toolkit > pt-query-digest](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) Dokumentation.
1. Führen Sie je nach den gefundenen Problemen Schritte aus, um die Abfrage zu korrigieren, damit sie schneller ausgeführt werden kann.

## Überprüfen, ob alle Tabellen über einen Primärschlüssel verfügen

Die Definition von Primärschlüsseln ist eine Voraussetzung für ein gutes Datenbank- und Tabellendesign. Mit Primären Schlüsseln können Sie eine Zeile in einer beliebigen Tabelle eindeutig identifizieren.

Wenn Sie über Tabellen ohne Primärschlüssel verfügen, verwendet die standardmäßige Datenbank-Engine für Adobe Commerce (InnoDB) den ersten eindeutigen Schlüssel (nicht den Nullschlüssel) als Primärschlüssel. Wenn kein eindeutiger Schlüssel verfügbar ist, erstellt InnoDB einen ausgeblendeten Primärschlüssel (6 Byte). Das Problem mit einem implizit definierten Primärschlüssel besteht darin, dass Sie keine Kontrolle darüber haben. Darüber hinaus wird der implizite Wert für alle Tabellen ohne Primärschlüssel global zugewiesen. Diese Konfiguration kann bei gleichzeitigen Schreibvorgängen für diese Tabellen zu Konflikten führen. Dies kann zu Leistungsproblemen führen, da die Tabellen auch die Indexinkrementierung des globalen ausgeblendeten Primärschlüssels gemeinsam nutzen.

Vermeiden Sie diese Probleme, indem Sie einen Primärschlüssel für Tabellen definieren, die keine haben.

### Identifizieren und Aktualisieren von Tabellen ohne Primärschlüssel

1. Identifizieren Sie Tabellen ohne Primärschlüssel mithilfe der folgenden SQL-Abfrage:

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. Fügen Sie für jede Tabelle, in der ein Primärschlüssel fehlt, einen Primärschlüssel hinzu, indem Sie die `db_schema.xml` (das deklarative Schema) mit einem Knoten ähnlich dem folgenden:

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Wenn Sie den Knoten hinzufügen, ersetzen Sie die `referenceID` und `column name` Variablen mit Ihren benutzerdefinierten Werten.

Weitere Informationen finden Sie unter [Deklaratives Schema konfigurieren](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) in unserer Entwicklerdokumentation.

## Identifizieren und Entfernen doppelter Indizes

Identifizieren Sie alle doppelten Indizes in Ihrer Datenbank und entfernen Sie sie.

### Überprüfen auf doppelte Indizes

Um in der Pro- oder Starter-Cloud-Architektur nach doppelten Indizes zu suchen, führen Sie die folgende SQL-Abfrage aus.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

Die Abfrage gibt die Spaltennamen und die Namen aller doppelten Indizes zurück.

Pro Architecture-Händler können die Prüfung auch mit dem Percona Toolkit ausführen  `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` Befehl.

### Duplizierte Indizes entfernen

SQL verwenden [DROP INDEX-Anweisung](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) , um doppelte Indizes zu entfernen.

```SQL
DROP INDEX
```

## Zusätzliche Informationen

[Best Practices für die Datenbankkonfiguration für Cloud-Bereitstellungen](../planning/database-on-cloud.md)
