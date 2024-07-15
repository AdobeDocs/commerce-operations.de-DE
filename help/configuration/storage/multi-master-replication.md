---
title: Datenbankreplikation
description: Erfahren Sie mehr über die Vorteile der Konfiguration der Datenbankreplikation.
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Datenbankreplikation

{{ee-only}}

{{deprecate-split-db}}

Das Einrichten der Datenbankreplikation bietet die folgenden Vorteile:

- Datensicherung
- Aktiviert die Datenanalyse ohne Beeinträchtigung der Master-Datenbank
- Skalierbarkeit

MySQL-Datenbanken replizieren asynchron, was bedeutet, dass Slaves nicht dauerhaft verbunden werden müssen, um Updates vom Master zu erhalten.

## Datenbankreplikation konfigurieren

Eine ausführliche Diskussion über die Datenbankreplikation fällt nicht in diesen Leitfaden. Zur Einrichtung können Sie eine Ressource wie die folgende konsultieren:

- [MySQL-Dokumentation](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Einrichten der Master-Slave-Replikation in MySQL (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce stellt Beispiel-MySQL-Konfigurationen für Ihre Slave-Datenbanken bereit. Eine einfache Konfiguration wird mit der `ResourceConnections`-Klasse `README.md` bereitgestellt.

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

Um die Leistung der Master-Slave-Replikation zu verbessern, können Sie einige Tabellen auf Slave-Instanzen filtern. Es wird empfohlen, alle temporären Tabellen mit dem Namensmuster `search\_tmp\_%` zu filtern, die für die Katalogsuche verwendet werden.

Fügen Sie dazu der Datei `my.cnf` in Ihren Slave-Instanzen die folgende Zeile hinzu:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
