---
title: Empfehlungen zur Leistungsoptimierung
description: Optimieren Sie die Leistung Ihrer Adobe Commerce-Implementierung, indem Sie diese Empfehlungen befolgen.
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
feature: Cloud
topic: Performance
source-git-commit: 8b09d734d8ac4490cd88af5673acd0a41b6cdf66
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 0%

---


# Leistungsoptimierungsprüfung

Auch wenn die Leistungsoptimierung aus vielen Aspekten hervorgehen kann, gibt es einige allgemeine Empfehlungen, die für die meisten Szenarien berücksichtigt werden sollten. Zu den allgemeinen Empfehlungen gehören die Konfigurationsoptimierung für Infrastrukturelemente, die Adobe Commerce-Backend-Konfiguration und die Planung der Architekturskalierbarkeit.

>[!TIP]
>
>Siehe [_Handbuch zu Best Practices für die Leistung_](../../../performance/overview.md) für weitere Informationen zur Leistungsoptimierung.

## Infrastruktur

In den folgenden Abschnitten werden Empfehlungen für die Optimierung der Infrastruktur beschrieben.

### DNS-Suchen

Bei der DNS-Suche wird ermittelt, zu welcher IP-Adresse der Domänenname gehört. Der Browser muss warten, bis die DNS-Suche abgeschlossen ist, bevor er irgendetwas für jede Anfrage herunterladen kann. Die Reduzierung der DNS-Suchen ist wichtig, um die Seitenladezeiten zu verbessern.

### CDN (Content Delivery Network)

Verwenden Sie ein CDN zur Optimierung der Leistung beim Herunterladen von Assets. Adobe Commerce verwendet Fastly. Wenn Sie über eine lokale Implementierung von Adobe Commerce verfügen, sollten Sie auch erwägen, eine CDN-Ebene hinzuzufügen.

### Weblatenz

Der Speicherort des Rechenzentrums wirkt sich auf die Weblatenz für Frontend-Benutzer aus.

### Netzwerkbandbreite

Eine ausreichende Netzwerkbandbreite ist eine der wichtigsten Anforderungen für den Datenaustausch zwischen Webknoten, Datenbanken, Caching-/Sitzungsservern und anderen Diensten.

Da Adobe Commerce Caching effektiv für hohe Leistung nutzt, kann Ihr System Daten aktiv mit Caching-Servern wie Redis austauschen. Wenn Redis auf einem Remote-Server installiert ist, müssen Sie einen ausreichenden Netzwerkkanal zwischen Webknoten und dem Caching-Server bereitstellen, um Engpässe bei Lese-/Schreibvorgängen zu vermeiden.

### Betriebssystem

Betriebssystemkonfigurationen und -optimierungen sind für Adobe Commerce im Vergleich zu anderen Webanwendungen mit hoher Auslastung ähnlich. Je mehr gleichzeitige Verbindungen vom Server verarbeitet werden, desto mehr verfügbare Sockets können vollständig zugeordnet werden.

### CPU der Webknoten

Ein CPU-Kern kann etwa 2 bis 4 Adobe Commerce-Anforderungen ohne Cache effektiv bedienen. Verwenden Sie die folgende Gleichung, um zu bestimmen, wie viele Webknoten/Kerne zur Verarbeitung aller eingehenden Anforderungen benötigt werden, ohne sie in die Warteschlange zu stellen:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### PHP-FPM-Einstellungen

Die Optimierung dieser Einstellungen hängt von den Ergebnissen der Leistungstests für verschiedene Projekte ab.

- **ByteCode**—Um die maximale Geschwindigkeit von Adobe Commerce auf PHP 7 zu erhalten, müssen Sie die `opcache` und konfigurieren Sie es ordnungsgemäß.

- **APCU**—Adobe empfiehlt, die PHP APCu-Erweiterung zu aktivieren und den Composer zu konfigurieren, um die maximale Leistung zu optimieren. Diese Erweiterung speichert Dateispeicherorte für geöffnete Dateien zwischen, wodurch die Leistung für Adobe Commerce-Server-Aufrufe, einschließlich Seiten, Ajax-Aufrufe und Endpunkte, erhöht wird.

- **Realpath_cacheconfiguration**—Optimierung `realpath_cache` ermöglicht es PHP-Prozessen, Pfade zu Dateien zwischenzuspeichern, anstatt sie jedes Mal zu suchen, wenn eine Seite geladen wird.

### Webserver

Für die Verwendung von nginx als Webserver ist nur eine geringfügige Neukonfiguration erforderlich. Der nginx-Webserver bietet eine bessere Leistung und ist einfach zu konfigurieren, indem die Beispielkonfigurationsdatei aus Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- PHP-FPM ordnungsgemäß mit TCP einrichten

- Aktivieren von HTTP/2 und Gzip

- Optimieren von Worker-Verbindungen

### Datenbank

Dieses Dokument enthält keine detaillierten MySQL-Tuning-Anweisungen, da jeder Speicher und jede Umgebung unterschiedlich sind. Adobe kann jedoch allgemeine Empfehlungen abgeben.

Die Adobe Commerce-Datenbank (und jede andere Datenbank) ist abhängig von der Speichermenge, die zum Speichern von Daten und Indizes verfügbar ist. Um die MySQL-Datenindizierung effektiv zu nutzen, sollte die verfügbare Speicherkapazität mindestens der Hälfte der in der Datenbank gespeicherten Daten entsprechen.

Optimieren Sie die `innodb_buffer_pool_instances` -Einstellung, um Probleme mit mehreren Threads zu vermeiden, die versuchen, auf dieselbe Instanz zuzugreifen. Der Wert der `max_connections` sollte mit der Gesamtanzahl der im Anwendungsserver konfigurierten PHP-Threads korrelieren. Verwenden Sie die folgende Formel, um den besten Wert für `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Sitzungszwischenspeicherung

Sitzungs-Caching ist ein guter Kandidat, um eine separate Instanz von Redis zu konfigurieren. Bei der Speicherkonfiguration für diesen Cache-Typ sollte die Strategie des Warenkorbabbruchs der Site berücksichtigt werden und wie lange eine Sitzung voraussichtlich im Cache verbleiben wird.

Für Redis sollte ausreichend Speicher zur Verfügung stehen, damit alle anderen Caches im Speicher gespeichert werden können, um eine optimale Leistung zu erzielen. Der Block-Cache ist der Schlüsselfaktor bei der Bestimmung des Speicherbedarfs, der konfiguriert werden muss. Der Block-Cache wächst relativ zur Anzahl der Seiten auf einer Site (Anzahl der SKU x Anzahl der Store-Ansichten).

### Seiten-Zwischenspeicherung

Adobe empfiehlt dringend die Verwendung von Varnish für den vollständigen Seiten-Cache in Ihrem Adobe Commerce-Store. Die `PageCache` -Modul ist weiterhin in der Codebase vorhanden, sollte jedoch nur zu Entwicklungszwecken verwendet werden.

Installieren Sie Varnish auf einem separaten Server vor der Webstufe. Es sollte alle eingehenden Anfragen akzeptieren und zwischengespeicherte Seitenkopien bereitstellen. Damit Varnish mit gesicherten Seiten effektiv arbeiten kann, kann ein SSL-Terminierungsproxy vor Varnish platziert werden. Zu diesem Zweck kann Nginx verwendet werden.

Obwohl die Invalidierung des gesamten Varnish-Cache-Speichers effektiv ist, empfiehlt Adobe, Varnish genügend Arbeitsspeicher zuzuweisen, um die beliebtesten Seiten im Arbeitsspeicher zu speichern.

### Nachrichtenwarteschlangen

Das Message Queue Framework (MQF) ist ein System, mit dem ein Modul Nachrichten in Warteschlangen veröffentlichen kann. Außerdem werden die Verbraucher definiert, die die Nachrichten asynchron empfangen. Adobe Commerce unterstützt [!DNL RabbitMQ] als Messaging Broker, der eine skalierbare Plattform für den Versand und Empfang von Nachrichten bietet.

### Leistungstests und -überwachung

Leistungstests vor jeder Produktionsversion werden immer empfohlen, um eine Schätzung der Funktionen Ihrer E-Commerce-Plattform zu erhalten. Behalten Sie die Überwachung nach dem Start bei und verfügen Sie über einen Skalierbarkeits- und Sicherungsplan für die Verarbeitung von Spitzenzeiten.

>[!NOTE]
>
> Adobe Commerce in der Cloud-Infrastruktur wendet bereits die oben genannten Optimierungen an Infrastruktur und Architektur an, mit Ausnahme der DNS-Suche, da sie außerhalb des Anwendungsbereichs liegt.

### Suche {#search-heading}

Elasticsearch (oder OpenSearch) ist ab Adobe Commerce-Version 2.4 erforderlich, es ist jedoch auch eine Best Practice, es für Versionen vor 2.4 zu aktivieren.

## Betriebssystem

Neben den bereits erwähnten Empfehlungen zur Optimierung der gemeinsamen Infrastruktur gibt es auch Ansätze zur Leistungsverbesserung für bestimmte Geschäftsmodi und Skalierungen. Dieses Dokument enthält keine detaillierten Tuning-Anweisungen für alle, da die einzelnen Szenarien unterschiedlich sind. Adobe kann jedoch einige allgemeine Optionen für Ihre Referenz bereitstellen.

### Headless-Architektur

Es gibt einen separaten Abschnitt für [Headless](../../architecture/enterprise-blueprint.md#headless-storefront). Zusammenfassend wird die Storefront-Schicht von der Plattform selbst getrennt. Es ist immer noch dasselbe Backend, aber Adobe Commerce verarbeitet Anforderungen nicht mehr direkt und unterstützt stattdessen nur benutzerdefinierte Storefronts über die GraphQL-API.

### Adobe Commerce aktualisieren

Adobe Commerce bietet immer eine bessere Leistung bei der Ausführung der neuesten Version. Auch wenn es nicht möglich ist, Adobe Commerce nach jeder neuen Version auf dem neuesten Stand zu halten, wird dennoch empfohlen, [Upgrade](../../../upgrade/overview.md) wenn Adobe Commerce erhebliche Leistungsoptimierungen einführt.

Beispielsweise veröffentlichte Adobe 2020 eine Optimierung für die Redis-Ebene, mit der viele Ineffizienzen, Verbindungsprobleme und unnötige Datenübertragungen zwischen Redis und Adobe Commerce behoben wurden. Die Gesamtleistung zwischen 2.3 und 2.4 ist Nacht und Tag und hat erhebliche Verbesserungen bei Warenkorb, Checkout und gleichzeitigen Benutzern erzielt, nur aufgrund der Redis-Optimierung.

### Datenmodell optimieren

Viele Probleme entstehen durch Daten, darunter fehlerhafte Datenmodelle, nicht ordnungsgemäß strukturierte Daten und Daten, denen ein Index fehlt.

Es sieht gut aus, wenn Sie einige Verbindungen testen. Nach der Bereitstellung in der Produktion kann es jedoch zu einer schwerwiegenden Leistungsbeeinträchtigung kommen. Es ist wichtig, dass Systemintegratoren wissen, wie ein Datenmodell (insbesondere für Produktattribute) entwickelt, unnötige Attribute vermieden und obligatorische Attribute beibehalten werden, die sich auf die Geschäftslogik auswirken (z. B. Preise, Lagerverfügbarkeit und Suche).

Für Attribute, die keine Auswirkungen auf die Geschäftslogik haben, aber weiterhin auf der Storefront vorhanden sein müssen, kombinieren Sie sie zu einigen Attributen (z. B. JSON-Format).

Um die Leistung der Plattform zu optimieren, ist es nicht erforderlich, dieses Attribut in Adobe Commerce hinzuzufügen, wenn auf der Storefront keine Geschäftslogik aus Daten oder Attributen aus einem PIM oder ERP erforderlich ist.

### Design für Skalierbarkeit

Die Skalierbarkeit ist wichtig für Unternehmen, die Kampagnen durchführen und häufig Spitzenverkehrszeiten erleben. Eine skalierbare Architektur und ein skalierbares Anwendungsdesign können die Ressourcen während Spitzenzeiten erhöhen und später reduzieren.
