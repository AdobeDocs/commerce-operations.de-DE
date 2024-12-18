---
title: Konfigurieren des Datenbankprofilers
description: Sehen Sie sich ein Beispiel für die Konfiguration der Ausgabe für den Datenbank-Profiler an.
feature: Configuration, Storage
badge: label="Beiträge von Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Konfigurieren des Datenbankprofilers

Der Commerce-Datenbankprofiler zeigt alle auf einer Seite implementierten Abfragen an, einschließlich der Zeit für jede Abfrage und der angewendeten Parameter.

## Schritt 1: Ändern der Bereitstellungskonfiguration

Ändern Sie `<magento_root>/app/etc/env.php` , um den folgenden Verweis zur [Datenbankprofilerklasse“ ](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

Es folgt ein Beispiel:

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

## Schritt 2: Konfigurieren der Ausgabe

Konfigurieren Sie die Ausgabe in der Bootstrap-Datei Ihrer Commerce-Anwendung. Dies kann `<magento_root>/pub/index.php` sein oder sich in einer virtuellen Host-Konfiguration des Webservers befinden.

Im folgenden Beispiel werden Ergebnisse in einer dreispaltigen Tabelle angezeigt:

- Gesamtzeit (zeigt die Gesamtzeit für die Ausführung aller Abfragen auf der Seite an)
- SQL (zeigt alle SQL-Abfragen an; die Zeilenüberschrift zeigt die Anzahl der Abfragen an)
- Abfrageparameter (zeigt die Parameter für jede SQL-Abfrage an)

Um die Ausgabe zu konfigurieren, fügen Sie in Ihrer Bootstrap-Datei nach der Zeile `$bootstrap->run($app);` Folgendes hinzu:

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

Gehen Sie zu einer beliebigen Seite in Ihrer Storefront oder in Ihrem Admin, um die Ergebnisse anzuzeigen. Es folgt ein Beispiel:

![Ergebnisse des Datenbankprofilers](../../assets/configuration/db-profiler-results.png)
