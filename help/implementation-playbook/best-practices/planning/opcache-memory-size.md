---
title: Best Practice für die Größe des OPcache-Speichers
description: Beschreibt, wie Sie eine Leistungsbeeinträchtigung durch bestimmte Einstellungen des OPcache-Speicherverbrauchs in Adobe Commerce-Projekten vermeiden.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Best Practice für die OPcache-Speichergröße in Adobe Commerce

Für Adobe Commerce on Cloud Infrastructure Pro-Planarchitektur 2.3.x wird empfohlen, `opcache.memory_consumption` auf mindestens 2 GB eingestellt ist, um eine Leistungsbeeinträchtigung zu vermeiden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur Pro-Planarchitektur 2.3.x
* PHP 7.0 und höher

## Speicher konfigurieren

Mindestens zuweisen **2 GB** des Speichers für [OPcache PHP-Modul](https://www.php.net/manual/en/book.opcache.php). Das OPcache-Modul wird im `php.ini` -Datei. Um 2048 MB Arbeitsspeicher zuzuweisen, legen Sie `opcache.memory_consumption = 2048`.

## Zusätzliche Informationen

* [Best Practices für die Leistung - PHP-Einstellungen](../../../performance/software.md#php-settings)
* [PHP-Optionen konfigurieren](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Best Practices für Datenbanken mit Adobe Commerce in Cloud-Infrastruktur](database-on-cloud.md)
* [Häufigste Datenbankprobleme in Adobe Commerce bei der Cloud-Infrastruktur](../maintenance/resolve-database-performance-issues.md)
* [Indexer &quot;Auf Zeitplan aktualisieren&quot;optimiert die Leistung von Adobe Commerce](../maintenance/indexer-configuration.md)
