---
title: Hardware-Recommendations
description: Überprüfen Sie eine Liste der empfohlenen Hardware im Zusammenhang mit der optimalen Leistung von Adobe Commerce-Implementierungen.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Hardware-Empfehlungen

## CPUs

[!DNL Commerce] -Webknoten dienen allen Anforderungen, die nicht zwischengespeichert werden oder nicht über die Anwendung zwischengespeichert werden können. Ein CPU-Kern kann etwa zwei (manchmal bis zu vier) [!DNL Commerce] -Anfragen effektiv unterstützen. Verwenden Sie die folgende Gleichung, um zu bestimmen, wie viele Webknoten/Kerne Sie benötigen, um alle eingehenden Anforderungen zu verarbeiten, ohne sie in die Warteschlange zu stellen:

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Wenn Sie erwarten, dass sich die Last eines Stores ändert, können Sie die Anzahl der Webknoten/Kerne für einen aktiven Verkaufszeitraum manuell erhöhen. Alternativ kann ein automatisches Skalierungsmodell zum automatischen Erweitern von Web-Stufen verwendet werden.

## Speicher

### PHP

Magento hat unterschiedliche PHP-Speicheranforderungen, je nachdem, wie Ihr System bereitgestellt wird.  Wenn Sie einen einzelnen Server-Store einrichten, empfehlen wir generell, den PHP-Speicher für 2G zu konfigurieren.  Wenn Sie eine Site mithilfe der Pipeline-Bereitstellung einrichten, empfehlen wir für Ihren Build-Server 2 GB und für Ihre Webknoten 1 GB.

Szenarien und erwartete PHP-Speicheranforderungen:

* Webnode nur für Storefront-Seiten: 256 MB
* Webnode für Admin-Seiten mit großem Katalog: 1 GB
* [!DNL Commerce] Cron-Indizierung einer Site mit einem großen Katalog: >256 MB (Informationen zur Optimierung der Leistung finden Sie unter [advanced-setup](../performance/advanced-setup.md) .)
* [!DNL Commerce] Kompilieren und Bereitstellen von statischen Assets: 756 MB
* [!DNL Commerce] Profilgenerierung des Leistungs-Toolkits: >1 GB PHP RAM, >16 MB [!DNL MySQL] TMP_TABLE_SIZE und MAX_HEAP_TABLE_SIZE-Einstellungen

### [!DNL MySQL]

Die [!DNL Commerce] -Datenbank (sowie jede andere Datenbank) ist abhängig von der Speichermenge, die zum Speichern von Daten und Indizes verfügbar ist. Um die [!DNL MySQL]-Datenindizierung effektiv zu nutzen, sollte die verfügbare Speichermenge mindestens der Hälfte der in der Datenbank gespeicherten Daten entsprechen.

### Caches

Beachten Sie bei der Bereitstellung mehrerer [!DNL Commerce] und der Verwendung von Redis oder [!DNL Varnish] für Ihre Caches die folgenden Grundsätze:

* [!DNL Varnish] Die Invalidierung des gesamten Seiten-Cache-Speichers ist wirksam. Empfehlen Sie genügend Speicher, der [!DNL Varnish] zugewiesen ist, um Ihre beliebtesten Seiten im Speicher zu speichern.
* Sitzungs-Cache ist ein guter Kandidat, um eine separate Instanz von Redis zu konfigurieren.  Die Speicherkonfiguration für diesen Cache-Typ sollte die Strategie des Warenkorbabbruchs auf der Site berücksichtigen und berücksichtigen, wie lange eine Sitzung voraussichtlich im Cache verbleibt
* Für Redis sollte ausreichend Speicher zur Verfügung stehen, damit alle anderen Caches im Speicher gespeichert werden können, um eine optimale Leistung zu erzielen.  Der Block-Cache ist der Schlüsselfaktor bei der Bestimmung des Speicherbedarfs, der konfiguriert werden muss.  Der Block-Cache wächst relativ zur Anzahl der Seiten auf einer Site (Anzahl der Stunden x Anzahl der Store-Ansichten).

## Netzwerkbandbreite

Eine ausreichende Netzwerkbandbreite ist eine der wichtigsten Anforderungen für den Datenaustausch zwischen Webknoten, Datenbanken, Caching-/Sitzungsservern und anderen Diensten. Da [!DNL Commerce] die Zwischenspeicherung für eine hohe Leistung effektiv nutzt, kann Ihr System Daten aktiv mit Caching-Servern wie Redis austauschen. Wenn sich Redis auf einem Remote-Server befindet, müssen Sie einen ausreichenden Netzwerkkanal zwischen Webknoten und dem Caching-Server bereitstellen, um Engpässe bei Lese-/Schreibvorgängen zu vermeiden.
