---
title: Best Practices für das Debugging
description: Erfahren Sie mehr über Verfahren zur Lösung häufiger Adobe Commerce-Entwicklungsprobleme.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---


# Debugging von Best Practices für Adobe Commerce

In diesem Thema wird erläutert, wie das Adobe Commerce-Framework systematisch und effektiv debuggt werden kann. Ziel ist es, Ihnen dabei zu helfen, schnell zur Wurzel eines Problems zu gelangen und die Untersuchungszeit zu minimieren.

## Fehlerbehebung: Übliche Verdächtige

In diesem Abschnitt werden die häufigsten Probleme beschrieben, auf die Sie bei der Entwicklung stoßen können.

### Cache

- Leeren Sie den Cache vor weiteren Untersuchungen.
- Betrachten Sie den APC-Cache, CDN, Varnish, generierten Code und die `var/view_preprocessed` und `pub/static/` Verzeichnisse
- Beenden und Neustart von Warteschlangen-Handlern nach dem Leeren des Cache oder Ändern des Codes

Das folgende Codebeispiel enthält hilfreiche Befehle zum Verwalten des Caches (nicht in Produktionsumgebungen ausführen):

```bash
# restart php-fpm to flush APC
sudo service php-fpm restart
 
# restart varnish to force full flush
sudo service varnish restart
 
# clear generated files
rm -rf generated/*
 
# clear static file cache
rm -rf var/view_preprocessed/*
rm -rf pub/static/*
 
# flush redis cache
redis-cli -n <db_number> FLUSHDB
 
# flush redis cache and sessions
redis-cli FLUSHALL
 
# flush redis cache with telnet
telnet <ip_or_host> 6379
SELECT <db_number>
FLUSHDB
Ctrl + ]
quit
 
# flush redis cache and sessions with telnet
telnet <ip_or_host> 6379
FLUSHALL
Ctrl + ]
quit
 
# find consumers
pgrep -af queue:consumers:start
 
# kill all queue consumers (they will restart by cron job)
sudo pkill -f queue:consumers:start
 
# kill a specific queue consumer (it will restart by cron job)
sudo kill <process_id>
```

### Indexierte Daten

Neuindizieren Sie alles neu, wenn das Problem möglicherweise indexbezogen ist. Das Debuggen indizierter Daten erfolgt normalerweise in Nicht-Produktionsumgebungen. In Produktionsumgebungen möchten Sie möglicherweise den Ursprung der Indexabweichung vor der Neuindizierung untersuchen. Die Eigenschaften des fehlerhaften Zustands können Ihnen etwas über den Ursprung des Problems vermitteln.

### Verfasser

Möglicherweise ist der Code aufgrund einer Verzweigungsänderung oder aufgrund von Kerndateien, die bei einem früheren Debugging-Vorgang bearbeitet wurden, veraltet. Führen Sie die folgenden Befehle aus, um potenzielle Probleme zu vermeiden:

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### Generierter Inhalt

Erstellen Sie Frontend-Dateien neu, bevor Sie den generierten Inhalt in JS, CSS, Bildern, Übersetzungen und anderen Dateien debuggen.

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### Entwicklermodus

Stellen Sie sicher, dass sich Ihre lokale Installation unter `developer` -Modus.

### Neues Modul

Wenn Sie ein Modul erstellt haben, überprüfen Sie, ob folgende Probleme vorliegen:

- Ist das Modul aktiviert?

  ```bash
  bin/magento module --enable Your_Module
  ```

  Überprüfen Sie die `app/etc/config.php` -Datei für Ihr neues Modul.

- Überprüfen Sie die Verschachtelung der Datei- und Ordnerstruktur. Beispielsweise sind Layout-Dateien in der Variablen `view/layout/` anstatt des `view/frontend/layout` Verzeichnis? Sind Vorlagen in der `view/frontend/template` anstatt des `view/frontend/templates` Verzeichnis?

## Fehlerbehebung: Halbtrennung

Wenn die üblichen Verdächtigen keine Lösung für das Problem bieten, ist der schnellste Weg, das Problem zu lösen, indem sie das Problem halbieren (oder zerteilen). Mit dieser Methode vermeiden Sie große Teile und teilen, was übrig bleibt, um die Grundursache zu finden, anstatt den Code linear zu durchlaufen.

Siehe folgende Diagramme:

![Auswahldiagramm](../../../assets/playbooks/bisect.png)

![Auswahldiagramm](../../../assets/playbooks/bisect2.png)

Es gibt mehrere Möglichkeiten, etwas zu zerlegen. Adobe empfiehlt jedoch, diese Reihenfolge zu befolgen:

- Themenauswahl
- Auswahl durch Zusagen
- Auswahl nach Dateien

### Schritt 1: Themenauswahl

Wenn das Problem möglicherweise nicht codebezogen ist, müssen Sie die großen Blöcke zuerst entfernen. Zu den großen Blöcken, an die gedacht werden sollte, gehören:

- **Adobe Commerce-Framework**—Ist das Problem überhaupt mit Adobe Commerce verbunden oder könnte es mit einem anderen verbundenen System verbunden sein?
- **Server und Client**—Löschen Sie den Browsercache und den Speicher. Ist das Problem gelöst? Dies kann eine serverbasierte Ursache ausschließen. Gibt es das Problem noch? Sie müssen keine Zeit mehr im Browser-Debugging verschwenden.
- **Sitzung**—Tritt das Problem für jeden Benutzer auf? Wenn nicht, ist Ihr Problem möglicherweise auf sitzungs- oder browserbezogene Themen beschränkt.
- **Cache**—Ändert das Deaktivieren aller Caches irgendetwas? Wenn ja, können Sie sich auf zwischenspeicherbezogene Themen konzentrieren.
- **Datenbank**—Tritt das Problem in jeder Umgebung auf, in der der gleiche Code ausgeführt wird? Wenn nicht, suchen Sie nach Problemen in der Konfiguration und anderen datenbankbezogenen Themen.
- **Code**—Suchen Sie nach Code-Problemen, wenn keiner der oben genannten Probleme das Problem gelöst hat.

### Schritt 2: Auswahl durch Zusagen

Wenn das Problem zwischen jetzt und vor zwei Monaten begann, setzen Sie den Code zurück auf vor zwei Monaten. Überprüfen Sie, ob das Problem weiterhin besteht. Gehen Sie einen Monat weiter. Tritt das Problem dort auf? Wenn nicht, gehen Sie zwei Wochen weiter. Tritt es jetzt auf? Geh eine Woche zurück. Noch da? Gehen Sie vier Tage zurück. Irgendwann ist nur noch ein Commit übrig, der wahrscheinlich Code enthält, der mit dem Problem in Verbindung steht. Ihre Hauptursache ist nun wahrscheinlich auf die Dateien beschränkt, die in diesem Commit bearbeitet werden.

Sie können Wochen und Tage durch Commits ersetzen. Beispiel: Rollback von 100 Commits, forward 50, forward 25, back 12.

### Schritt 3: Von Dateien auswählen

- Teilen Sie Adobe Commerce nach Dateitypen (Core und Nicht-Core) auf. Deaktivieren Sie zunächst alle Kunden- und Marketplace-Module. Gibt es das Problem noch? Es handelt sich höchstwahrscheinlich um ein Nicht-Kernproblem.
- Aktivieren Sie (ungefähr) die Hälfte der Module erneut im `app/etc/config.php` -Datei. Beachten Sie Abhängigkeiten. Es ist am besten, Modul-Cluster mit demselben Thema gleichzeitig zu aktivieren. Gibt es das Problem noch?
- Aktivieren Sie ein Viertel der verbleibenden Module. Gibt es das Problem noch? Deaktivieren Sie die Hälfte von dem, was Sie aktiviert haben. Diese Methode kann Ihnen dabei helfen, die Hauptursache in einem einzelnen Modul zu isolieren.

## Zeiteinsparungen

Abgesehen von den Fehlerbehebungsverfahren enthält dieser Abschnitt einige allgemeine Regeln, die Ihnen helfen, Zeit beim Debugging zu sparen.

### Daten begrenzen

Überlegen Sie, ob Sie den vollständigen Katalog oder alle Store-Ansichten benötigen, um das Problem zu replizieren. Sie können Indizierungsprobleme mit einem Datenbankklon beheben, bei dem Sie 95 % des Katalogs entfernt haben, bevor Sie mit dem Debugging beginnen. Diese Methode spart während der Indizierung viel Zeit. Erstellen Sie ein Duplikat der Client-Datenbank mit reduzierter Speicheranzahl und reduziertem Katalog. Dies kann abhängig vom zu debuggenden Bereich auch für andere Entitäten (z. B. Kunden) gelten.

### Weitere Informationen anfordern

Manchmal, ein leichter Schritt zu vergessen inmitten des gesamten Codes und technischen Arbeit: nach weiteren Informationen fragen. Vollbildaufnahmen, ein Video, ein Videokonferenzchat mit der Person, die das Problem identifiziert hat, Replikationsschritte, Fragen, ob andere scheinbar unwichtige Dinge um das problematische Ereignis herum passiert sind. Frag, was jemand erwartet hat. Ist das wirklich ein Fehler oder vielleicht nur ein Missverständnis darüber, wie der Code funktioniert?

### Sprache und Dolmetschen

Ist die Beschreibung des Problems klar? Sind Sie sicher, dass keine Begriffe oder Beschreibungen auf unterschiedliche Weise interpretiert werden können? Wenn ja, stellen Sie sicher, dass Sie über dasselbe sprechen.

### Internetsuche

Führen Sie eine Internet-Suche mit Begriffen aus dem Problem durch. Es besteht die Gefahr, dass jemand anderer bereits auf dasselbe Problem gestoßen ist. Durchsuchen Sie die [Adobe Commerce GitHub-Probleme](https://github.com/magento/magento2/issues).

### Pause machen

Wenn Sie ein Problem zu lange betrachten, kann es schwierig sein, eine Lösung zu finden. Leg deine Arbeit nieder und hole eine andere Aufgabe oder mache einen Spaziergang. Die Antwort kommt Ihnen vielleicht, wenn Sie das Problem für eine Weile vergessen.

## Instrumente

Die n98 magerun CLI Tools ([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2)) bietet nützliche Funktionen für die Arbeit mit Adobe Commerce über die Befehlszeile. Insbesondere diese Befehle:

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## Code-Snippets

Die folgenden Themen enthalten Code-Snippets, die zur Protokollierung oder Identifizierung von Problemen in Commerce-Projekten verwendet werden können.

### Überprüfen, ob eine XML-Datei von Commerce verwendet wird

Fügen Sie einen offensichtlichen Syntaxfehler in eine XML-Datei ein, um zu sehen, ob sie verwendet wird. Öffnen Sie ein Tag und schließen Sie es beispielsweise nicht:

```xml
<?xml version="1.0"?>
<test
```

Wenn diese Datei verwendet wird, erzeugt sie einen Fehler. Ist dies nicht der Fall, wird Ihr Modul möglicherweise nicht verwendet oder zum Beispiel nicht aktiviert, oder die XML-Datei befindet sich möglicherweise am falschen Speicherort.

### Protokollierung

>[!BEGINTABS]

>[!TAB Adobe Commerce]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB Monolog]

```php
$log = new \Monolog\Logger('custom', [new \Monolog\Handler\StreamHandler(BP.'/var/log/test.log')]);
$log->info('Your Logging Message', ['context' => ['email' => 'john@example.com']]);
```

>[!TAB Zend]

```php
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/test.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info('Your text message');
$logger->info(print_r($yourArray, true));
```

>[!ENDTABS]

### Protokollierung auf niedriger Ebene

Zwei Beispiele, die immer in jeder PHP-Datei funktionieren:

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

Und für eine Stapelablaufverfolgung:

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
