---
title: Hardware-Empfehlungen
description: Erfahren Sie mehr über Hardwareempfehlungen für optimale Adobe Commerce-Leistung. Erfahren Sie mehr über CPU-, Speicher- und Speicheranforderungen für Produktionsbereitstellungen.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%
---
# Hardware-Empfehlungen

## CPUs

[!DNL Commerce] Webknoten dienen allen Anforderungen, die nicht zwischengespeichert werden oder nicht über die Anwendung zwischengespeichert werden können. Ein CPU-Kern kann etwa zwei (manchmal bis zu vier) [!DNL Commerce] effektiv bereitstellen. Verwenden Sie die folgende Gleichung, um zu bestimmen, wie viele Web-Knoten/Kerne Sie benötigen, um alle eingehenden Anfragen zu verarbeiten, ohne sie in die Warteschlange zu stellen:

```text
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Wenn Sie erwarten, dass sich die Auslastung eines Stores ändert, können Sie die Anzahl der Web-Knoten/Kerne für einen aktiven Verkaufszeitraum manuell erhöhen. Alternativ kann ein Modell mit automatischer Skalierung für die automatische Erweiterung von Web-Ebenen verwendet werden.

## Arbeitsspeicher

### PHP

Magento hat unterschiedliche PHP-Speicheranforderungen, je nachdem, wie Ihr System bereitgestellt wird.  Wenn Sie einen einzelnen Server-Store einrichten, empfehlen wir im Allgemeinen die Konfiguration des PHP-Speichers für 2G.  Wenn Sie eine Site mithilfe der Pipeline-Bereitstellung einrichten, empfehlen wir 2 GB auf Ihrem Build-Server und 1 GB auf Ihren Web-Knoten.

Szenarien und erwartete PHP-Speicheranforderungen:

* Webnode, der nur Storefront-Seiten bereitstellt: 256 MB
* Webnode, der Admin-Seiten mit einem großen Katalog bedient: 1 GB
* [!DNL Commerce] Cron-Indizierung einer Site mit einem großen Katalog: >256 MB (Siehe [Advanced-Setup](../performance/advanced-setup.md) zur Optimierung der Leistung.)
* [!DNL Commerce] Kompilieren und Bereitstellen von statischen Assets: 756 MB
* Profilgenerierung im [!DNL Commerce]-Leistungs-Toolkit: >1 GB PHP-RAM, >16 MB [!DNL MySQL] Einstellungen für TMP_TABLE_SIZE und MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

Die [!DNL Commerce] Datenbank (sowie jede andere Datenbank) reagiert auf die Menge des Speichers, der zum Speichern von Daten und Indizes verfügbar ist. Um [!DNL MySQL] Datenindizierung effektiv nutzen zu können, sollte der verfügbare Speicher mindestens etwa halb so groß sein wie die in der Datenbank gespeicherten Daten.

### Caches

Wenn Sie mehrere [!DNL Commerce] bereitstellen und Redis oder [!DNL Varnish] für Ihre Caches verwenden, beachten Sie bitte die folgenden Prinzipien:

* [!DNL Varnish] die vollständige Cache-Speicherinvalidierung der Seite wirksam ist, empfehlen wir, ausreichend Speicher für [!DNL Varnish] zuzuweisen, um die beliebtesten Seiten im Speicher zu speichern
* Der Sitzungs-Cache eignet sich gut zum Konfigurieren einer separaten Instanz von Redis.  Die Speicherkonfiguration für diesen Cache-Typ sollte die Strategie des Warenkorbabbruchs der Site berücksichtigen und angeben, wie lange eine Sitzung im Cache verbleiben soll
* Redis sollten über genügend Speicherplatz verfügen, um alle anderen Caches im Speicher zu speichern, um eine optimale Leistung zu erzielen.  Der Block-Cache ist der Schlüsselfaktor bei der Bestimmung der zu konfigurierenden Speichermenge.  Der Block-Cache wächst im Verhältnis zur Anzahl der Seiten auf einer Site (Anzahl der SKUs x Anzahl der Store-Ansichten)

## Netzwerkbandbreite

Ausreichende Netzwerkbandbreite ist eine der wichtigsten Anforderungen für den Datenaustausch zwischen Web-Knoten, Datenbanken, Caching-/Sitzungs-Servern und anderen Services. Da [!DNL Commerce] Caching effektiv für hohe Leistung nutzt, kann Ihr System Daten aktiv mit Caching-Servern wie Redis austauschen. Wenn sich Redis auf einem Remote-Server befindet, müssen Sie einen ausreichenden Netzwerkkanal zwischen den Web-Knoten und dem Caching-Server bereitstellen, um Engpässe bei Lese-/Schreibvorgängen zu vermeiden.
