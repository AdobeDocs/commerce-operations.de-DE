---
title: Konfigurieren von Valley für Sitzungsspeicher
description: Erfahren Sie, wie Sie Valkey für die Sitzungsspeicherung in Adobe Commerce konfigurieren. Erfahren Sie mehr über die Einrichtung von CLI, Sitzungsparameter und Techniken zur Verbindungsprüfung.
feature: Configuration, Cache
exl-id: 986ddb5c-8fc5-4210-8a41-a29e3a7625b7
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
autotag-review: '2026-06-22T21:59:49.664Z'
TQID: 'https://experienceleague.adobe.com/Cc9-5afIU1qJ0-4gxtUWo4tRFPtTMD3l1uzpyNBX7p0'
product_v2: id: b974b164-8a4e-43b8-a9e2-8e67ec131677id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 976
ht-degree: 1%

---


# Konfigurieren von Valley für Sitzungsspeicher

{{cloud-cache-config}}

Commerce bietet Befehlszeilenoptionen zum Konfigurieren des Valkey-Sitzungsspeichers. Obwohl Sie den Sitzungsspeicher durch Bearbeiten der `<Commerce-install-dir>/app/etc/env.php`-Datei konfigurieren können, ist die Verwendung der Befehlszeile die empfohlene Methode, insbesondere für anfängliche Konfigurationen. Die Befehlszeile stellt eine Validierung bereit, um sicherzustellen, dass die Konfiguration syntaktisch korrekt ist.

>[!IMPORTANT]
>
>Bevor Sie den Sitzungsspeicher konfigurieren können, müssen Sie &quot;[&quot; ](config-valkey.md#install-valkey).

## Valley-Sitzungsspeicher konfigurieren

Führen Sie den Befehl `setup:config:set` aus und geben Sie valley-spezifische Parameter an.

```shell
bin/magento setup:config:set --session-save=valkey --session-save-valkey-<parameter_name>=<parameter_value>...
```

- `--session-save=valkey` ermöglicht die Speicherung von Valkey-Sitzungen. Wenn diese Funktion bereits aktiviert ist, lassen Sie diesen Parameter weg.

- `--session-save-valkey-<parameter_name>=<parameter_value>` ist eine Liste von Parameter/Wert-Paaren, die den Sitzungsspeicher konfigurieren:

>[!NOTE]
>
>Ab **Adobe Commerce 2.4.9-alpha2** hat **Valkey** Redis im CLI-Tool aufgrund von Änderungen in der Lizenzierung offiziell ersetzt. Valkey ist eine Abspaltung von Redis und verfügt über nahezu identische Funktionen. Für **Versionen 2.4.8 und früher** bleiben die zur Konfiguration von Valkey verwendeten CLI-Befehle die gleichen wie für Redis, wodurch eine nahtlose Abwärtskompatibilität gewährleistet und die Migration oder Unterstützung von zwei Umgebungen vereinfacht wird. Das folgende Beispiel zeigt den valley-spezifischen Befehl.

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

| Befehlszeilenparameter | Parametername | Bedeutung | Standardwert |
|----------------------------------------------|--- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| session-save-valkey-host | Host | Vollqualifizierter Hostname, IP-Adresse oder absoluter Pfad bei Verwendung von UNIX-Sockets. | localhost |
| session-save-valkey-port | Port | Lauschender Port des Valley-Servers | 6379 |
| session-save-valkey-password | Passwort | Gibt ein Kennwort an, wenn der Valley-Server eine Authentifizierung erfordert. | leer |
| session-save-valkey-timeout | Zeitüberschreitung | Verbindungs-Timeout, in Sekunden. | 2,5 |
| session-save-valkey-persistent-id | persistent_identifier | Eindeutige Zeichenfolge zur Aktivierung persistenter Verbindungen (z. B. sess-db0).<br>[Bekannte Probleme mit phpredis und php-fpm](https://github.com/phpredis/phpredis/issues/70). |  |
| session-save-valkey-db | Datenbank | Eindeutige Valkey-Datenbanknummer, die zum Schutz vor Datenverlust empfohlen wird.<br><br>**Wichtig**: Wenn Sie Valkey für mehr als einen Caching-Typ verwenden, müssen die Datenbanknummern unterschiedlich sein. Es wird empfohlen, `0` die standardmäßige Caching-Datenbanknummer, `1` die Seitencaching-Datenbanknummer und `2` die Sitzungsspeicher-Datenbanknummer zuzuweisen. | 0 |
| session-save-value-compression-threshold | compression_threshold | Auf `0` setzen, um die Komprimierung zu deaktivieren (wird bei der `suhosin.session.encrypt = On` empfohlen). | 2048 |
| session-save-valkey-compression-lib | compression_library | Optionen: gzip, lzf, lz4 oder snappy. | gzip |
| session-save-valkey-log-level | log_level | Legen Sie eine der folgenden Einstellungen fest, die in der Reihenfolge von der letzten Ausführlichkeit bis zur letzten Ausführlichkeit aufgeführt sind:<ul><li>0 (Notfall: nur die schwerwiegendsten Fehler)<li>1 (Warnhinweis: sofortiges Handeln erforderlich)<li>2 (Kritisch: Anwendungskomponente nicht verfügbar)<li>3 (Fehler: Laufzeitfehler, nicht kritisch, aber zu überwachen)<li>4 (Warnung: zusätzliche Informationen, empfohlen)<li>5 (Hinweis: Normaler, aber signifikanter Zustand)<li>6 (INFO: Informationsnachrichten)<li>7 (Debugging: Die meisten Informationen nur für Entwicklung oder Tests)</ul> | 1 |
| session-save-valkey-max-concurrency | max_concurrency | Maximale Anzahl von Prozessen, die auf eine Sperre einer Sitzung warten können. Setzen Sie dies bei großen Produktions-Clustern auf mindestens 10% der Anzahl der PHP-Prozesse. | 6 |
| session-save-valkey-break-after-frontend | break_after_frontend | Anzahl der Sekunden, die gewartet werden soll, bevor versucht wird, die Sperre für die Frontend-Sitzung (d. h. Storefront) aufzuheben. | 5 |
| session-save-valkey-break-after-adminhtml | break_after_adminhtml | Anzahl der Sekunden, die gewartet werden soll, bevor versucht wird, die Sperre für eine Admin-HTML-Sitzung (d. h. Admin-Sitzung) aufzuheben. | 30 |
| session-save-valkey-first-lifetime | first_lifeTime | Die Lebensdauer der Sitzung für Nicht-Bots beim ersten Schreiben in Sekunden oder `0` zum Deaktivieren verwenden. | 600 |
| session-save-valkey-bot-first-lifetime | bot_first_lifeTime | Die Lebensdauer der Sitzung für Bots beim ersten Schreiben in Sekunden oder `0` zum Deaktivieren. | 60 |
| session-save-valkey-bot-lifetime | bot_lifeTime | Die Lebensdauer der Sitzung für Bots bei nachfolgenden Schreibvorgängen in Sekunden oder `0` zum Deaktivieren. | 7200 |
| session-save-valkey-disable-locked | disable_locking | Deaktivieren Sie die Sitzungssperre vollständig. | 0 (falsch) |
| session-save-valkey-min-lifetime | min_lifeTime | Mindestlebensdauer der Sitzung in Sekunden. | 60 |
| session-save-valkey-max-lifetime | max_lifeTime | Maximale Sitzungslebensdauer in Sekunden. | 2592000 (720 Stunden) |
| session-save-valkey-sentinel-master | sentinel_master | Master-Name des Wächtertals. | leer |
| session-save-valkey-sentinel-servers | sentinel_servers | Liste der Valley-Sentinel-Server, durch Kommata getrennt. | leer |
| session-save-valkey-sentinel-verify-master | sentinel_verify_master | Status-Flag „Valley Sentinel Master“ überprüfen. | 0 (falsch) |
| session-save-valkey-sentinel-connect-retry | sentinel_connect_retries | Verbindungsversuche für Wächter. | 5 |

## Beispiel

Im folgenden Beispiel wird Valkey als Sitzungsdatenspeicher, der Host als `127.0.0.1`, die Protokollebene als `4` und die Datenbanknummer als `2` festgelegt. Alle anderen Parameter sind auf den Standardwert eingestellt.

```shell
bin/magento setup:config:set --session-save=valkey --session-save-valkey-host=127.0.0.1 --session-save-valkey-log-level=4 --session-save-valkey-db=2
```

>[!NOTE]
>
>Ab **Adobe Commerce 2.4.9** hat **Valkey** Redis im CLI-Tool aufgrund von Änderungen bei der Lizenzierung offiziell ersetzt. Valkey ist eine Abspaltung von Redis und verfügt über nahezu identische Funktionen. Für **Versionen 2.4.8 und früher** bleiben die zur Konfiguration von Valkey verwendeten CLI-Befehle die gleichen wie für Redis, wodurch eine nahtlose Abwärtskompatibilität gewährleistet und die Migration oder Unterstützung von zwei Umgebungen vereinfacht wird. Das folgende Beispiel zeigt den valley-spezifischen Befehl.

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Ergebnis

Commerce fügt Zeilen ähnlich den folgenden zu `<magento_root>app/etc/env.php` hinzu:

```php
'session' => [
    'save' => 'valkey',
    'redis' => [
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
        'max_lifetime' => '2592000',
    ],
],
```

>[!INFO]
>
>Die TTL für Sitzungseinträge verwendet den Wert für „Cookie-Lebensdauer“, der in der Admin konfiguriert wird. Wenn Cookie Lifetime auf `0` gesetzt ist (der Standardwert ist `3600`), laufen Valkey-Sitzungen in der in min_lifeTime angegebenen Anzahl von Sekunden ab (der Standardwert ist `60`). Diese Diskrepanz ist auf Unterschiede in der Interpretation des Lebenszeitwerts von `0` durch Valkey- und Sitzungs-Cookies zurückzuführen. Wenn dieses Verhalten nicht gewünscht ist, erhöhen Sie den Wert von min_lifeTime.

## Valley-Verbindung überprüfen

Um sicherzustellen, dass Valkey und Commerce ordnungsgemäß zusammenarbeiten, melden Sie sich bei dem Server an, auf dem Valkey ausgeführt wird, öffnen Sie ein Terminal und verwenden Sie entweder den Befehl `valkey-cli monitor` oder den Befehl `redis-cli ping`.

### Valley-Überwachungsbefehl

```shell
valkey-cli monitor
```

Beispielausgabe für Sitzungsspeicher:

```text
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Valley-Ping-Befehl

```shell
valkey-cli ping
```

Die erwartete Antwort lautet: `PONG`.

Wenn beide Befehle erfolgreich waren, ist Valkey richtig eingerichtet.

### Überprüfen komprimierter Daten

Um komprimierte Sitzungsdaten und den Seitencache zu überprüfen, unterstützt [RESP.app](https://flathub.org/apps/app.resp.RESP) die automatische Dekomprimierung von Commerce 2-Sitzungs- und Seitencache und zeigt PHP-Sitzungsdaten in einem für Menschen lesbaren Format an.
