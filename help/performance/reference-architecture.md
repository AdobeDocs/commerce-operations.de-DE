---
title: Referenzarchitektur
description: Erfahren Sie mehr über die Referenzarchitektur in Adobe Commerce. Erfahren Sie mehr über Implementierungsanleitungen und Optimierungsstrategien.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Referenzarchitektur

In diesem Abschnitt wird eine allgemeine empfohlene Einrichtung für Adobe Commerce-Instanzen beschrieben, bei der einfache Server verwendet werden, die physisch in einem Rechenzentrum gehostet (nicht virtualisiert) werden, in dem Ressourcen nicht mit anderen Benutzern geteilt werden. Ihr Hosting-Anbieter, insbesondere wenn er auf Hochleistungs-Hosting in Commerce spezialisiert ist, empfiehlt möglicherweise ein anderes Setup, das für Ihre Anforderungen gleichermaßen oder effektiver ist.

Informationen zu Adobe Commerce in Cloud-Infrastrukturumgebungen finden Sie unter [Starter-Architektur](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/architecture/starter-architecture).

## [!DNL Commerce] Referenzarchitekturdiagramm

Das Diagramm [!DNL Commerce] Referenzarchitektur stellt den Best-Practice-Ansatz zum Einrichten einer skalierbaren [!DNL Commerce]-Site dar.

Die Farbe der einzelnen Elemente im Diagramm gibt an, ob das Element Teil von Magento Open Source oder Adobe Commerce ist und ob es erforderlich ist.

* Für Magento Open Source sind orange Elemente erforderlich
* Graue Elemente sind für Magento Open Source optional
* Blaue Elemente sind für Adobe Commerce optional

![Commerce-Referenzarchitekturdiagramm](../assets/performance/images/ref-architecture-2.3.png)

Die folgenden Abschnitte enthalten Empfehlungen und Überlegungen zu jedem Abschnitt des Commerce-Referenzarchitekturdiagramms.

### [!DNL Varnish]

* Ein [!DNL Varnish] Cluster kann auf den Traffic einer Site skaliert werden
* Passen Sie die Instanzgröße auf der Grundlage der Anzahl der benötigten Cache-Seiten an
* Bei einer Website mit hohem Traffic verwenden Sie einen [!DNL Varnish] Master, um sicherzustellen, dass (höchstens) eine Anfrage pro Web-Stufe im Cache geleert wird

### Web

* Aktivieren der Skalierung von Knoten für Traffic und Redundanz
* Ein Knoten ist Master und führt Cron aus.
* Alternativ können Sie einen dedizierten Administrator- und Worker-Knoten verwenden

### Cache

* Erwägen Sie die Implementierung einer separaten Redis-Instanz für Sitzungen
* Pro Cache kann eine Redis-Instanz vorhanden sein
* Instanz so dimensionieren, dass die größte erwartete Cache-Größe enthalten ist

### Datenbank und Warteschlangen

* Sites mit hohem Traffic können die DB-Leistung mit Slave-DBs und Split-DBs für Bestellungen/Warenkörbe (in Adobe Commerce) optimieren
* Erwägen Sie die Verwendung einer Slave-DB für eine schnelle Wiederherstellung und für Datensicherungen
* Sites mit geringem Traffic können Bilder in der Datenbank speichern

### Suche {#search-heading}

* Stimmen Sie die Anzahl der Instanzen basierend auf dem Such-Traffic ab

### Speicherung

* Erwägen Sie die Verwendung von GFS oder GlusterFS für Pub-/Medienspeicher
* Alternativ können Sie den DB-Speicher für Sites mit geringem Traffic verwenden

### Empfohlene [!DNL Varnish] Referenzarchitektur

Magento unterstützt standardmäßig mehrere Engines zum Zwischenspeichern ganzer Seiten (File, Memcache, Redis, [!DNL Varnish]) sowie eine erweiterte Abdeckung durch Erweiterungen. [!DNL Varnish] ist die empfohlene vollständige Seiten-Cache-Engine.  [!DNL Commerce] unterstützt viele verschiedene [!DNL Varnish].

Für Websites, die keine hohe Verfügbarkeit erfordern, empfehlen wir die Verwendung einer einfachen [!DNL Varnish]-Einrichtung mit Nginx-SSL-Beendigung.

![Einfache [!DNL Varnish] mit SSL-Beendigung](../assets/performance/images/single-varnish-with-ssl-termination.png)

Für Websites, für die eine hohe Verfügbarkeit erforderlich ist, empfehlen wir die Verwendung einer 2-Tier-[!DNL Varnish]-Konfiguration mit einem SSL-abschließenden Lastenausgleich.

![Zweistufige [!DNL Varnish]-Konfiguration mit hoher Verfügbarkeit und SSL-Abschluss des Lastenausgleichs](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
