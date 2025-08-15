---
title: RealPath-Cachegröße
description: Erfahren Sie, wie Sie die Leistung von Adobe Commerce optimieren können, indem Sie die Konfiguration des PHP readlpath Cache aktualisieren, um empfohlene Einstellungen zu verwenden.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 1%

---

# Best Practices für die RealPath-Cache-Konfiguration

Der RealPath-Cache speichert die echten Dateisystempfade der referenzierten Dateinamen zwischen, anstatt sie jedes Mal nachzuschlagen. Jedes Mal, wenn verschiedene Dateifunktionen ausgeführt werden oder eine Datei benötigen und einen relativen Pfad verwenden, muss PHP nachschlagen, wo diese Datei wirklich existiert.

Um die Leistung von Commerce zu verbessern, verwenden Sie die folgenden empfohlenen Einstellungen, um die `realpath_cache` in der `php.ini`-Datei zu konfigurieren:

- Cache-Größe auf 10 MB festlegen (`realpath cache_size=10M`)
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
- [Indexer „Update on Schedule“ optimieren die Leistung von Magento](../maintenance/indexer-configuration.md)
