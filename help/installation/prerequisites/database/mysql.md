---
title: MySQL-Richtlinien
description: Führen Sie diese Schritte aus, um MySQL und MariaDB für lokale Installationen von Adobe Commerce und Magento Open Source zu installieren und zu konfigurieren.
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# Allgemeine MySQL-Richtlinien

Siehe [Systemanforderungen](../../system-requirements.md) für unterstützte MySQL-Versionen.

Adobe _stark_ empfiehlt bei der Einrichtung der Datenbank die Einhaltung des folgenden Standards:

* Verwendung von Adobe Commerce und Magento Open Source [MySQL-Datenbank-Trigger](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) , um den Datenbankzugriff während der Neuindizierung zu verbessern. Diese werden erstellt, wenn der Indexmodus auf [Zeitplan](../../../configuration/cli/manage-indexers.md#configure-indexers). Das Programm unterstützt keine benutzerdefinierten Trigger in der Datenbank, da benutzerdefinierte Trigger Inkompatibilitäten mit zukünftigen Adobe Commerce- und Magento Open Source-Versionen verursachen können.
* Machen Sie sich mit [Diese möglichen Einschränkungen für MySQL Trigger](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) bevor Sie fortfahren.
* Aktivieren Sie zur Erhöhung der Datenbanksicherheit die [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL-Modus, um zu verhindern, dass ungültige Datenwerte gespeichert werden, was zu unerwünschten Datenbankinteraktionen führen kann.
* Adobe Commerce und Magento Open Source _not_ Unterstützung der auf MySQL-Anweisungen basierenden Replikation. Stellen Sie sicher, dass Sie _only_ [row-basierte Replikation](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce verwendet derzeit `CREATE TEMPORARY TABLE` Anweisungen innerhalb von Transaktionen, die [inkompatibel](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) bei Datenbankimplementierungen die GTID-basierte Replikation verwenden, z. B. [Instanzen der zweiten Generation von Google Cloud SQL](https://cloud.google.com/sql/docs/features#differences). Betrachten Sie als Alternative MySQL für Cloud SQL 8.0.

>[!NOTE]
>
>Wenn sich Ihr Webserver und Ihr Datenbankserver auf unterschiedlichen Hosts befinden, führen Sie die in diesem Thema beschriebenen Aufgaben auf dem Datenbankserverhost aus. Informationen dazu finden Sie unter [Eine Remote-Verbindung zur MySQL-Datenbank einrichten](mysql-remote.md).

## Installieren von MySQL auf Ubuntu

Adobe Commerce und Magento Open Source 2.4 erfordern eine saubere Installation von MySQL 8.0. Folgen Sie den unten stehenden Links, um Anweisungen zur Installation von MySQL auf Ihrem Computer zu erhalten.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Wenn Sie mit dem Import einer großen Anzahl von Produkten rechnen, können Sie den Wert für [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) größer als der Standardwert ist, 16 MB.

>[!NOTE]
>
>Der Standardwert gilt für Adobe Commerce in der Cloud-Infrastruktur. _und_ Projekte vor Ort. Kunden von Adobe Commerce on Cloud Infrastructure Pro müssen ein Support-Ticket öffnen, um die `max_allowed_packet` -Wert. Kunden von Adobe Commerce on Cloud Infrastructure Starter können den Wert erhöhen, indem sie die Konfiguration in `/etc/mysql/mysql.cnf` -Datei.

Um den Wert zu erhöhen, öffnen Sie die `/etc/mysql/mysql.cnf` in einem Texteditor und suchen Sie nach dem Wert für `max_allowed_packet`. Speichern Sie Ihre Änderungen in der `mysql.cnf` -Datei, schließen Sie den Texteditor und starten Sie MySQL neu (`service mysql restart`).

Geben Sie den folgenden Befehl an einer `mysql>` Eingabeaufforderung:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Dann [Datenbankinstanz konfigurieren](#configuring-the-database-instance).

## MySQL 8-Änderungen

Für Adobe Commerce und Magento Open Source 2.4 wurde Unterstützung für MySQL 8 hinzugefügt.
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
| `modified` | `timestamp` | NO | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` bei Aktualisierung `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | JA | | `NULL` | |
| `lognum` | `smallint unsigned` | NO | | `0` | |

Außer für _TINYINT(1)_, sollten alle Ganzzahlabstände (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) aus dem `db_schema.xml` -Datei.

Weitere Informationen finden Sie unter [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Standardreihenfolge nach Verhalten

Vor 8.0 wurden Einträge nach Fremdschlüssel sortiert. Die standardmäßige Sortierreihenfolge hängt von der verwendeten Engine ab.
Geben Sie immer eine Sortierreihenfolge an, wenn Ihr Code von einer bestimmten Sortierung abhängig ist.

### Veraltete ASC- und DESC-Qualifikatoren für GRUPPE BY

Ab MySQL 8.0.13 wird die veraltete `ASC` oder `DESC` Qualifikatoren für `GROUP BY` -Klauseln entfernt. Abfragen, die zuvor verwendet wurden `GROUP BY` -Sortierung kann zu Ergebnissen führen, die sich von früheren MySQL-Versionen unterscheiden. Um eine bestimmte Sortierreihenfolge zu erstellen, geben Sie eine `ORDER BY` -Klausel.

## Commerce und MySQL 8

Es wurden einige Änderungen an Adobe Commerce und Magento Open Source vorgenommen, um MySQL 8 ordnungsgemäß zu unterstützen.

### Verhalten bei Abfrage und Einfügen

Adobe Commerce und Magento Open Source haben das reguläre Validierungsverhalten deaktiviert, indem SET SQL_MODE=&#39;&#39; in `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. Wenn die Validierung deaktiviert ist, ist es möglich, dass MySQL Daten abschneidet. In MySQL hat sich das Verhalten der Abfrage geändert: `Select * on my_table where IP='127.0.0.1'` gibt keine Ergebnisse mehr zurück, da die IP-Adresse jetzt ordnungsgemäß als Zeichenfolge und nicht als Ganzzahl betrachtet wird.

## Upgrade von MySQL 5.7 auf MySQL 8

Um MySQL ordnungsgemäß von Version 5.7 auf Version 8 zu aktualisieren, müssen Sie die folgenden Schritte ausführen, um die richtige Reihenfolge zu wählen:

1. Aktualisieren Sie Adobe Commerce oder Magento Open Source auf Version 2.4.0. Testen Sie alles und stellen Sie sicher, dass Ihr System wie erwartet funktioniert.
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

In diesem Abschnitt wird beschrieben, wie Sie eine Datenbankinstanz für Adobe Commerce oder Magento Open Source erstellen. Obwohl empfohlen wird, eine neue Datenbankinstanz zu installieren, können Sie optional Adobe Commerce oder Magento Open Source mit einer vorhandenen Datenbankinstanz installieren.

Konfigurieren einer MySQL-Datenbankinstanz:

1. Melden Sie sich bei Ihrem Datenbankserver als ein beliebiger Benutzer an.
1. Wechseln Sie zu einer MySQL-Eingabeaufforderung:

   ```bash
   mysql -u root -p
   ```

1. MySQL eingeben `root` das Kennwort des Benutzers bei Aufforderung.
1. Geben Sie die folgenden Befehle in der angezeigten Reihenfolge ein, um eine Datenbankinstanz mit dem Namen `magento` mit Benutzername `magento`:

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

1. Eingabe `exit` , um die Eingabeaufforderung zu beenden.

1. Datenbank überprüfen:

   ```bash
   mysql -u magento -p
   ```

   Wenn der MySQL-Monitor angezeigt wird, haben Sie die Datenbank ordnungsgemäß erstellt. Wenn ein Fehler angezeigt wird, wiederholen Sie die vorherigen Befehle.

1. Wenn sich Ihr Webserver und Ihr Datenbankserver auf unterschiedlichen Hosts befinden, führen Sie die in diesem Thema beschriebenen Aufgaben auf dem Datenbankserverhost aus. Informationen dazu finden Sie unter [Eine Remote-Verbindung zur MySQL-Datenbank einrichten](mysql-remote.md).

   Es wird empfohlen, Ihre Datenbankinstanz entsprechend Ihrem Unternehmen zu konfigurieren. Beachten Sie bei der Konfiguration Ihrer Datenbank Folgendes:

   * Indexer erfordern höher `tmp_table_size` und `max_heap_table_size` Werte (z. B. 64 M). Wenn Sie die `batch_size` -Parameter können Sie diesen Wert zusammen mit den Einstellungen für die Tabellengröße anpassen, um die Indexleistung zu verbessern. Siehe Abschnitt [Optimierungshandbuch](../../../performance/configuration.md) für weitere Informationen.

   * Um eine optimale Leistung zu erzielen, stellen Sie sicher, dass alle MySQL- und Adobe Commerce- oder Magento Open Source-Indextabellen im Speicher aufbewahrt werden können (konfigurieren Sie beispielsweise `innodb_buffer_pool_size`).

   * Die Neuindizierung auf MariaDB 10.4 nimmt im Vergleich zu anderen MariaDB- oder MySQL-Versionen mehr Zeit in Anspruch. Siehe [Best Practices bei der Konfiguration](../../../performance/configuration.md#indexers).

1. Für MySQL `TIMESTAMP` Felder, die den Voreinstellungen und der Zusammensetzung entsprechen, die von der deklarativen Schemaarchitektur der Anwendung, der Systemvariablen, erwartet werden `explicit_defaults_for_timestamp` muss auf `on`.

   Verweise:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Wenn diese Einstellung nicht aktiviert ist, `bin/magento setup:db:status` meldet immer, dass die `Declarative Schema is not up to date`.

>[!NOTE]
>
>Die `explicit_defaults_for_timestamp` eingestellt wurde. Diese Einstellung steuert veraltete TIMESTAMP-Verhaltensweisen, die in einer zukünftigen MySQL-Version entfernt werden. Wenn diese Verhaltensweisen entfernt werden, wird die `explicit_defaults_for_timestamp` -Einstellung ebenfalls entfernt.

>[!WARNING]
>
>Für Adobe Commerce bei Cloud-Infrastrukturprojekten muss die `explicit_defaults_for_timestamp` -Einstellung für MySQL (MariaDB) standardmäßig auf _OFF_.

{{$include /help/_includes/maria-db-config.md}}
