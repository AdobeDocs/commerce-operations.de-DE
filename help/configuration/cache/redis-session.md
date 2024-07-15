---
title: Verwenden von Redizes für die Sitzungsspeicherung
description: Erfahren Sie, wie Sie Redis für die Sitzungsspeicherung konfigurieren.
feature: Configuration, Cache
exl-id: f93f500d-65b0-4788-96ab-f1c3d2d40a38
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 1%

---

# Verwenden von Redizes für die Sitzungsspeicherung

>[!IMPORTANT]
>
>Sie müssen [Redis](config-redis.md#install-redis) installieren, bevor Sie fortfahren.


Commerce bietet jetzt Befehlszeilenoptionen zum Konfigurieren des Sitzungsspeichers für Redis. In früheren Versionen haben Sie die Datei &quot;`<Commerce install dir>app/etc/env.php`&quot; bearbeitet. Die Befehlszeile bietet eine Validierung und ist die empfohlene Konfigurationsmethode, Sie können jedoch die Datei &quot;`env.php`&quot;weiterhin bearbeiten.

Führen Sie den Befehl `setup:config:set` aus und geben Sie Redis-spezifische Parameter an.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

where

`--session-save=redis` aktiviert die Speicherung der Redis-Sitzung. Wenn diese Funktion bereits aktiviert wurde, lassen Sie diesen Parameter weg.

`--session-save-redis-<parameter_name>=<parameter_value>` ist eine Liste von Parameter-/Wertpaaren, die die Sitzungsspeicherung konfigurieren:

| Befehlszeilenparameter | Parametername | Bedeutung | Standardwert |
|--- |--- |--- |--- |
| session-save-redis-host | Host | Vollständig qualifizierter Hostname, IP-Adresse oder absoluter Pfad bei Verwendung von UNIX-Sockets. | localhost |
| session-save-reds-port | port | Redis Server-Überwachungsanschluss. | 6379 |
| session-save-redis-password | password | Gibt ein Kennwort an, wenn für Ihren Redis-Server eine Authentifizierung erforderlich ist. | leer |
| session-save-redis-timeout | timeout | Zeitüberschreitung der Verbindung in Sekunden. | 2,5 |
| session-save-redis-persistent-id | persistent_identifier | Eindeutige Zeichenfolge zum Aktivieren persistenter Verbindungen (z. B. sess-db0).<br>[Bekannte Probleme mit phpredis und php-fpm](https://github.com/phpredis/phpredis/issues/70). |
| session-save-redis-db | Datenbank | Eindeutige Redis-Datenbanknummer, die zum Schutz vor Datenverlust empfohlen wird.<br><br>**Wichtig**: Wenn Sie Redis für mehr als einen Typ von Zwischenspeicherung verwenden, müssen die Datenbanknummern unterschiedlich sein. Es wird empfohlen, die standardmäßige Caching-Datenbanknummer auf 0, die Datenbank-Nummer für die Seitenspeicherung auf 1 und die Datenbanknummer für die Sitzungsspeicherung auf 2 zuzuweisen. | 0 |
| session-save-redis-compression-threshold | compression_threshold | Auf 0 setzen, um die Komprimierung zu deaktivieren (empfohlen bei `suhosin.session.encrypt = On`).<br>[Bekanntes Problem mit Zeichenfolgen von mehr als 64 KB](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18). | 2048 |
| session-save-redis-compression-lib | compression_library | Optionen: gzip, lzf, lz4 oder snappy. | gzip |
| session-save-redis-log-level | log_level | Legen Sie einen der folgenden Werte fest, die in der Reihenfolge von &quot;am wenigsten ausführlich&quot;bis &quot;am ausführlichsten&quot;aufgeführt sind:<ul><li>0 (Notfall: nur die schwersten Fehler)<li>1 (Warnhinweis: sofortiges Handeln erforderlich)<li>2 (kritisch: Anwendungskomponente nicht verfügbar)<li>3 (Fehler: Laufzeitfehler, nicht kritisch, sondern muss überwacht werden)<li>4 (Warnung: zusätzliche Informationen, empfohlen)<li>5 (Hinweis: normal, aber signifikant)<li>6 (Info: Informationsmeldungen)<li>7 (debug: die meisten Informationen nur für Entwicklung oder Tests)</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | Maximale Anzahl von Prozessen, die auf eine Sperrung für eine Sitzung warten können. Setzen Sie dies bei großen Produktionsclustern auf mindestens 10 % der Anzahl an PHP-Prozessen. | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | Anzahl der Sekunden, die gewartet werden muss, bevor versucht wird, die Sperre für die Frontend-Sitzung (d. h. Storefront) zu unterbrechen. | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | Anzahl der Sekunden, die gewartet werden muss, bevor versucht wird, die Sperre für eine Admin-Sitzung zu unterbrechen (d. h. Admin-Sitzung). | 30 |
| session-save-redis-first-lifetime | first_lifetime | Lebensdauer (in Sekunden) der Sitzung für Nicht-Bots beim ersten Schreiben oder verwenden Sie 0 zur Deaktivierung. | 600 |
| session-save-redis-bot-first-lifetime | bot_first_lifetime | Lebensdauer (in Sekunden) der Sitzung für Bots beim ersten Schreiben oder verwenden Sie 0 zur Deaktivierung. | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | Lebensdauer (in Sekunden) der Sitzung für Bots bei nachfolgenden Schreibvorgängen oder verwenden Sie 0 zur Deaktivierung. | 7200 |
| session-save-redis-disable-locking | disable_locking | Die Sitzungssperrung kann vollständig deaktiviert werden. | 0 (false) |
| session-save-redis-min-lifetime | min_lifetime | Mindestdauer der Sitzung in Sekunden. | 60 |
| session-save-redis-max-lifetime | max_lifetime | Maximale Sitzungslebensdauer in Sekunden. | 2592000 (720 Stunden) |
| session-save-redis-sentinel-master | sentinel_master | Redis Sentinel Master Name | leer |
| session-save-redis-sentinel-servers | sentinel_servers | Liste der Sentinel-Server von Redis, durch Kommas getrennt | leer |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | Überprüfung des Master-Statusmarkierungen von Redis Sentinel | 0 (false) |
| session-save-redis-sentinel-connect-retries | sentinel_connect_retries | Verbindungsversuche für Sentinels | 5 |

## Beispiel

Im folgenden Beispiel wird Redis als Sitzungsdatenspeicher festgelegt, der Host auf `127.0.0.1` gesetzt, die Protokollebene auf 4 festgelegt und die Datenbanknummer auf 2 festgelegt. Alle anderen Parameter werden auf den Standardwert gesetzt.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Ergebnis

Commerce fügt Zeilen ähnlich den folgenden zu `<magento_root>app/etc/env.php` hinzu:

```php
    'session' =>
    array (
      'save' => 'redis',
      'redis' =>
      array (
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000'
      )
    ),
```

>[!INFO]
>
>TTL für Sitzungsdatensätze verwendet den Wert für Cookie-Lebensdauer, der in Admin konfiguriert ist. Wenn die Cookie-Lebensdauer auf 0 festgelegt ist (der Standardwert ist 3600), laufen Redis-Sitzungen mit der in min_lifetime angegebenen Anzahl von Sekunden ab (der Standardwert ist 60). Diese Diskrepanz beruht auf Unterschieden in der Interpretation von Redis und Sitzungs-Cookies für einen Lebenszeitwert von 0. Wenn dieses Verhalten nicht gewünscht wird, erhöhen Sie den Wert von min_lifetime.

## Rediv-Verbindung überprüfen

Um sicherzustellen, dass Redis und Commerce zusammenarbeiten, melden Sie sich bei dem Server an, auf dem Redis ausgeführt wird, öffnen Sie ein Terminal und verwenden Sie den Befehl Redis Monitor oder den Ping-Befehl.

### Redis Monitor, Befehl

```bash
redis-cli monitor
```

Beispielausgabe für die Sitzungsspeicherung:

```terminal
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Redis, Ping, Befehl

```bash
redis-cli ping
```

`PONG` sollte die Antwort sein.

Wenn beide Befehle erfolgreich waren, wird Redis ordnungsgemäß eingerichtet.

### Überprüfen komprimierter Daten

Um komprimierte Sitzungsdaten und Seiten-Cache zu untersuchen, unterstützt [RESP.app](https://flathub.org/apps/details/app.resp.RESP) die automatische Dekomprimierung des Commerce 2-Sitzungs- und Seiten-Caches und zeigt PHP-Sitzungsdaten in einer für Menschen lesbaren Form an.
