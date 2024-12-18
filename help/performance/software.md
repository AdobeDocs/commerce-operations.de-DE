---
title: Software Recommendations
description: Überprüfen Sie eine Liste mit empfohlener Software zur Optimierung der Leistung von Adobe Commerce-Bereitstellungen.
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# Software-Empfehlungen

Für Produktionsinstanzen von [!DNL Commerce] benötigen wir die folgende Software:

* [PHP](../installation/system-requirements.md)
* Nginx und [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] oder OpenSearch](../installation/prerequisites/search-engine/overview.md)

Für Multi-Server-Bereitstellungen oder für Händler, die eine Skalierung ihres Unternehmens planen, empfehlen wir Folgendes:

* [[!DNL Varnish]](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) für Sitzungen (ab 2.0.6+)
* Eine separate Redis-Instanz als [Standard-Cache](../configuration/cache/redis-pg-cache.md) (verwenden Sie diese Instanz nicht für den Seiten-Cache)

Unter [Systemanforderungen](../installation/system-requirements.md) finden Sie Informationen zu den unterstützten Versionen der einzelnen Softwaretypen.

## Betriebssystem

Betriebssystemkonfigurationen und -optimierungen sind für [!DNL Commerce] im Vergleich zu anderen Web-Anwendungen mit hoher Last ähnlich. Je mehr gleichzeitige Verbindungen vom Server verarbeitet werden, desto mehr Sockets kann die Anzahl der verfügbaren Sockets vollständig zugewiesen werden. Der Linux-Kernel unterstützt einen Mechanismus zum „Wiederverwenden“ von TCP-Verbindungen. Um diesen Mechanismus zu aktivieren, legen Sie den folgenden Wert in `/etc/sysctl.conf` fest:

>[!INFO]
>
>Die Aktivierung von net.ipv4.tcp_tw_reuse hat keine Auswirkungen auf eingehende Verbindungen.

```text
net.ipv4.tcp_tw_reuse = 1
```

Der Kernel-Parameter `net.core.somaxconn` steuert die maximale Anzahl offener Sockets, die auf Verbindungen warten. Dieser Wert kann sicher auf 1024 erhöht werden, sollte jedoch mit der Fähigkeit des Servers korreliert werden, diesen Betrag zu verarbeiten. Um diesen Kernelparameter zu aktivieren, setzen Sie den folgenden Wert in `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Magento unterstützt PHP 7.3 und 7.4 vollständig. Es gibt mehrere Faktoren, die bei der Konfiguration von PHP zu berücksichtigen sind, um maximale Geschwindigkeit und Effizienz bei der Verarbeitung von Anfragen zu erhalten.

### PHP-Erweiterungen

Es wird empfohlen, die Liste der aktiven PHP-Erweiterungen auf die zu beschränken, die für [!DNL Commerce] Funktionalität erforderlich sind.

Magento Open Source und Adobe Commerce:

* ext-bcmath
* ext-type
* ext-curl
* ext-dom
* ext-fileInfo
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
* ext-socket
* Ext-Natrium
* ext-tokenizer
* ext-xmlWriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Darüber hinaus erfordert Adobe Commerce Folgendes:

* ext-bcmath
* ext-type
* ext-curl
* ext-dom
* ext-fileInfo
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
* ext-socket
* Ext-Natrium
* ext-spl
* ext-tokenizer
* ext-xmlWriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Das Hinzufügen weiterer Erweiterungen erhöht die Ladezeiten von Bibliotheken.

>[!INFO]
>
>`php-mcrypt` wurde aus PHP 7.2 entfernt und durch die [`sodium`-Bibliothek ersetzt](https://www.php.net/manual/en/book.sodium.php). Stellen Sie sicher[ dass ](https://www.php.net/manual/en/sodium.installation.php)Natrium) beim Upgrade von PHP ordnungsgemäß aktiviert ist.

>[!INFO]
>
>Das Vorhandensein von Profiling- und Debugging-Erweiterungen kann sich negativ auf die Antwortzeit Ihrer Seiten auswirken. Beispielsweise kann ein aktives xDebug-Modul ohne Debugging-Sitzung die Antwortzeit der Seite um bis zu 30 % erhöhen.

### PHP-Einstellungen

Um eine erfolgreiche Ausführung aller [!DNL Commerce]-Instanzen zu gewährleisten, ohne Daten oder Code auf der Festplatte abzulegen, stellen Sie die Speicherbegrenzung wie folgt ein:

```text
memory_limit=1G
```

Erhöhen Sie zum Debuggen diesen Wert auf 2G.

#### RealPath_cache-Konfiguration

Um die [!DNL Commerce] zu verbessern, fügen Sie die folgenden empfohlenen `realpath_cache` in der `php.ini` hinzu oder aktualisieren Sie sie. Diese Konfiguration ermöglicht es PHP-Prozessen, Pfade zu Dateien zwischenzuspeichern, anstatt sie bei jedem Laden einer Seite zu suchen. Siehe [Leistungsoptimierung](https://www.php.net/manual/en/ini.core.php) in der PHP-Dokumentation.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### Byte-Code

Um die maximale Geschwindigkeit von [!DNL Commerce] auf PHP 7 zu erreichen, müssen Sie das OpCache-Modul aktivieren und ordnungsgemäß konfigurieren. Diese Einstellungen werden für das Modul empfohlen:

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Berücksichtigen Sie bei der Feinabstimmung der Speicherzuweisung für Opcache die Größe der Magento-Codebasis und all Ihrer Erweiterungen. Das Leistungsteam der Magento verwendet die Werte im vorherigen Beispiel zum Testen, da es im Opcache ausreichend Platz für die durchschnittliche Anzahl installierter Erweiterungen bietet.

Wenn Sie einen Computer mit wenig Arbeitsspeicher haben und nicht viele Erweiterungen oder Anpassungen installiert sind, verwenden Sie die folgenden Einstellungen, um ein ähnliches Ergebnis zu erzielen:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Es wird empfohlen, die [PHP APCu-Erweiterung](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) zu aktivieren und [`composer` zu konfigurieren, um sie zu unterstützen](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) um die maximale Leistung zu optimieren. Diese Erweiterung speichert Dateispeicherorte für geöffnete Dateien zwischen, was die Leistung für [!DNL Commerce] Server-Aufrufe wie Seiten, Ajax-Aufrufe und Endpunkte erhöht.

Bearbeiten Sie die `apcu.ini` Datei so, dass sie Folgendes enthält:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Webserver

Magento unterstützt vollständig die Nginx- und Apache-Webserver. [!DNL Commerce] enthält Beispiele für empfohlene Konfigurationsdateien in den `<magento_home>/nginx.conf.sample`-Dateien (Nginx) und `<magento_home>.htaccess.sample`-Dateien (Apache).  Das Nginx-Beispiel enthält Einstellungen für eine bessere Leistung und ist so konzipiert, dass nur wenige Neukonfigurationen erforderlich sind. Zu den wichtigsten Best Practices für die Konfiguration, die in der Beispieldatei definiert sind, gehören:

* Einstellungen für das Caching statischer Inhalte in einem Browser
* Speicher- und Ausführungszeiteinstellungen für PHP
* Einstellungen zur Inhaltskomprimierung

Sie sollten auch die Anzahl der Threads für die Verarbeitung von Eingabeanfragen konfigurieren, wie unten aufgeführt:

| Webserver | Attributname | Speicherort | Verwandte Informationen |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Optimieren von NGINX für Leistung](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache-Leistungsoptimierung](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Apache MPM - Allgemeine Anweisungen](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Dieses Dokument enthält keine detaillierten [!DNL MySQL], da jeder Store und jede Umgebung unterschiedlich sind. Wir können jedoch einige allgemeine Empfehlungen geben.

Es wurden viele Verbesserungen an [!DNL MySQL] 5.7.9 vorgenommen. Wir sind zuversichtlich, dass [!DNL MySQL] mit guten Standardeinstellungen verteilt wird. Die wichtigsten Einstellungen sind:

| Parameter | Standard | Beschreibung |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | Der Standardwert ist 8, um Probleme mit mehreren Threads zu vermeiden, die auf dieselbe Instanz zugreifen möchten. |
| `innodb_buffer_pool_size` | 128 MB | In Kombination mit den oben beschriebenen mehreren Pool-Instanzen bedeutet dies eine standardmäßige Speicherzuweisung von 1024 MB. Die Gesamtgröße wird auf alle Pufferpools aufgeteilt. Um eine optimale Effizienz zu erzielen, geben Sie eine Kombination aus `innodb_buffer_pool_instances` und `innodb_buffer_pool_size` an, sodass jede Pufferpoolinstanz mindestens 1 GB beträgt. |
| `max_connections` | 150 | Der Wert des `max_connections` sollte mit der Gesamtzahl der PHP-Threads korrelieren, die im Anwendungs-Server konfiguriert sind. Eine allgemeine Empfehlung wäre 300 für eine kleine und 1.000 für eine mittlere Umgebung. |
| `innodb_thread_concurrency` | 0 | Der beste Wert für diese Konfiguration sollte anhand der folgenden Formel berechnet werden: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento empfiehlt dringend, [!DNL Varnish] als Seiten-Cache-Server für Ihren Store zu verwenden. Das PageCache-Modul ist weiterhin in der Codebasis vorhanden, sollte jedoch nur zu Entwicklungszwecken verwendet werden. Es sollte nicht zusammen mit oder anstelle von [!DNL Varnish] verwendet werden.

Installieren Sie [!DNL Varnish] auf einem separaten Server vor der Web-Stufe. Er sollte alle eingehenden Anfragen akzeptieren und zwischengespeicherte Seitenkopien bereitstellen. Damit [!DNL Varnish] effektiv mit gesicherten Seiten arbeiten können, kann ein SSL-Terminations-Proxy vor [!DNL Varnish] platziert werden. Hierfür kann Nginx verwendet werden.

[!DNL Commerce] verteilt eine Beispielkonfigurationsdatei für [!DNL Varnish] (Versionen 4 und 5), die alle empfohlenen Leistungseinstellungen enthält. Zu den wichtigsten Leistungskriterien zählen:

* **Backend-Konsistenzprüfung** fragt den [!DNL Commerce]-Server ab, ob er zeitnah reagiert.
* **Gnadenmodus** ermöglicht es Ihnen, [!DNL Varnish] anzuweisen, ein Objekt über seine Time-to-Live (TTL)-Periode hinaus im Cache zu halten und diesen veralteten Inhalt bereitzustellen, wenn [!DNL Commerce] nicht in Ordnung ist oder noch kein neuer Inhalt abgerufen wurde.
* **Saint-Modus** sperrt für einen konfigurierbaren Zeitraum die Liste der fehlerhaften [!DNL Commerce]-Server. Daher können ungesunde Backends bei der Verwendung von [!DNL Varnish] als Lastenausgleich keinen Traffic bereitstellen.

Siehe [Erweitert [!DNL Varnish] Konfiguration](../configuration/cache/config-varnish-advanced.md) für weitere Informationen zur Implementierung dieser Funktionen.

### Asset-Leistung optimieren

Im Allgemeinen empfehlen wir, Ihre Assets (Bilder, JS, CSS usw.) in einem CDN zu speichern, um eine optimale Leistung zu erzielen.

Wenn für Ihre Site keine große Anzahl von Gebietsschemata bereitgestellt werden muss und sich Ihre Server in derselben Region wie die meisten Ihrer Kunden befinden, können Sie zu niedrigeren Kosten erhebliche Leistungsgewinne erzielen, indem Sie Ihre Assets in [!DNL Varnish] speichern, anstatt ein CDN zu verwenden.

Um Ihre Assets in [!DNL Varnish] zu speichern, fügen Sie die folgenden VCL-Einträge in Ihrer von [!DNL Commerce] für [!DNL Varnish] 5 generierten `default.vcl` hinzu.

Fügen Sie am Ende der `if` für PURGE-Anfragen in der `vcl_recv`-Unterroutine Folgendes hinzu:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

Suchen Sie in der `vcl_backend_response`-Unterroutine nach der `if`-Anweisung, die das Cookie für `GET`- oder `HEAD`-Anfragen aufhebt.
Der aktualisierte `if` sollte wie folgt aussehen:

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

Starten Sie den [!DNL Varnish]-Server neu, um zwischengespeicherte Assets zu leeren, sobald Sie Ihre Site aktualisieren oder Assets bereitstellen/aktualisieren.

## Caching und Sitzungsserver

Magento bietet eine Reihe von Optionen zum Speichern Ihrer Cache- und Sitzungsdaten, einschließlich Redis, Memcache, Dateisystem und Datenbank. Einige dieser Optionen werden im Folgenden erläutert.

### Einrichtung eines einzelnen Web-Knotens

Wenn Sie Ihren gesamten Traffic mit nur einem Webknoten bedienen möchten, ist es nicht sinnvoll, Ihren Cache auf einen Remote-Redis-Server zu legen. Verwenden Sie stattdessen entweder das Dateisystem oder einen lokalen Redis-Server. Wenn Sie das Dateisystem verwenden möchten, legen Sie Ihre Cache-Ordner auf ein Volume, das in einem RAM-Dateisystem gemountet ist, ab. Wenn Sie einen lokalen Redis-Server verwenden möchten, empfehlen wir dringend, Redis so zu konfigurieren, dass Sockets für direkte Verbindungen verwendet werden, anstatt Daten über HTTP auszutauschen.

### Einrichtung mehrerer Web-Knoten

Für die Einrichtung mehrerer Web-Knoten ist Redis die beste Option. Da [!DNL Commerce] viele Daten aktiv zwischenspeichert, um eine bessere Leistung zu erzielen, achten Sie auf Ihren Netzwerkkanal zwischen den Web-Knoten und dem Redis-Server. Sie möchten nicht, dass der Kanal zu einem Engpass bei der Anfrageverarbeitung wird.

>[!INFO]
>
>Wenn Sie Hunderte und Tausende von Anfragen gleichzeitig bearbeiten müssen, benötigen Sie möglicherweise einen Kanal von bis zu 1 Gbit (oder sogar mehr) zu Ihrem Redis-Server.
