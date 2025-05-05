---
title: Best Practices zum Beheben von Problemen mit der Datenbankleistung
description: Erfahren Sie, wie Sie Datenbankprobleme beheben, die die Leistung auf Adobe Commerce-Sites verlangsamen, die in der Cloud-Infrastruktur bereitgestellt werden.
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# Best Practices zum Beheben von Problemen mit der Datenbankleistung

In diesem Artikel wird beschrieben, wie Sie Datenbankprobleme beheben können, die sich negativ auf die Datenbankleistung von Adobe Commerce auf Cloud-Infrastruktur-Sites auswirken.

## Betroffene Versionen

Adobe Commerce auf Cloud-Infrastruktur

## Identifizieren und Auflösen von lang laufenden Abfragen

Ermitteln Sie, ob Sie langsame MySQL-Abfragen haben. Abhängig von Ihrem Adobe Commerce on Cloud-Infrastrukturplan und damit der Verfügbarkeit von Tools haben Sie folgende Möglichkeiten.

### Analysieren von Datenbankabfragen mit MySQL

Sie können MySQL verwenden, um lang laufende Abfragen für jedes Adobe Commerce in Cloud-Infrastrukturprojekt zu identifizieren und aufzulösen.

1. Führen Sie die [`SHOW \[FULL\] PROCESSLIST`](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) aus.
1. Wenn Sie Abfragen mit langer Laufzeit sehen, führen Sie [MySQL-`EXPLAIN` und `EXPLAIN ANALYZE`](https://mysqlserverteam.com/mysql-explain-analyze/) für jede dieser Abfragen aus, um herauszufinden, wodurch die Abfrage lange ausgeführt wird.
1. Führen Sie basierend auf den gefundenen Problemen Schritte aus, um die Abfrage zu beheben, damit sie schneller ausgeführt wird.

### Abfragen mit dem Percona Toolkit analysieren (nur für Pro-Architektur)

Wenn Ihr Adobe Commerce-Projekt in der Pro-Architektur bereitgestellt wird, können Sie das Percona Toolkit zur Analyse von Abfragen verwenden.

1. Führen Sie den `pt-query-digest --type=slowlog`-Befehl für MySQL-Protokolle mit langsamen Abfragen aus.
   * Den Speicherort der langsamen Abfrageprotokolle finden Sie unter **[!UICONTROL Log locations > Service Logs]**(https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/test/log-locations#service-logs) in unserer Entwicklerdokumentation.
   * Weitere Informationen finden [ in der Dokumentation zu Percona Toolkit > pt-query](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest)digest.
1. Führen Sie basierend auf den gefundenen Problemen Schritte aus, um die Abfrage zu beheben, damit sie schneller ausgeführt wird.

## Überprüfen, ob alle Tabellen einen Primärschlüssel haben

Die Definition von Primärschlüsseln ist eine Voraussetzung für einen guten Datenbank- und Tabellenentwurf. Primäre Schlüssel bieten die Möglichkeit, eine Zeile in einer Tabelle eindeutig zu identifizieren.

Wenn Sie Tabellen ohne Primärschlüssel haben, verwendet die standardmäßige Datenbank-Engine für Adobe Commerce (InnoDB) den ersten eindeutigen Schlüssel, der nicht null ist, als Primärschlüssel. Wenn kein eindeutiger Schlüssel verfügbar ist, erstellt InnoDB einen ausgeblendeten Primärschlüssel (6 Byte). Das Problem mit einem implizit definierten Primärschlüssel besteht darin, dass Sie keine Kontrolle darüber haben. Darüber hinaus wird der implizite -Wert global für alle Tabellen ohne Primärschlüssel zugewiesen. Diese Konfiguration kann zu Konflikten führen, wenn gleichzeitig auf diese Tabellen geschrieben wird. Dies kann zu Leistungsproblemen führen, da die Tabellen auch das Inkrement des globalen ausgeblendeten Primärschlüsselindex gemeinsam nutzen.

Vermeiden Sie diese Probleme, indem Sie einen Primärschlüssel für alle Tabellen definieren, die keinen haben.

### Identifizieren und Aktualisieren von Tabellen ohne Primärschlüssel

1. Identifizieren Sie Tabellen ohne Primärschlüssel mithilfe der folgenden SQL-Abfrage:

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. Fügen Sie für jede Tabelle, der ein Primärschlüssel fehlt, einen Primärschlüssel hinzu, indem Sie das `db_schema.xml` (das deklarative Schema) mit einem Knoten ähnlich dem folgenden aktualisieren:

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Wenn Sie den Knoten hinzufügen, ersetzen Sie die Variablen `referenceID` und `column name` durch Ihre benutzerdefinierten Werte.

Weitere Informationen finden Sie unter [Konfigurieren eines deklarativen Schemas](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) in unserer Entwicklerdokumentation.

## Identifizieren und Entfernen doppelter Indizes

Identifizieren Sie alle doppelten Indizes in Ihrer Datenbank und entfernen Sie sie.

### Auf doppelte Indizes prüfen

Um nach doppelten Indizes in der Pro- oder Starter-Cloud-Architektur zu suchen, führen Sie die folgende SQL-Abfrage aus.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

Die Abfrage gibt die Spaltennamen und die Namen aller doppelten Indizes zurück.

Kaufleute, die Pro-Architektur verwenden, können den Test auch mit dem `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)`-Befehl des Percona Toolkits durchführen.

### Doppelte Indizes entfernen

Verwenden Sie die SQL [DROP INDEX-Anweisung](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html), um doppelte Indizes zu entfernen.

```SQL
DROP INDEX
```

## Weitere Informationen

[Best Practices für die Datenbankkonfiguration bei Cloud-Bereitstellungen](../planning/database-on-cloud.md)
