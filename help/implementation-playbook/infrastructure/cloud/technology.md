---
title: Cloud-Infrastruktur-Technologien
description: Informieren Sie sich über die von uns für Adobe Commerce verwendete Technologie zur Cloud-Infrastruktur.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
source-git-commit: 683ce0a72aca0319ade2e4ccfd7a8e541a228156
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Technologien

Wie wir bereits erwähnt haben, nutzt Adobe Commerce eine Reihe von Softwarelösungen, um die Plattform zu unterstützen. Insbesondere haben wir im Zusammenhang mit der Produktion einige der technischen Lösungen und Funktionen von Adobe Commerce in der Cloud-Infrastruktur aufgeschlüsselt, die dazu beitragen, Ihre Produktionsumgebung optimal zu nutzen.

![Abbildung der Adobe Commerce zur Cloud-Infrastruktur-Technologie](../../../assets/playbooks/infrastructure-technology.svg)

## Software-Lösungen

- **Nginx**—Webserver mit PHP-FPM. Es gibt eine Instanz mit mehreren Workern.

- **GlusterFS**—Dateiserver für die Verwaltung aller statischen Dateibereitstellungen und Synchronisation mit vier Ordnerbereitstellungen:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**—Ein Server pro VM mit nur einem aktiven und den beiden anderen als Replikate.

- **Elasticsearch**—Suchen Sie nach Adobe Commerce-Version 2.2.x und höher.

- **OpenSearch**—Suchen Sie nach Adobe Commerce-Version 2.4.6 und höher.

- **Galera**—Datenbankcluster mit einer MySQL-Datenbank von MariaDB pro Knoten mit einer automatischen Inkrementierungseinstellung von drei für eindeutige IDs in jeder Datenbank.

## Funktionen und Vorteile

- Mit drei dedizierten Instanzen in einem VPC gibt es einen elastischen Lastenausgleich über drei separate Verfügbarkeitszonen oder Rechenzentren hinweg.

- Höhere Ausfallsicherheit wird bei Ereignissen erzielt, die dazu führen können, dass eine einzelne Instanz fehlschlägt. Beispielsweise ein Ausfall einer gesamten AWS-Verfügbarkeitszone oder eines Rechenzentrums.

- Keine Ausfallzeiten - Skalierung über den gesamten Stapel, einschließlich Web, Zwischenspeicherung, Suche und Datenbank, in weniger als 15 Minuten.
