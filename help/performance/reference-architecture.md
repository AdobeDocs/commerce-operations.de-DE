---
title: Referenzarchitektur
description: Überprüfen Sie Diagramme der empfohlenen Referenzarchitektur für Adobe Commerce-Implementierungen.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Referenzarchitektur

Hier wird eine allgemeine empfohlene Einrichtung für Adobe Commerce-Instanzen beschrieben, die einfache Server verwenden, die physisch in einem Rechenzentrum gehostet werden (nicht virtualisiert) und in denen Ressourcen nicht für andere Benutzer freigegeben werden. Ihr Hosting-Anbieter kann, insbesondere wenn er sich auf Hosting mit hoher Leistung von Commerce spezialisiert hat, eine andere Einrichtung empfehlen, die Ihren Anforderungen gleichermaßen oder effektiver entspricht.

Informationen zu Adobe Commerce in Cloud-Infrastrukturumgebungen finden Sie unter [Starterarchitektur](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] Referenzarchitekturdiagramm

Das Diagramm [!DNL Commerce] Referenzarchitektur stellt den Best Practice-Ansatz zum Einrichten einer skalierbaren [!DNL Commerce] -Site dar.

Die Farbe jedes Elements im Diagramm zeigt an, ob das Element Teil von Magento Open Source oder Adobe Commerce ist und ob es erforderlich ist.

* Orangenelemente sind für die Magento Open Source erforderlich
* Graue Elemente sind optional für die Magento Open Source
* Blaue Elemente sind für Adobe Commerce optional.

![Commerce-Referenzarchitektur-Diagramm](../assets/performance/images/ref-architecture-2.3.png)

Die folgenden Abschnitte enthalten Empfehlungen und Überlegungen zu jedem Abschnitt des Commerce-Referenzarchitektur-Diagramms.

### [!DNL Varnish]

* Ein [!DNL Varnish]-Cluster kann auf den Traffic einer Site skaliert werden
* Die Größe der Instanz basierend auf der Anzahl der benötigten Cache-Seiten anpassen
* Verwenden Sie auf einer Site mit hohem Traffic-Aufkommen einen [!DNL Varnish] Master, um sicherzustellen, dass im Cache eine Anforderung (höchstens) pro Webstufe geleert wird.

### Web

* Aktivieren der Skalierung von Knoten für Traffic und Redundanz
* Ein Knoten ist Master und führt Cron aus
* Alternativ können Sie einen dedizierten Admin- und Worker-Knoten verwenden

### Cache

* Erwägen Sie die Implementierung einer separaten Redis-Instanz für Sitzungen
* Sie können eine Redis-Instanz pro Cache haben.
* Größe der Instanz so ändern, dass sie die größte erwartete Cachegröße enthält

### Datenbank und Warteschlangen

* High-Traffic-Sites können die DB-Leistung mit Slave-DBs optimieren und DBs für Bestellungen/Warenkorb (in Adobe Commerce) aufteilen.
* Erwägen Sie die Verwendung einer Slave-DB, um eine schnelle Wiederherstellung und Datensicherungen zu ermöglichen
* Sites mit geringem Traffic können Bilder in der DB speichern

### Suche {#search-heading}

* Anzahl der Instanzen auf Grundlage des Suchverkehrs anpassen

### Speicherung

* Erwägen Sie die Verwendung von GFS oder GlusterFS für Pub-/Medienspeicher.
* Alternativ können Sie DB-Speicher für Sites mit geringem Traffic verwenden

### Empfohlene [!DNL Varnish] Referenzarchitektur

Magento unterstützt standardmäßig mehrere vollständige Seiten-Caching-Engines (Datei, Memcache, Redis, [!DNL Varnish]) sowie eine erweiterte Abdeckung durch Erweiterungen. [!DNL Varnish] ist die empfohlene vollständige Seiten-Cache-Engine.  [!DNL Commerce] unterstützt viele verschiedene [!DNL Varnish] -Konfigurationen.

Für Sites, die keine hohe Verfügbarkeit erfordern, empfehlen wir die Verwendung eines einfachen [!DNL Varnish]-Setups mit Nginx-SSL-Terminierung.

![Einfache [!DNL Varnish] Konfiguration mit SSL-Beendigung](../assets/performance/images/single-varnish-with-ssl-termination.png)

Für Sites, für die eine hohe Verfügbarkeit erforderlich ist, empfehlen wir die Verwendung einer zweistufigen [!DNL Varnish] -Konfiguration mit einem SSL-terminierenden Lastenausgleich.

![Zwei-Tier-Konfiguration mit hoher Verfügbarkeit [!DNL Varnish] mit SSL-beendet den Lastenausgleich](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
