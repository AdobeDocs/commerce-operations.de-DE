---
title: Datenbank-Profiler konfigurieren
description: Sehen Sie sich ein Beispiel für die Konfiguration der Ausgabe für den Datenbank-Profiler an.
feature: Configuration, Storage
badge: label="Verfasst von Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Datenbank-Profiler konfigurieren

Der Commerce-Datenbank-Profiler zeigt alle auf einer Seite implementierten Abfragen an, einschließlich der Zeit für jede Abfrage und der angewendeten Parameter.

## Schritt 1: Ändern der Bereitstellungskonfiguration

Ändern Sie `<magento_root>/app/etc/env.php`, um der [Datenbankprofiler-Klasse](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php) die folgende Referenz hinzuzufügen:

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

Ein Beispiel:

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## Schritt 2: Ausgabe konfigurieren

Konfigurieren Sie die Ausgabe in Ihrer Bootstrap-Datei der Commerce-Anwendung. Dies kann `<magento_root>/pub/index.php` sein oder sich in einer virtuellen Host-Konfiguration des Webservers befinden.

Im folgenden Beispiel werden die Ergebnisse in einer Tabelle mit drei Spalten angezeigt:

- Gesamtzeit (zeigt die Gesamtdauer an, die zum Ausführen aller Abfragen auf der Seite erforderlich ist)
- SQL (zeigt alle SQL-Abfragen an; der Zeilenheader zeigt die Anzahl der Abfragen an)
- Abfrageparameter (zeigt die Parameter für jede SQL-Abfrage an)

Um die Ausgabe zu konfigurieren, fügen Sie Folgendes nach der Zeile `$bootstrap->run($app);` in Ihrer Bootstrap-Datei hinzu:

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## Schritt 3: Ergebnisse anzeigen

Navigieren Sie zu einer beliebigen Seite in Ihrer Storefront oder in Ihrem Administrator, um die Ergebnisse anzuzeigen. Ein Beispiel:

![ Beispiele für Datenbankprofilergebnisse](../../assets/configuration/db-profiler-results.png)
