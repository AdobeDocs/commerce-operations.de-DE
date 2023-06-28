---
title: Cache-Größe für Realpath
description: Erfahren Sie, wie Sie die Adobe Commerce-Leistung optimieren können, indem Sie die Cache-Konfiguration für PHP readpath aktualisieren, um die empfohlenen Einstellungen zu verwenden.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Best Practices für die Konfiguration des Realpath-Caches

Der Realpath-Cache speichert die tatsächlichen Dateisystempfade der referenzierten Dateinamen zwischen, anstatt sie jedes Mal zu suchen. Jedes Mal, wenn verschiedene Dateifunktionen ausgeführt werden oder eine Datei benötigen und einen relativen Pfad verwenden, muss PHP nachschlagen, wo diese Datei wirklich existiert.

Um die Commerce-Leistung zu verbessern, verwenden Sie die folgenden empfohlenen Einstellungen, um die `realpath_cache` -Einstellungen in `php.ini` Datei:

- Legen Sie die Cachegröße auf 10 MB (`realpath cache_size=10M`)
- Legen Sie die Live-Zeit (ttl) auf 7200 Sekunden (`realpath_cache_ttl=7200`)

Konfigurationsanweisungen finden Sie unter [Festlegen von PHP-Optionen](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Betroffene Produkte und Versionen

- Adobe Commerce vor Ort, alle Versionen 2.3.x und höher
- Adobe Commerce in der Cloud-Infrastruktur, alle Versionen 2.3.x und höher

## Potenzielle Auswirkung auf die Leistung

Wenn die Konfigurationswerte für den Realpath-Cache zu niedrig oder zu hoch sind, erhöht sich der Mehraufwand bei der Cache-Generierung, was die Leistung verlangsamt.

## Zusätzliche Informationen

- [Vor Ort: PHP-Einstellungen](../../../performance/software.md#php-settings)
- Über die Cloud-Infrastruktur:
   - [Best Practices für Datenbanken](database-on-cloud.md)
   - [Die häufigsten Datenbankprobleme in Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Indexer &quot;Auf Zeitplan aktualisieren&quot;optimiert die Leistung des Magentos](../maintenance/indexer-configuration.md)
