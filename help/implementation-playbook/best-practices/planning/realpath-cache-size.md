---
title: RealPath-Cachegröße
description: Erfahren Sie, wie Sie die Leistung von Adobe Commerce optimieren können, indem Sie die Konfiguration des PHP readlpath Cache aktualisieren, um empfohlene Einstellungen zu verwenden.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%
---
# Best Practices für die RealPath-Cache-Konfiguration

Der RealPath-Cache speichert die echten Dateisystempfade der referenzierten Dateinamen zwischen, anstatt sie jedes Mal nachzuschlagen. Jedes Mal, wenn verschiedene Dateifunktionen ausgeführt werden oder eine Datei benötigen und einen relativen Pfad verwenden, muss PHP nachschlagen, wo diese Datei wirklich existiert.

Um die Leistung von Commerce zu verbessern, verwenden Sie die folgenden empfohlenen Einstellungen, um die `realpath_cache` in der `php.ini`-Datei zu konfigurieren:

- Cache-Größe auf 10 MB festlegen (`realpath_cache_size=10M`)
- Setzen Sie die Time to Live (ttl) auf 7200 Sekunden (`realpath_cache_ttl=7200`)

Konfigurationsanweisungen finden Sie unter [So legen Sie PHP-Optionen fest](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Betroffene Produkte und Versionen

- Adobe Commerce On-Premises, alle Versionen 2.3.x und höher
- Adobe Commerce auf Cloud-Infrastruktur, alle Versionen 2.3.x und höher

## Potenzielle Auswirkungen auf die Leistung

Wenn die RealPath-Cache-Konfigurationswerte zu niedrig oder zu hoch sind, führt dies zu zusätzlichem Overhead bei der Cache-Generierung, was die Leistung verlangsamt.

## Weitere Informationen

- [On-Premise: PHP-Einstellungen](../../../performance/software.md#php-settings)
- Cloud-Infrastruktur:
  - [Best Practices für Datenbanken](database-on-cloud.md)
  - [Häufigste Datenbankprobleme in Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Indexer „Update on Schedule“ optimiert die Magento-Leistung](../maintenance/indexer-configuration.md)
