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

Unter [Systemanforderungen](../../system-requirements.md) finden Sie unterstützte Versionen von MySQL.

Adobe _strong_ empfiehlt, beim Einrichten der Datenbank den folgenden Standard zu beachten:

* Adobe Commerce verwendet [MySQL-Datenbank-Trigger](https://dev.mysql.com/doc/refman/8.0/en/triggers.html), um den Datenbankzugriff während der Neuindizierung zu verbessern. Diese werden erstellt, wenn der Indexmodus auf [schedule](../../../configuration/cli/manage-indexers.md#configure-indexers) festgelegt ist. Das Programm unterstützt keine benutzerdefinierten Trigger in der Datenbank, da benutzerdefinierte Trigger Inkompatibilitäten mit zukünftigen Adobe Commerce-Versionen verursachen können.
* Machen Sie sich mit [diesen möglichen Einschränkungen für MySQL-Trigger](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) vertraut, bevor Sie fortfahren.
* Um die Sicherheit Ihrer Datenbank zu verbessern, aktivieren Sie den SQL-Modus [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) , um zu verhindern, dass ungültige Datenwerte gespeichert werden, was zu unerwünschten Datenbankinteraktionen führen kann.
* Adobe Commerce unterstützt _nicht_ die auf MySQL-Anweisungen basierende Replikation. Stellen Sie sicher, dass Sie die Zeilenbasierte Replikation _nur_ [ ](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html) verwenden.

>[!WARNING]
>
>Adobe Commerce verwendet derzeit `CREATE TEMPORARY TABLE` -Anweisungen innerhalb von Transaktionen, die [inkompatibel](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) mit Datenbankimplementierungen sind und die GTID-basierte Replikation verwenden, z. B. [Google Cloud SQL-Instanzen der zweiten Generation](https://cloud.google.com/sql/docs/features#differences). Betrachten Sie als Alternative MySQL für Cloud SQL 8.0.

>[!NOTE]
>
>Wenn sich Ihr Webserver und Ihr Datenbankserver auf unterschiedlichen Hosts befinden, führen Sie die in diesem Thema beschriebenen Aufgaben auf dem Datenbankserverhost aus und lesen Sie dann den Abschnitt [Einrichten einer Remote-MySQL-Datenbankverbindung](mysql-remote.md).

## Installieren von MySQL auf Ubuntu

Für Adobe Commerce 2.4 ist eine saubere Installation von MySQL 8.0 erforderlich. Folgen Sie den unten stehenden Links, um Anweisungen zur Installation von MySQL auf Ihrem Computer zu erhalten.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Wenn Sie erwarten, dass eine große Anzahl von Produkten importiert wird, können Sie den Wert für [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) erhöhen, der größer als der Standardwert (16 MB) ist.

>[!NOTE]
>
>Der Standardwert gilt für Adobe Commerce bei Cloud-Infrastrukturprojekten _und_ vor Ort. Kunden von Adobe Commerce on Cloud Infrastructure Pro müssen ein Support-Ticket öffnen, um den `max_allowed_packet` -Wert zu erhöhen. Kunden von Adobe Commerce on Cloud Infrastructure Starter können den Wert erhöhen, indem sie die Konfiguration in der Datei `/etc/mysql/mysql.cnf` aktualisieren.

Um den Wert zu erhöhen, öffnen Sie die Datei `/etc/mysql/mysql.cnf` in einem Texteditor und suchen Sie den Wert für `max_allowed_packet`. Speichern Sie Ihre Änderungen in der Datei &quot;`mysql.cnf`&quot;, schließen Sie den Texteditor und starten Sie MySQL (`service mysql restart`) neu.

Geben Sie den folgenden Befehl an einer `mysql>` -Eingabeaufforderung ein, um optional den von Ihnen festgelegten Wert zu überprüfen:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Konfigurieren Sie dann [die Datenbankinstanz](#configuring-the-database-instance).

## MySQL 8-Änderungen

Für Adobe Commerce 2.4 wurde Unterstützung für MySQL 8 hinzugefügt.
In diesem Abschnitt werden wichtige Änderungen an MySQL 8 beschrieben, die Entwickler kennen sollten.

### Die Breite für ganzzahlige Typen wurde entfernt (Umrandung)

Die Spezifikation der Anzeigebreite für ganzzahlige Datentypen (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) ist in MySQL 8.0.17 nicht mehr enthalten. Anweisungen, die Datentypdefinitionen in ihrer Ausgabe enthalten, zeigen die Anzeigebreite für ganzzahlige Typen nicht mehr an, mit Ausnahme von TINYINT(1). MySQL Connectors gehen davon aus, dass die TINYINT(1)-Spalten als BOOLEAN-Spalten stammen. Diese Ausnahme ermöglicht es ihnen, diese Annahme fortzusetzen.

#### Beispiel

Beschreiben Sie admin_user unter mysql 8.19

| Feld | Typ | Null | Schlüssel | Standard | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NO | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | JA | | `NULL` | |
| `lastname` | `varchar(32`) | JA | | `NULL` | |
| `email` | `varchar(128)` | JA | | `NULL` | |
| `username` | `varchar(40)` | JA | UNI | `NULL` | |
| `password` | `varchar(255)` | NO | | `NULL` | |
| `created` | `timestamp` | NO | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NO | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` bei Update `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | JA | | `NULL` | |
| `lognum` | `smallint unsigned` | NO | | `0` | |

Mit Ausnahme von _TINYINT(1)_ sollten alle Ganzzahlabstände (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) aus der Datei `db_schema.xml` entfernt werden.

Weitere Informationen finden Sie unter [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Standardreihenfolge nach Verhalten

Vor 8.0 wurden Einträge nach Fremdschlüssel sortiert. Die standardmäßige Sortierreihenfolge hängt von der verwendeten Engine ab.
Geben Sie immer eine Sortierreihenfolge an, wenn Ihr Code von einer bestimmten Sortierung abhängig ist.

### Veraltete ASC- und DESC-Qualifikatoren für GRUPPE BY

Ab MySQL 8.0.13 wurden die veralteten `ASC` - oder `DESC` -Qualifikatoren für `GROUP BY` -Klauseln entfernt. Abfragen, die zuvor auf eine Sortierung mit dem Wert `GROUP BY` zurückgegriffen haben, können zu Ergebnissen führen, die sich von früheren MySQL-Versionen unterscheiden. Um eine bestimmte Sortierreihenfolge zu erstellen, geben Sie eine `ORDER BY` -Klausel an.

## Commerce und MySQL 8

Es wurden einige Änderungen an Adobe Commerce vorgenommen, um MySQL 8 ordnungsgemäß zu unterstützen.

### Verhalten bei Abfrage und Einfügen

Adobe Commerce hat das reguläre Validierungsverhalten deaktiviert, indem SET SQL_MODE=&#39;&#39; in `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.` festgelegt wurde. Wenn die Validierung deaktiviert ist, ist es möglich, dass MySQL Daten abschneidet. In MySQL hat sich das Verhalten der Abfrage geändert: `Select * on my_table where IP='127.0.0.1'` gibt keine Ergebnisse mehr zurück, da die IP-Adresse jetzt ordnungsgemäß als Zeichenfolge und nicht als Ganzzahl betrachtet wird.

## Upgrade von MySQL 5.7 auf MySQL 8

Um MySQL ordnungsgemäß von Version 5.7 auf Version 8 zu aktualisieren, müssen Sie die folgenden Schritte ausführen, um die richtige Reihenfolge zu wählen:

1. Aktualisieren Sie Adobe Commerce auf 2.4.0.
Testen Sie alles und stellen Sie sicher, dass Ihr System wie erwartet funktioniert.
1. Wartungsmodus aktivieren:

   ```bash
   bin/magento maintenance:enable
   ```

1. Erstellen Sie eine Datenbanksicherung:

   ```bash
   bin/magento setup:backup --db
   ```

1. Aktualisieren Sie MySQL auf Version 8.
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

In diesem Abschnitt wird beschrieben, wie Sie eine Datenbankinstanz für Adobe Commerce erstellen. Obwohl empfohlen wird, eine neue Datenbankinstanz zu installieren, können Sie optional Adobe Commerce mit einer vorhandenen Datenbankinstanz installieren.

Konfigurieren einer MySQL-Datenbankinstanz:

1. Melden Sie sich bei Ihrem Datenbankserver als ein beliebiger Benutzer an.
1. Wechseln Sie zu einer MySQL-Eingabeaufforderung:

   ```bash
   mysql -u root -p
   ```

1. Geben Sie bei Aufforderung das Kennwort des MySQL `root`-Benutzers ein.
1. Geben Sie die folgenden Befehle in der angezeigten Reihenfolge ein, um eine Datenbankinstanz mit dem Namen `magento` mit dem Benutzernamen `magento` zu erstellen:

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

1. Datenbank überprüfen:

   ```bash
   mysql -u magento -p
   ```

   Wenn der MySQL-Monitor angezeigt wird, haben Sie die Datenbank ordnungsgemäß erstellt. Wenn ein Fehler angezeigt wird, wiederholen Sie die vorherigen Befehle.

1. Wenn sich Ihr Webserver und Ihr Datenbankserver auf unterschiedlichen Hosts befinden, führen Sie die in diesem Thema beschriebenen Aufgaben auf dem Datenbankserverhost aus und lesen Sie dann den Abschnitt [Einrichten einer Remote-MySQL-Datenbankverbindung](mysql-remote.md).

   Es wird empfohlen, Ihre Datenbankinstanz entsprechend Ihrem Unternehmen zu konfigurieren. Beachten Sie bei der Konfiguration Ihrer Datenbank Folgendes:

   * Indexer erfordern höhere Werte für `tmp_table_size` und `max_heap_table_size` (z. B. 64 M). Wenn Sie den Parameter `batch_size` konfigurieren, können Sie diesen Wert zusammen mit den Einstellungen für die Tabellengröße anpassen, um die Indexleistung zu verbessern. Weitere Informationen finden Sie im [Optimierungshandbuch](../../../performance/configuration.md) .

   * Um eine optimale Leistung zu erzielen, stellen Sie sicher, dass alle MySQL- und Adobe Commerce-Indextabellen im Speicher aufbewahrt werden können (z. B. `innodb_buffer_pool_size` konfigurieren).

   * Die Neuindizierung auf MariaDB 10.4 nimmt im Vergleich zu anderen MariaDB- oder MySQL-Versionen mehr Zeit in Anspruch. Siehe [Best Practices für die Konfiguration](../../../performance/configuration.md#indexers).

1. Damit MySQL `TIMESTAMP` -Felder den Voreinstellungen und Kompositionen entsprechen, die von der deklarativen Schemaarchitektur der Anwendung erwartet werden, muss die Systemvariable `explicit_defaults_for_timestamp` auf `on` gesetzt werden.

   Verweise:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Wenn diese Einstellung nicht aktiviert ist, meldet `bin/magento setup:db:status` immer das `Declarative Schema is not up to date`.

>[!NOTE]
>
>Die Einstellung `explicit_defaults_for_timestamp` wird nicht mehr unterstützt. Diese Einstellung steuert veraltete TIMESTAMP-Verhaltensweisen, die in einer zukünftigen MySQL-Version entfernt werden. Wenn diese Verhaltensweisen entfernt werden, wird auch die Einstellung `explicit_defaults_for_timestamp` entfernt.

>[!WARNING]
>
>Bei Adobe Commerce für Cloud-Infrastrukturprojekte ist die Einstellung `explicit_defaults_for_timestamp` für MySQL (MariaDB) standardmäßig auf _OFF_ eingestellt.

{{$include /help/_includes/maria-db-config.md}}
