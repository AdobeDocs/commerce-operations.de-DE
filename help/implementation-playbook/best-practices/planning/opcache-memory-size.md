---
title: Best Practice für die Größe des OP-Cache-Speichers
description: Beschreibt, wie Leistungseinbußen durch bestimmte Einstellungen der OPcache-Speichernutzung in Adobe Commerce-Projekten verhindert werden können.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
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
* [PHP-Optionen konfigurieren](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure/app/configure-app-yaml)
* [Best Practices für Datenbanken für Adobe Commerce in der Cloud-Infrastruktur](database-on-cloud.md)
* [Häufigste Datenbankprobleme in Adobe Commerce in der Cloud-Infrastruktur](../maintenance/resolve-database-performance-issues.md)
* [Indexer „Update on Schedule“ optimieren die Leistung von Adobe Commerce](../maintenance/indexer-configuration.md)
