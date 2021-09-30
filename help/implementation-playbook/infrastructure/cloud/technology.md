---
title: Cloud-Infrastruktur-Technologien
description: Informieren Sie sich über die von uns für Adobe Commerce in der Cloud-Infrastruktur verwendeten Technologien.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Technologien

Wie wir bereits erwähnt haben, nutzt Adobe Commerce eine Reihe von Softwarelösungen, um die Plattform zu unterstützen. Insbesondere haben wir, da es sich um Produktionsumgebungen handelt, einige der technischen Lösungen und Funktionen von Adobe Commerce in Cloud-Infrastrukturen aufgegliedert, die dazu beitragen, Ihre Produktionsumgebung optimal zu nutzen.

![Abbildung der Adobe Commerce in Cloud-Infrastrukturtechnologie](../../../assets/playbooks/infrastructure-technology.svg)

## Software-Lösungen

- **Nginx**—Webserver mit PHP-FPM. Es gibt eine Instanz mit mehreren Workern.

- **GlusterFS** - Dateiserver für die Verwaltung aller statischen Dateibereitstellungen und die Synchronisierung mit vier Ordnerbereitstellungen:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis** - Ein Server pro VM mit nur einem aktiven und den beiden anderen als Replikate.

- **Elasticsearch** - Suchen Sie nach Adobe Commerce Version 2.2.x und höher.

- **Galera** - Datenbankcluster mit einer MySQL-Datenbank von MariaDB pro Knoten mit einer automatischen Inkrementierungseinstellung von drei für eindeutige IDs in jeder Datenbank.

## Funktionen und Vorteile

- Mit drei dedizierten Instanzen in einem VPC gibt es einen elastischen Lastenausgleich über drei separate Verfügbarkeitszonen oder Rechenzentren hinweg.

- Höhere Ausfallsicherheit wird bei Ereignissen erzielt, die dazu führen können, dass eine einzelne Instanz fehlschlägt. Beispiel: Ausfall einer gesamten AWS-Verfügbarkeitszone oder eines Rechenzentrums.

- Keine Ausfallzeiten - Skalierung über den gesamten Stapel, einschließlich Web, Zwischenspeicherung, Suche und Datenbank, in weniger als 15 Minuten.
