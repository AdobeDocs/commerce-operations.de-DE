---
title: Best Practice für die Größe des OP-Cache-Speichers
description: Beschreibt, wie Leistungseinbußen durch bestimmte Einstellungen der OPcache-Speichernutzung in Adobe Commerce-Projekten verhindert werden können.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 6c0a9268cb3a3b2e76f4a389846e8407f0893b4f
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---

# Best Practice für die Größe des OP-Cache-Speichers in Adobe Commerce

Für Adobe Commerce on Cloud Infrastructure Pro plan architecture 2.3.x wird empfohlen, `opcache.memory_consumption` auf mindestens 2 GB festzulegen, um Leistungseinbußen zu vermeiden.

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur 2.3.x
* PHP 7.0 und höher

## Konfigurieren des Speichers

Mindestens **2 GB** Speicher für das [OPcache PHP-Modul](https://www.php.net/manual/en/book.opcache.php). Das OPcache-Modul wird in der `php.ini`-Datei konfiguriert. Um 2048 MB Speicher zuzuweisen, setzen Sie `opcache.memory_consumption = 2048`.

## Weitere Informationen

* [Best Practices für die Leistung - PHP-Einstellungen](../../../performance/software.md#php-settings)
* [PHP-Optionen konfigurieren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/configure-app-yaml)
* [Best Practices für Datenbanken für Adobe Commerce in der Cloud-Infrastruktur](database-on-cloud.md)
* [Häufigste Datenbankprobleme in Adobe Commerce in der Cloud-Infrastruktur](../maintenance/resolve-database-performance-issues.md)
* [Indexer „Update on Schedule“ optimieren die Leistung von Adobe Commerce](../maintenance/indexer-configuration.md)
