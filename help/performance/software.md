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
* Eine separate Redis-Instanz als Ihren [Standard-Cache](../configuration/cache/redis-pg-cache.md) (verwenden Sie diese Instanz nicht für Seiten-Cache)

Informationen zu unterstützten Versionen der einzelnen Softwaretypen finden Sie unter [Systemanforderungen](../installation/system-requirements.md) .

## Betriebssystem

Betriebssystemkonfigurationen und -optimierungen sind für [!DNL Commerce] im Vergleich zu anderen Webanwendungen mit hoher Auslastung ähnlich. Je mehr gleichzeitige Verbindungen vom Server verarbeitet werden, desto mehr verfügbare Sockets können vollständig zugeordnet werden. Der Linux-Kernel unterstützt einen Mechanismus zur &quot;Wiederverwendung&quot; von TCP-Verbindungen. Um diesen Mechanismus zu aktivieren, legen Sie den folgenden Wert in `/etc/sysctl.conf` fest:

>[!INFO]
>
>Die Aktivierung von net.ipv4.tcp_tw_reuse hat keine Auswirkungen auf eingehende Verbindungen.

```text
net.ipv4.tcp_tw_reuse = 1
```

Der Kernel-Parameter `net.core.somaxconn` steuert die maximale Anzahl von offenen Sockets, die auf Verbindungen warten. Dieser Wert kann sicher auf 1024 erhöht werden, sollte jedoch mit der Fähigkeit des Servers korreliert werden, diesen Betrag zu verarbeiten. Um diesen Kernel-Parameter zu aktivieren, legen Sie den folgenden Wert in `/etc/sysctl.conf` fest:

```text
net.core.somaxconn = 1024
```

## PHP

Magento unterstützt vollständig PHP 7.3 und 7.4. Es gibt mehrere Faktoren, die bei der Konfiguration von PHP berücksichtigt werden müssen, um maximale Geschwindigkeit und Effizienz bei der Anforderungsverarbeitung zu erreichen.

### PHP-Erweiterungen

Es wird empfohlen, die Liste der aktiven PHP-Erweiterungen auf diejenigen zu beschränken, die für die Funktion [!DNL Commerce] erforderlich sind.

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
>`php-mcrypt` wurde aus PHP 7.2 entfernt und durch die [`sodium` Bibliothek](https://www.php.net/manual/en/book.sodium.php) ersetzt. Stellen Sie sicher, dass [Natrium](https://www.php.net/manual/en/sodium.installation.php) beim Aktualisieren von PHP ordnungsgemäß aktiviert ist.

>[!INFO]
>
>Das Vorhandensein von Profiling- und Debugging-Erweiterungen kann sich negativ auf die Reaktionszeit Ihrer Seiten auswirken. Beispielsweise kann ein aktives xDebug-Modul ohne Debug-Sitzung die Seitenreaktionszeit um bis zu 30 % erhöhen.

### PHP-Einstellungen

Um eine erfolgreiche Ausführung aller [!DNL Commerce] -Instanzen ohne Daten- oder Code-Dumping auf die Festplatte zu gewährleisten, legen Sie die Speicherbegrenzung wie folgt fest:

```text
memory_limit=1G
```

Erhöhen Sie zum Debugging diesen Wert auf 2G.

#### Realpath_cache-Konfiguration

Um die Leistung von [!DNL Commerce] zu verbessern, fügen Sie die folgenden empfohlenen `realpath_cache`-Einstellungen in der Datei `php.ini` hinzu oder aktualisieren Sie sie. Diese Konfiguration ermöglicht es PHP-Prozessen, Pfade zu Dateien zwischenzuspeichern, anstatt sie bei jedem Laden einer Seite zu suchen. Siehe [Leistungsoptimierung](https://www.php.net/manual/en/ini.core.php) in der PHP-Dokumentation.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Um die maximale Geschwindigkeit von [!DNL Commerce] auf PHP 7 zu erreichen, müssen Sie das OpCache-Modul aktivieren und es ordnungsgemäß konfigurieren. Diese Einstellungen werden für das Modul empfohlen:

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

Es wird empfohlen, die [PHP APCu-Erweiterung](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) und die [Konfiguration `composer` zu aktivieren, um sie zu unterstützen](../performance/deployment-flow.md#preprocess-dependency-injection-instructions), um die maximale Leistung zu optimieren. Diese Erweiterung speichert Dateispeicherorte für geöffnete Dateien zwischen, wodurch die Leistung für [!DNL Commerce] -Server-Aufrufe, einschließlich Seiten, Ajax-Aufrufe und Endpunkte, erhöht wird.

Bearbeiten Sie Ihre `apcu.ini` -Datei, um Folgendes einzuschließen:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Webserver

Magento unterstützt vollständig die Nginx- und Apache-Webserver. [!DNL Commerce] enthält empfohlene Beispielkonfigurationsdateien in den Dateien `<magento_home>/nginx.conf.sample` (Nginx) und `<magento_home>.htaccess.sample` (Apache).  Das Nginx-Beispiel enthält Einstellungen für eine bessere Leistung und ist so konzipiert, dass nur wenig Neukonfiguration erforderlich ist. Zu den wichtigsten in der Beispieldatei definierten Best Practices für die Konfiguration gehören:

* Einstellungen zum Zwischenspeichern von statischen Inhalten in einem Browser
* Speicher- und Ausführungszeiteinstellungen für PHP
* Einstellungen zur Inhaltskomprimierung

Sie sollten auch die Anzahl der Threads für die Verarbeitung von Eingabeanfragen konfigurieren, wie unten aufgeführt:

| Webserver | Attributname | Standort | Verwandte Informationen |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Tuning NGINX for Performance](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache-Leistungsoptimierung](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Gemeinsame Apache MPM-Richtlinien](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Dieses Dokument enthält keine detaillierten [!DNL MySQL]-Tuning-Anweisungen, da jeder Store und jede Umgebung unterschiedlich sind. Wir können jedoch einige allgemeine Empfehlungen abgeben.

Es wurden viele Verbesserungen an [!DNL MySQL] 5.7.9 vorgenommen. Wir sind überzeugt, dass [!DNL MySQL] mit guten Standardeinstellungen verteilt ist. Die wichtigsten Einstellungen sind:

| Parameter | Standard | Beschreibung |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | Der Standardwert ist auf 8 gesetzt, um Probleme mit mehreren Threads zu vermeiden, die versuchen, auf dieselbe Instanz zuzugreifen. |
| `innodb_buffer_pool_size` | 128 MB | In Kombination mit den oben beschriebenen mehreren Poolinstanzen bedeutet dies eine standardmäßige Speicherzuweisung von 1024 MB. Die Gesamtgröße wird auf alle Pufferpools aufgeteilt. Geben Sie für optimale Effizienz eine Kombination aus `innodb_buffer_pool_instances` und `innodb_buffer_pool_size` an, sodass jede Pufferpool-Instanz mindestens 1 GB beträgt. |
| `max_connections` | 150 | Der Wert des Parameters `max_connections` sollte mit der Gesamtzahl der im Anwendungsserver konfigurierten PHP-Threads korrelieren. Eine allgemeine Empfehlung wäre 300 für eine kleine und 1 000 für eine mittlere Umwelt. |
| `innodb_thread_concurrency` | 0 | Der beste Wert für diese Konfiguration sollte anhand der Formel berechnet werden: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento empfiehlt dringend, [!DNL Varnish] als vollständigen Seiten-Cache-Server für Ihren Store zu verwenden. Das PageCache-Modul ist weiterhin in der Codebase vorhanden, sollte jedoch nur zu Entwicklungszwecken verwendet werden. Sie sollte nicht zusammen mit oder anstelle von [!DNL Varnish] verwendet werden.

Installieren Sie [!DNL Varnish] auf einem separaten Server vor der Webstufe. Es sollte alle eingehenden Anfragen akzeptieren und zwischengespeicherte Seitenkopien bereitstellen. Damit [!DNL Varnish] effektiv mit gesicherten Seiten funktioniert, kann ein SSL-Terminierungsproxy vor [!DNL Varnish] platziert werden. Zu diesem Zweck kann Nginx verwendet werden.

[!DNL Commerce] verteilt eine Beispielkonfigurationsdatei für [!DNL Varnish] (Versionen 4 und 5), die alle empfohlenen Leistungseinstellungen enthält. Zu den wichtigsten Leistungsmerkmalen zählen:

* **Die Backend-Konsistenzprüfung** fragt den [!DNL Commerce] -Server ab, um festzustellen, ob er zeitnah reagiert.
* Mit dem **Übergangmodus** können Sie [!DNL Varnish] anweisen, ein Objekt über den TTL-Zeitraum (Time to Live) hinaus im Cache zu belassen und diesen veralteten Inhalt bereitzustellen, wenn [!DNL Commerce] nicht gesund ist oder wenn noch kein neuer Inhalt abgerufen wurde.
* **Der SAINT-Modus** blackt ungesunde [!DNL Commerce] Server für einen konfigurierbaren Zeitraum auf. Daher können ungesunde Backends keinen Traffic bereitstellen, wenn [!DNL Varnish] als Lastenausgleich verwendet wird.

Weitere Informationen zur Implementierung dieser Funktionen finden Sie unter [Erweiterte Konfiguration [!DNL Varnish] 2} .](../configuration/cache/config-varnish-advanced.md)

### Optimieren der Asset-Leistung

Im Allgemeinen empfehlen wir, Ihre Assets (Bilder, JS, CSS usw.) in einem CDN zu speichern, um eine optimale Leistung zu erzielen.

Wenn Ihre Site nicht die Bereitstellung einer großen Anzahl von Gebietsschemas erfordert und sich Ihre Server in derselben Region wie die Mehrheit Ihrer Kunden befinden, können Sie erhebliche Leistungsgewinne zu geringeren Kosten feststellen, indem Sie Ihre Assets in [!DNL Varnish] speichern, anstatt ein CDN zu verwenden.

Um Ihre Assets in [!DNL Varnish] zu speichern, fügen Sie die folgenden VCL-Einträge in Ihrer `default.vcl` -Datei hinzu, die von [!DNL Commerce] für [!DNL Varnish] 5 generiert wurde.

Fügen Sie am Ende der `if` -Anweisung für PURGE-Anforderungen in der `vcl_recv`-UnterRoutine Folgendes hinzu:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

Suchen Sie in der UnterRoutine `vcl_backend_response` nach der Anweisung `if` , mit der das Cookie für `GET` - oder `HEAD` -Anforderungen aufgehoben wird.
Der aktualisierte `if` -Block sollte wie folgt aussehen:

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

Starten Sie den [!DNL Varnish] -Server neu, um zwischengespeicherte Assets beim Aktualisieren Ihrer Site oder Bereitstellen/Aktualisieren von Assets zu leeren.

## Caching- und Sitzungsserver

Magento bietet eine Reihe von Optionen zum Speichern des Caches und der Sitzungsdaten, einschließlich Redis, Memcache, Dateisystem und Datenbank. Einige dieser Optionen werden nachfolgend beschrieben.

### Einrichtung eines einzelnen Webknotens

Wenn Sie Ihren gesamten Traffic mit nur einem Webknoten bedienen möchten, ist es nicht sinnvoll, Ihren Cache auf einen Remote-Redis-Server zu legen. Verwenden Sie stattdessen entweder das Dateisystem oder einen lokalen Redis-Server. Wenn Sie das Dateisystem verwenden möchten, platzieren Sie Ihre Cache-Ordner auf einem auf einem RAM-Dateisystem bereitgestellten Volume. Wenn Sie einen lokalen Redis-Server verwenden möchten, empfehlen wir dringend, Redis so zu konfigurieren, dass es Sockets für direkte Verbindungen verwendet, anstatt Daten über HTTP auszutauschen.

### Einrichtung mehrerer Webknoten

Bei einer Einrichtung mehrerer Webknoten ist Redis die beste Option. Da [!DNL Commerce] viele Daten aktiv zwischenspeichert, um eine bessere Leistung zu erzielen, achten Sie auf Ihren Netzwerkkanal zwischen den Webknoten und dem Redis-Server. Sie möchten nicht, dass der Kanal zu einem Engpass bei der Anforderungsverarbeitung wird.

>[!INFO]
>
>Wenn Sie Hunderte und Tausende gleichzeitiger Anfragen bedienen müssen, benötigen Sie möglicherweise einen Kanal von bis zu 1 Gbit (oder sogar mehr) zum Redis-Server.
