---
title: MySQL-Richtlinien
description: Führen Sie diese Schritte aus, um MySQL und MariaDB für lokale Installationen von Adobe Commerce zu installieren und zu konfigurieren.
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# Allgemeine MySQL-Richtlinien

Siehe [Systemanforderungen](../../system-requirements.md) für unterstützte Versionen von MySQL.

Adobe _empfiehlt dringend_ beim Einrichten der Datenbank den folgenden Standard zu beachten:

* Adobe Commerce Trigger verwendet [MySQL-Datenbank-](https://dev.mysql.com/doc/refman/8.0/en/triggers.html), um den Datenbankzugriff während der Neuindizierung zu verbessern. Diese werden erstellt, wenn der Indexermodus auf &quot;[&quot; ](../../../configuration/cli/manage-indexers.md#configure-indexers) ist. Das Programm unterstützt keine benutzerdefinierten Trigger in der Datenbank, da benutzerdefinierte Trigger Inkompatibilitäten mit zukünftigen Adobe Commerce-Versionen einführen können.
* Machen Sie sich mit [diesen potenziellen Einschränkungen von MySQL Trigger ](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) vertraut, bevor Sie fortfahren.
* Um den Sicherheitszustand Ihrer Datenbank zu verbessern, aktivieren Sie den [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL-Modus, um zu verhindern, dass ungültige Datenwerte gespeichert werden, was zu unerwünschten Datenbankinteraktionen führen könnte.
* Adobe Commerce unterstützt _nicht_ die auf MySQL-Anweisungen basierende Replikation. Stellen Sie sicher _dass Sie_[zeilenbasierte Replikation](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html) verwenden.

>[!WARNING]
>
>Adobe Commerce verwendet derzeit `CREATE TEMPORARY TABLE`-Anweisungen innerhalb von Transaktionen, die [inkompatibel](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) mit Datenbankimplementierungen sind und eine GTID-basierte Replikation verwenden, z. B. [Google Cloud SQL-Instanzen der zweiten Generation](https://cloud.google.com/sql/docs/features#differences). Betrachten Sie MySQL für Cloud SQL 8.0 als Alternative.

>[!NOTE]
>
>Wenn sich Ihr Webserver und Datenbankserver auf unterschiedlichen Hosts befinden, führen Sie die in diesem Thema beschriebenen Aufgaben auf dem Datenbankserverhost aus. Weitere Informationen finden Sie unter [Einrichten einer Remote-MySQL-Datenbankverbindung](mysql-remote.md).

## Installieren von MySQL auf Ubuntu

Adobe Commerce 2.4 erfordert eine Neuinstallation von MySQL 8.0. Folgen Sie den unten stehenden Links, um Anweisungen zur Installation von MySQL auf Ihrem Computer zu erhalten.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Wenn Sie erwarten, dass Sie eine große Anzahl von Produkten importieren, können Sie den Wert für [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) erhöhen, der größer ist als der Standardwert (16 MB).

>[!NOTE]
>
>Der Standardwert gilt für Adobe Commerce in Cloud-Infrastruktur _und_ lokalen Projekten. Kunden von Adobe Commerce on Cloud Infrastructure Pro müssen ein Support-Ticket erstellen, um den Wert der `max_allowed_packet` zu erhöhen. Adobe Commerce on Cloud Infrastructure Starter-Kunden können den Wert erhöhen, indem sie die Konfiguration in der `/etc/mysql/mysql.cnf` aktualisieren.

Um den Wert zu erhöhen, öffnen Sie die `/etc/mysql/mysql.cnf` in einem Texteditor und suchen Sie den Wert für `max_allowed_packet`. Speichern Sie Ihre Änderungen in der `mysql.cnf`-Datei, schließen Sie den Texteditor und starten Sie MySQL neu (`service mysql restart`).

Um optional den von Ihnen festgelegten Wert zu überprüfen, geben Sie den folgenden Befehl an einer `mysql>` ein:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Wählen Sie dann [Datenbankinstanz konfigurieren](#configuring-the-database-instance).

## MySQL 8-Änderungen

Für Adobe Commerce 2.4 wurde Unterstützung für MySQL 8 hinzugefügt.
In diesem Abschnitt werden wichtige Änderungen an MySQL 8 beschrieben, die Entwickler beachten sollten.

### Breite für ganzzahlige Typen wurde entfernt (Abstand)

Die Angabe der Anzeigebreite für ganzzahlige Datentypen (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) wird in MySQL 8.0.17 nicht mehr unterstützt. Anweisungen, die Datentypdefinitionen in ihrer Ausgabe enthalten, zeigen die Anzeigebreite für ganzzahlige Typen nicht mehr an, außer für TINYINT(1). MySQL-Connectoren gehen davon aus, dass TINYINT(1)-Spalten als BOOLESCHE Spalten entstanden sind. Diese Ausnahme ermöglicht es ihnen, weiterhin von dieser Annahme auszugehen.

#### Beispiel

Beschreibung von admin_user unter mysql 8.19

| Feld | Typ | Null | Schlüssel | Standard | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NEIN | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | JA | | `NULL` | |
| `lastname` | `varchar(32`) | JA | | `NULL` | |
| `email` | `varchar(128)` | JA | | `NULL` | |
| `username` | `varchar(40)` | JA | EINHEIT | `NULL` | |
| `password` | `varchar(255)` | NEIN | | `NULL` | |
| `created` | `timestamp` | NEIN | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NEIN | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` auf Update-`CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | JA | | `NULL` | |
| `lognum` | `smallint unsigned` | NEIN | | `0` | |

Mit Ausnahme von _TINYINT(1)_ sollten alle ganzzahligen Auffüllungen (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) aus der `db_schema.xml`-Datei entfernt werden.

https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature Weitere Informationen finden Sie unter [&#128279;](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Standardverhalten von ORDER BY

Vor 8.0 wurden die Einträge nach dem Fremdschlüssel sortiert. Die standardmäßige Sortierreihenfolge hängt von der verwendeten Engine ab.
Geben Sie immer eine Sortierreihenfolge an, wenn Ihr Code von einer bestimmten Sortierung abhängt.

### Veraltete ASC- und DESC-Kriterien für GROUP BY

Ab MySQL 8.0.13 wurden die veralteten `ASC`- oder `DESC` für `GROUP BY` entfernt. Abfragen, die sich zuvor auf `GROUP BY` Sortierung stützten, können zu Ergebnissen führen, die sich von früheren MySQL-Versionen unterscheiden. Um eine bestimmte Sortierreihenfolge zu erzeugen, geben Sie eine `ORDER BY` -Klausel an.

## Commerce und MySQL 8

Adobe Commerce wurde geändert, um MySQL 8 ordnungsgemäß zu unterstützen.

### Abfrage- und Einfügeverhalten

Adobe Commerce hat das Verhalten bei regulärer Validierung deaktiviert, indem es SET SQL_MODE=&#39;&#39; in `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.` festgelegt hat. Bei deaktivierter Validierung ist es möglich, dass MySQL Daten abschneidet. In MySQL hat sich das Abfrageverhalten geändert: `Select * on my_table where IP='127.0.0.1'` gibt jetzt keine Ergebnisse mehr zurück, da die IP-Adresse nun korrekt als Zeichenfolge und nicht mehr als Ganzzahl angezeigt wird.

## Aktualisieren von MySQL 5.7 auf MySQL 8

Um MySQL ordnungsgemäß von Version 5.7 auf Version 8 zu aktualisieren, müssen Sie die folgenden Schritte in der richtigen Reihenfolge ausführen:

1. Aktualisieren Sie Adobe Commerce auf 2.4.0.
Testen Sie alles und stellen Sie sicher, dass Ihr System erwartungsgemäß funktioniert.
1. Wartungsmodus aktivieren:

   ```bash
   bin/magento maintenance:enable
   ```

1. Erstellen Sie eine Datenbanksicherung:

   ```bash
   bin/magento setup:backup --db
   ```

1. MySQL auf Version 8 aktualisieren.
1. Importieren Sie die gesicherten Daten in MySQL.
1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```

1. Wartungsmodus deaktivieren:

   ```bash
   bin/magento maintenance:disable
   ```

## Datenbankinstanz konfigurieren

In diesem Abschnitt wird beschrieben, wie Sie eine Datenbankinstanz für Adobe Commerce erstellen. Obwohl eine neue Datenbankinstanz empfohlen wird, können Sie Adobe Commerce optional mit einer vorhandenen Datenbankinstanz installieren.

Konfigurieren einer MySQL-Datenbankinstanz:

1. Melden Sie sich bei Ihrem Datenbank-Server als beliebiger Benutzer an.
1. Wechseln Sie zu einer MySQL-Eingabeaufforderung:

   ```bash
   mysql -u root -p
   ```

1. Geben Sie bei Aufforderung das Kennwort des MySQL-`root`-Benutzers ein.
1. Geben Sie die folgenden Befehle in der angegebenen Reihenfolge ein, um eine Datenbankinstanz mit dem Namen `magento` mit dem Benutzernamen `magento` zu erstellen:

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. Geben Sie `exit` ein, um die Eingabeaufforderung zu beenden.

1. Überprüfen Sie die Datenbank:

   ```bash
   mysql -u magento -p
   ```

   Wenn der MySQL-Monitor angezeigt wird, haben Sie die Datenbank ordnungsgemäß erstellt. Wenn ein Fehler angezeigt wird, wiederholen Sie die vorherigen Befehle.

1. Wenn sich Ihr Webserver und Datenbankserver auf unterschiedlichen Hosts befinden, führen Sie die in diesem Thema beschriebenen Aufgaben auf dem Datenbankserverhost aus. Weitere Informationen finden Sie unter [Einrichten einer Remote-MySQL-Datenbankverbindung](mysql-remote.md).

   Es wird empfohlen, die Datenbankinstanz für Ihr Unternehmen entsprechend zu konfigurieren. Beachten Sie beim Konfigurieren Ihrer Datenbank Folgendes:

   * Indexer benötigen höhere `tmp_table_size` und `max_heap_table_size` Werte (z. B. 64 M). Wenn Sie den `batch_size` konfigurieren, können Sie diesen Wert zusammen mit den Tabellengrößeneinstellungen anpassen, um die Indexerleistung zu verbessern. Weitere Informationen finden Sie [Optimierungshandbuch](../../../performance/configuration.md) .

   * Um eine optimale Leistung zu erzielen, stellen Sie sicher, dass alle MySQL- und Adobe Commerce-Indextabellen im Speicher aufbewahrt werden können (konfigurieren Sie beispielsweise `innodb_buffer_pool_size`).

   * Die Neuindizierung auf MariaDB 10.4 dauert im Vergleich zu anderen MariaDB- oder MySQL-Versionen länger. Siehe [Best Practices für die Konfiguration](../../../performance/configuration.md#indexers).

1. Damit MySQL-`TIMESTAMP` den Voreinstellungen und der Komposition entsprechen, die von der deklarativen Schemaarchitektur des Programms erwartet werden, muss die Systemvariable `explicit_defaults_for_timestamp` auf `on` gesetzt werden.

   Verweise:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Wenn diese Einstellung nicht aktiviert ist, meldet `bin/magento setup:db:status` immer, dass die `Declarative Schema is not up to date`.

>[!NOTE]
>
>Die `explicit_defaults_for_timestamp` Einstellung wird nicht mehr unterstützt. Mit dieser Einstellung werden veraltete ZEITSTEMPEL-Verhaltensweisen gesteuert, die in einer zukünftigen MySQL-Version entfernt werden. Wenn diese Verhaltensweisen entfernt werden, wird auch die `explicit_defaults_for_timestamp` entfernt.

>[!WARNING]
>
>Bei Adobe Commerce in Cloud-Infrastrukturprojekten ist die `explicit_defaults_for_timestamp` für MySQL (MariaDB) standardmäßig auf _OFF_ eingestellt.

{{$include /help/_includes/maria-db-config.md}}
