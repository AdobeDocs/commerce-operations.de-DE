---
title: Software Recommendations
description: Überprüfen Sie eine Liste der empfohlenen Software im Zusammenhang mit der optimalen Leistung von Adobe Commerce-Implementierungen.
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# Software-Empfehlungen

Wir benötigen die folgende Software für Produktionsinstanzen von [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx und [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] oder OpenSearch](../installation/prerequisites/search-engine/overview.md)

Bei Multi-Server-Bereitstellungen oder bei Händlern, die eine Skalierung ihres Geschäfts planen, empfehlen wir Folgendes:

* [[!DNL Varnish] cache](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) für Sitzungen (ab 2.0.6)
* Eine separate Rediv-Instanz als [Standardcache](../configuration/cache/redis-pg-cache.md) (Verwenden Sie diese Instanz nicht für Seiten-Cache)

Siehe [Systemanforderungen](../installation/system-requirements.md) für Informationen zu unterstützten Versionen der einzelnen Softwaretypen.

## Betriebssystem

Betriebssystemkonfigurationen und -optimierungen sind für [!DNL Commerce] im Vergleich zu anderen Hochlade-Webanwendungen. Je mehr gleichzeitige Verbindungen vom Server verarbeitet werden, desto mehr verfügbare Sockets können vollständig zugeordnet werden. Der Linux-Kernel unterstützt einen Mechanismus zur &quot;Wiederverwendung&quot; von TCP-Verbindungen. Um diesen Mechanismus zu aktivieren, legen Sie den folgenden Wert in `/etc/sysctl.conf`:

>[!INFO]
>
>Die Aktivierung von net.ipv4.tcp_tw_reuse hat keine Auswirkungen auf eingehende Verbindungen.

```text
net.ipv4.tcp_tw_reuse = 1
```

Der Kernel-Parameter `net.core.somaxconn` steuert die maximale Anzahl offener Sockets, die auf Verbindungen warten. Dieser Wert kann sicher auf 1024 erhöht werden, sollte jedoch mit der Fähigkeit des Servers korreliert werden, diesen Betrag zu verarbeiten. Um diesen Kernel-Parameter zu aktivieren, legen Sie den folgenden Wert in `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Magento unterstützt vollständig PHP 7.3 und 7.4. Es gibt mehrere Faktoren, die bei der Konfiguration von PHP berücksichtigt werden müssen, um maximale Geschwindigkeit und Effizienz bei der Anforderungsverarbeitung zu erreichen.

### PHP-Erweiterungen

Es wird empfohlen, die Liste der aktiven PHP-Erweiterungen auf die für [!DNL Commerce] Funktionalität.

Magento Open Source und Adobe Commerce:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* ext-sockets
* ext-natrium
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Darüber hinaus erfordert Adobe Commerce Folgendes:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* ext-sockets
* ext-natrium
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Das Hinzufügen weiterer Erweiterungen verlängert die Ladezeiten von Bibliotheken.

>[!INFO]
>
>`php-mcrypt` wurde aus PHP 7.2 entfernt und durch die [`sodium` Bibliothek](https://www.php.net/manual/en/book.sodium.php). Stellen Sie sicher, dass [Natrium](https://www.php.net/manual/en/sodium.installation.php) richtig aktiviert ist, wenn PHP aktualisiert wird.

>[!INFO]
>
>Das Vorhandensein von Profiling- und Debugging-Erweiterungen kann sich negativ auf die Reaktionszeit Ihrer Seiten auswirken. Beispielsweise kann ein aktives xDebug-Modul ohne Debug-Sitzung die Seitenreaktionszeit um bis zu 30 % erhöhen.

### PHP-Einstellungen

Gewährleistung der erfolgreichen Ausführung aller [!DNL Commerce] Instanzen ohne Daten- oder Code-Dumping auf die Festplatte zu laden, legen Sie die Speicherbegrenzung wie folgt fest:

```text
memory_limit=1G
```

Erhöhen Sie zum Debugging diesen Wert auf 2G.

#### Realpath_cache-Konfiguration

Verbesserung [!DNL Commerce] Leistung, Hinzufügen oder Aktualisieren der folgenden empfohlenen `realpath_cache` -Einstellungen in `php.ini` -Datei. Diese Konfiguration ermöglicht es PHP-Prozessen, Pfade zu Dateien zwischenzuspeichern, anstatt sie bei jedem Laden einer Seite zu suchen. Siehe [Leistungsoptimierung](https://www.php.net/manual/en/ini.core.php) in der PHP-Dokumentation.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

So erhalten Sie die maximale Geschwindigkeit von [!DNL Commerce] auf PHP 7 müssen Sie das OpCache-Modul aktivieren und es ordnungsgemäß konfigurieren. Diese Einstellungen werden für das Modul empfohlen:

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Berücksichtigen Sie bei der Feinabstimmung der Speicherzuordnung für opcache die Größe der Magento-Codebasis und all Ihre Erweiterungen. Das Magento-Leistungsteam verwendet die Werte aus dem obigen Beispiel zum Testen, da es genügend Platz in opcache für die durchschnittliche Anzahl der installierten Erweiterungen bereitstellt.

Wenn Sie über einen Computer mit geringem Arbeitsspeicher verfügen und nicht viele Erweiterungen oder Anpassungen installiert sind, verwenden Sie die folgenden Einstellungen, um ein ähnliches Ergebnis zu erhalten:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Es wird empfohlen, [PHP APCu-Erweiterung](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) und [configuring `composer` Unterstützung](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) zur Optimierung der maximalen Leistung. Diese Erweiterung speichert Dateispeicherorte für geöffnete Dateien zwischen, wodurch die Leistung für [!DNL Commerce] Server-Aufrufe, einschließlich Seiten, Ajax-Aufrufe und Endpunkte.

Bearbeiten Sie Ihre `apcu.ini` -Datei, die Folgendes enthalten soll:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Webserver

Magento unterstützt vollständig die Nginx- und Apache-Webserver. [!DNL Commerce] bietet Beispieldateien für empfohlene Konfigurationsdateien im  `<magento_home>/nginx.conf.sample` Nginx und  `<magento_home>.htaccess.sample` (Apache).  Das Nginx-Beispiel enthält Einstellungen für eine bessere Leistung und ist so konzipiert, dass nur wenig Neukonfiguration erforderlich ist. Zu den wichtigsten in der Beispieldatei definierten Best Practices für die Konfiguration gehören:

* Einstellungen zum Zwischenspeichern von statischen Inhalten in einem Browser
* Speicher- und Ausführungszeiteinstellungen für PHP
* Einstellungen zur Inhaltskomprimierung

Sie sollten auch die Anzahl der Threads für die Verarbeitung von Eingabeanfragen konfigurieren, wie unten aufgeführt:

| Webserver | Attributname | Standort | Verwandte Informationen |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Optimierung von NGINX für Leistung](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache-Leistungsoptimierung](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Gemeinsame Richtlinien für Apache MPM](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Dieses Dokument bietet keine eingehende [!DNL MySQL] Anweisungen anpassen, da jeder Store und jede Umgebung unterschiedlich sind, aber wir können einige allgemeine Empfehlungen abgeben.

Es wurden viele Verbesserungen an [!DNL MySQL] 5.7.9 Wir sind zuversichtlich, dass [!DNL MySQL] ist mit guten Standardeinstellungen verteilt. Die wichtigsten Einstellungen sind:

| Parameter | Standard | Beschreibung |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | Der Standardwert ist auf 8 gesetzt, um Probleme mit mehreren Threads zu vermeiden, die versuchen, auf dieselbe Instanz zuzugreifen. |
| `innodb_buffer_pool_size` | 128 MB | In Kombination mit den oben beschriebenen mehreren Poolinstanzen bedeutet dies eine standardmäßige Speicherzuweisung von 1024 MB. Die Gesamtgröße wird auf alle Pufferpools aufgeteilt. Geben Sie für eine optimale Effizienz eine Kombination aus `innodb_buffer_pool_instances` und `innodb_buffer_pool_size` sodass jede Pufferpool-Instanz mindestens 1 GB beträgt. |
| `max_connections` | 150 | Der Wert der `max_connections` sollte mit der Gesamtanzahl der im Anwendungsserver konfigurierten PHP-Threads korrelieren. Eine allgemeine Empfehlung wäre 300 für eine kleine und 1 000 für eine mittlere Umwelt. |
| `innodb_thread_concurrency` | 0 | Der beste Wert für diese Konfiguration sollte anhand der Formel berechnet werden: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento empfiehlt dringend, [!DNL Varnish] als vollständigen Seiten-Cache-Server für Ihren Store. Das PageCache-Modul ist weiterhin in der Codebase vorhanden, sollte jedoch nur zu Entwicklungszwecken verwendet werden. Es sollte nicht zusammen mit oder anstelle von verwendet werden. [!DNL Varnish].

Installieren [!DNL Varnish] auf einem separaten Server vor der Webstufe. Es sollte alle eingehenden Anfragen akzeptieren und zwischengespeicherte Seitenkopien bereitstellen. In [!DNL Varnish] um effektiv mit gesicherten Seiten zu arbeiten, kann ein SSL-Terminierungsproxy vor [!DNL Varnish]. Zu diesem Zweck kann Nginx verwendet werden.

[!DNL Commerce] verteilt eine Beispielkonfigurationsdatei für [!DNL Varnish] (Versionen 4 und 5), die alle empfohlenen Leistungseinstellungen enthält. Zu den wichtigsten Leistungsmerkmalen zählen:

* **Backend-Konsistenzprüfung** fragt die [!DNL Commerce] -Server, um zu bestimmen, ob er zeitnah reagiert.
* **Übergangmodus** ermöglicht es Ihnen, [!DNL Varnish] , um ein Objekt über den TTL-Zeitraum (Time to Live) hinaus im Cache zu belassen und diesen veralteten Inhalt bereitzustellen, wenn [!DNL Commerce] ist nicht gesund oder wenn frischer Inhalt noch nicht abgerufen wurde.
* **Saint-Modus** Blacklists ungesund [!DNL Commerce] -Server für einen konfigurierbaren Zeitraum. Ungesunde Backends können daher bei Verwendung von [!DNL Varnish] als Lastenausgleich.

Siehe [Erweitert [!DNL Varnish] Konfiguration](../configuration/cache/config-varnish-advanced.md) Weitere Informationen zur Implementierung dieser Funktionen.

### Optimieren der Asset-Leistung

Im Allgemeinen empfehlen wir, Ihre Assets (Bilder, JS, CSS usw.) in einem CDN zu speichern, um eine optimale Leistung zu erzielen.

Wenn Ihre Site nicht die Bereitstellung einer großen Anzahl von Gebietsschemas erfordert und sich Ihre Server in derselben Region befinden wie die Mehrheit Ihrer Kunden, können Sie durch die Speicherung Ihrer Assets in erhebliche Leistungssteigerungen zu geringeren Kosten feststellen [!DNL Varnish] anstatt ein CDN zu verwenden.

So speichern Sie Ihre Assets in [!DNL Varnish]Fügen Sie die folgenden VCL-Einträge in Ihrer `default.vcl` von [!DNL Commerce] für [!DNL Varnish] 5.

Am Ende des `if` Anweisung für PURGE-Anfragen in der `vcl_recv` unterroutinemäßig hinzufügen:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

Im `vcl_backend_response` untergeordnete Routine, suchen Sie nach der `if` -Anweisung, die das Cookie für `GET` oder `HEAD` -Anfragen.
Die aktualisierten `if` -Block sollte wie folgt aussehen:

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

Starten Sie den [!DNL Varnish] Server zum Leeren zwischengespeicherter Assets beim Aktualisieren Ihrer Site oder Bereitstellen/Aktualisieren von Assets.

## Caching- und Sitzungsserver

Magento bietet eine Reihe von Optionen zum Speichern des Caches und der Sitzungsdaten, einschließlich Redis, Memcache, Dateisystem und Datenbank. Einige dieser Optionen werden nachfolgend beschrieben.

### Einrichtung eines einzelnen Webknotens

Wenn Sie Ihren gesamten Traffic mit nur einem Webknoten bedienen möchten, ist es nicht sinnvoll, Ihren Cache auf einen Remote-Redis-Server zu legen. Verwenden Sie stattdessen entweder das Dateisystem oder einen lokalen Redis-Server. Wenn Sie das Dateisystem verwenden möchten, platzieren Sie Ihre Cache-Ordner auf einem auf einem RAM-Dateisystem bereitgestellten Volume. Wenn Sie einen lokalen Redis-Server verwenden möchten, empfehlen wir dringend, Redis so zu konfigurieren, dass es Sockets für direkte Verbindungen verwendet, anstatt Daten über HTTP auszutauschen.

### Einrichtung mehrerer Webknoten

Bei einer Einrichtung mehrerer Webknoten ist Redis die beste Option. weil [!DNL Commerce] speichert viele Daten aktiv zwischen, um die Leistung zu verbessern, achten Sie auf Ihren Netzwerkkanal zwischen den Webknoten und dem Redis-Server. Sie möchten nicht, dass der Kanal zu einem Engpass bei der Anforderungsverarbeitung wird.

>[!INFO]
>
>Wenn Sie Hunderte und Tausende gleichzeitiger Anfragen bedienen müssen, benötigen Sie möglicherweise einen Kanal von bis zu 1 Gbit (oder sogar mehr) zum Redis-Server.
