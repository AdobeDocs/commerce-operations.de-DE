---
title: Best Practices für das Debugging
description: Erfahren Sie mehr über Verfahren zum Beheben häufiger Adobe Commerce-Entwicklungsprobleme.
feature: Best Practices
role: Developer
exl-id: 78fbea7b-28e8-4713-990d-b4cae159250c
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# Best Practices für das Debugging von Adobe Commerce

In diesem Abschnitt werden Möglichkeiten zum systematischen und effektiven Debuggen des Adobe Commerce-Frameworks erläutert. Ziel ist es, Ihnen zu helfen, die Wurzel eines Problems schnell zu finden und die Untersuchungszeit zu minimieren.

## Fehlerbehebung: Übliche Verdächtige

In diesem Abschnitt werden die häufigsten Probleme beschrieben, auf die Sie während der Entwicklung stoßen können.

### Cache

- Leeren Sie den Cache, bevor Sie weitere Untersuchungen durchführen
- Betrachten Sie den APC-Cache, das CDN, den Lack, den generierten Code sowie die `var/view_preprocessed`- und `pub/static/`
- Warteschlangen-Handler anhalten und neu starten, nachdem der Cache geleert oder der Code geändert wurde

Das folgende Codebeispiel enthält hilfreiche Befehle im Zusammenhang mit der Verwaltung des Caches (nicht in Produktionsumgebungen ausführen):

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

### Indizierte Daten

Alles neu indizieren, wenn das Problem möglicherweise indexbezogen ist. Das Debugging indizierter Daten erfolgt normalerweise in Nicht-Produktionsumgebungen. In Produktionsumgebungen sollten Sie den Ursprung der Indexfehlausrichtung untersuchen, bevor Sie die Neuindizierung durchführen. Die Merkmale des fehlerhaften Zustands können Ihnen etwas über die Ursache des Problems verraten.

### Komponist

Möglicherweise ist der Code aufgrund einer Verzweigungsänderung oder aufgrund von Kerndateien, die im Rahmen eines vorherigen Debuggens bearbeitet wurden, veraltet. Um potenzielle Probleme zu vermeiden, führen Sie die folgenden Befehle aus:

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### Erzeugter Inhalt

Erstellen Sie Frontend-Dateien neu, bevor Sie den generierten Inhalt in JS, CSS, Bildern, Übersetzungen und anderen Dateien debuggen.

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### Entwicklermodus

Stellen Sie sicher, dass sich Ihre lokale Installation im `developer` befindet.

### Neues Modul

Wenn Sie ein Modul erstellt haben, überprüfen Sie die folgenden Probleme:

- Ist das Modul aktiviert?

  ```bash
  bin/magento module --enable Your_Module
  ```

  Überprüfen Sie die `app/etc/config.php` für Ihr neues Modul.

- Überprüfen Sie die Verschachtelung der Datei- und Verzeichnisstruktur. Befinden sich beispielsweise Layout-Dateien im Verzeichnis `view/layout/` anstelle des Verzeichnisses `view/frontend/layout`? Befinden sich Vorlagen im `view/frontend/template`-Verzeichnis statt im `view/frontend/templates`-Verzeichnis?

## Fehlerbehebung: Halbzerlegung

Wenn die üblichen Verdächtigen keine Lösung für das Problem anbieten, besteht die schnellste Möglichkeit darin, das Problem halbzuteilen (oder zu halbieren). Mit dieser Methode eliminieren Sie große Blöcke und teilen, was übrig bleibt, um die Grundursache zu finden, anstatt den Code linear zu durchlaufen.

Siehe die folgenden Diagramme:

![Halbierungsdiagramm](../../../assets/playbooks/bisect.png)

![Halbierungsdiagramm](../../../assets/playbooks/bisect2.png)

Es gibt mehrere Ansätze zum Halbieren, aber Adobe empfiehlt, diese Reihenfolge zu befolgen:

- Nach Thema teilen
- Durch Commits halbieren
- Nach Dateien teilen

### Schritt 1: Nach Thema teilen

Wenn das Problem möglicherweise nicht Code-bezogen ist, beseitigen Sie zuerst die großen Blöcke. Zu den großen Textbausteinen, die zu berücksichtigen sind, gehören:

- **Adobe Commerce-Framework** - Bezieht sich das Problem überhaupt auf Adobe Commerce oder könnte es auf ein anderes verbundenes System zurückzuführen sein?
- **Server und Client** - Löschen Sie den Browsercache und den Speicher. Ist das Problem gelöst? Dies könnte eine Server-bedingte Ursache ausschließen. Gibt es das Problem noch? Sie müssen keine Zeit mehr mit dem Browser-Debugging verschwenden.
- **Sitzung** - Tritt das Problem bei jedem Benutzer auf? Andernfalls kann sich das Problem auf sitzungs- oder browserbezogene Themen beschränken.
- **Cache** - Ändert sich durch die Deaktivierung aller Caches etwas? Wenn ja, können Sie sich auf Themen im Zusammenhang mit dem Cache konzentrieren.
- **Datenbank**: Tritt das Problem in jeder Umgebung auf, in der derselbe Code ausgeführt wird? Suchen Sie andernfalls nach Problemen in der Konfiguration und anderen datenbankbezogenen Themen.
- **Code** - Suchen Sie nach Code-Problemen, wenn keines der oben genannten Probleme behoben wurde.

### Schritt 2: Durch Commits teilen

Wenn das Problem zwischen jetzt und vor zwei Monaten aufgetreten ist, setzen Sie den Code auf vor zwei Monaten zurück. Überprüfen Sie, ob das Problem weiterhin besteht. Einen Monat später. Tritt das Problem dort auf? Wenn nicht, zwei Wochen vorgehen. Kommt es jetzt vor? Geh eine Woche zurück. Immer noch da? Geh vier Tage zurück. An irgendeinem Punkt ist nur noch ein Commit übrig, der wahrscheinlich Code enthält, der mit dem Problem zusammenhängt. Ihre Grundursache ist jetzt wahrscheinlich auf die Dateien beschränkt, die in diesem Commit bearbeitet wurden.

Sie können Wochen und Tage durch Commits ersetzen. Beispiel: Zurücksetzen auf 100 Commits, Vorwärts 50, Vorwärts 25, Rückwärts 12.

### Schritt 3: Nach Dateien teilen

- Unterteilen Sie Adobe Commerce nach Dateitypen (Kern und Nicht-Kern). Deaktivieren Sie zunächst alle Kunden- und Marketplace-Module. Gibt es das Problem noch? Es handelt sich höchstwahrscheinlich um ein Problem, das nicht zum Kern gehört.
- Aktivieren Sie (grob) die Hälfte der Module wieder in der `app/etc/config.php`. sich der Abhängigkeiten bewusst sein. Es wird empfohlen, Modulcluster mit demselben Thema gleichzeitig zu aktivieren. Gibt es das Problem noch?
- Aktivieren Sie ein Viertel der verbleibenden Module. Gibt es das Problem noch? Deaktivieren Sie die Hälfte der aktivierten Elemente. Mit dieser Methode können Sie die Grundursache in einem einzelnen Modul isolieren.

## Zeiteinsparung

Neben den Techniken zur Fehlerbehebung finden Sie in diesem Abschnitt einige allgemeine Regeln, die Ihnen helfen, beim Debuggen Zeit zu sparen.

### Daten begrenzen

Erwägen, ob Sie den vollständigen Katalog oder alle Store-Ansichten benötigen, um das Problem zu replizieren. Sie können Indizierungsprobleme mit einem Datenbankklon beheben, bei dem Sie 95 % des Katalogs entfernt haben, bevor Sie mit dem Debugging beginnen. Diese Methode spart bei Indizierungsvorgängen viel Zeit. Erstellen Sie ein Duplikat der Client-Datenbank mit reduzierter Speicheranzahl und reduziertem Katalog. Dies kann je nach dem Bereich, den Sie debuggen, auch für andere Entitäten (z. B. Kunden) gelten.

### Weitere Informationen anfordern

Manchmal ein einfacher Schritt, um inmitten all des Codes und der technischen Arbeit zu vergessen: Fragen Sie nach mehr Informationen. Im Vollbildmodus werden Folgendes erfasst: ein Video, eine Videokonferenz, ein Chat mit der Person, die das Problem identifiziert hat, Replikationsschritte und Fragen dazu, ob andere scheinbar unwichtige Dinge im Zusammenhang mit dem problematischen Ereignis passiert sind. Fragen Sie, was jemand erwartet hat. Ist das wirklich ein Bug oder vielleicht nur ein Missverständnis der Art, wie der Code funktioniert?

### Sprache und Dolmetschen

Ist die Beschreibung des Problems klar? Sind Sie sicher, dass keine Begriffe oder Beschreibungen auf verschiedene Weise interpretiert werden können? Wenn ja, stellen Sie sicher, dass Sie über dieselbe Sache sprechen.

### Internetsuche

Führen Sie eine Internet-Suche mit Begriffen im Zusammenhang mit dem Problem durch. Wahrscheinlich ist bereits jemand anderes auf dasselbe Problem gestoßen. Durchsuchen Sie die [Adobe Commerce GitHub-Probleme](https://github.com/magento/magento2/issues).

### Mach eine Pause

Wenn Sie ein Problem zu lange betrachten, kann es schwierig sein, eine Lösung zu finden. Setze deine Arbeit nieder und nimm eine andere Aufgabe auf oder mache einen Spaziergang. Die Antwort könnte kommen, wenn Sie das Problem für eine Weile vergessen haben.

## Tools

Die n98 magerun CLI-Tools ([https://github.com/netz98/n98-magerun2](https://github.com/netz98/n98-magerun2)) bieten nützliche Funktionen für die Arbeit mit Adobe Commerce über die Befehlszeile. Insbesondere diese Befehle:

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## Codeausschnitte

Die folgenden Themen enthalten Codeausschnitte, mit denen Probleme in Commerce-Projekten protokolliert oder identifiziert werden können.

### Überprüfen, ob eine XML-Datei von Commerce verwendet wird

Fügen Sie in einer XML-Datei einen offensichtlichen Syntaxfehler hinzu, um zu sehen, ob er verwendet wird. Öffnen Sie ein Tag und schließen Sie es nicht, zum Beispiel:

```xml
<?xml version="1.0"?>
<test
```

Wenn diese Datei verwendet wird, wird ein Fehler generiert. Ist dies nicht der Fall, wird das Modul möglicherweise nicht verwendet oder nicht aktiviert, oder die XML-Datei befindet sich am falschen Speicherort.

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

Und für eine Stacktrace:

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
