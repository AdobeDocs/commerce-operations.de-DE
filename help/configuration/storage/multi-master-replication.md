---
title: Datenbankreplikation
description: Erfahren Sie mehr über die Vorteile der Konfiguration der Datenbankreplikation.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---


# Datenbankreplikation

{{ee-only}}

{{deprecate-split-db}}

Das Einrichten der Datenbankreplikation bietet die folgenden Vorteile:

- Datensicherung
- Aktiviert die Datenanalyse ohne Beeinträchtigung der Übergeordneten Datenbank
- Skalierbarkeit

MySQL-Datenbanken replizieren asynchron, was bedeutet, dass Slaves nicht dauerhaft verbunden werden müssen, um Updates von der Übergeordneten zu erhalten.

## Datenbankreplikation konfigurieren

Eine ausführliche Diskussion über die Datenbankreplikation fällt nicht in diesen Leitfaden. Zur Einrichtung können Sie eine Ressource wie die folgende konsultieren:

- [MySQL-Dokumentation](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Einrichten der Übergeordneten Slave-Replikation in MySQL (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce bietet Beispiel-MySQL-Konfigurationen für Ihre Slave-Datenbanken. Eine einfache Konfiguration wird mit dem `ResourceConnections` class `README.md`.

Die folgenden Informationen sind weiter gefasst und dienen nur Ihren Informationen:

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## Leistungsverbesserung

Um die Leistung der Übergeordneten Slave-Replikation zu verbessern, können Sie einige Tabellen nach Slave-Instanzen filtern. Es wird empfohlen, alle temporären Tabellen mit Namensmustern zu filtern `search\_tmp\_%` die für die Katalogsuche verwendet werden.

Fügen Sie dazu die folgende Zeile zu Ihrer `my.cnf` Datei auf Ihren Slave-Instanzen:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
