---
title: Platform Tools
description: Wählen Sie die empfohlenen Plattformtools für Ihre Adobe Commerce-Implementierung aus.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Plattformtools

Es gibt keinen Mangel an Aspekten, die gut durchdacht und streng getestet werden müssen, damit eine E-Commerce-Website ohne Interferenzen läuft. Sie müssen nicht nur die richtigen Lösungen finden, um jeden Aspekt der Site anzugehen - von Datenspeicherung und -programmierung über Zwischenspeicherung und Sicherheit bis hin zur Bereitstellung einer Plattform, die reibungslos und effizient erstellt und optimiert werden kann.

This section offers not only a look at the tools, solutions, processes, and methodologies that have been tested and perfected over a number of Adobe Commerce implementations, but also our recommendations for which solutions best fit specific business needs and objectives.

The following table includes solutions that we recommend and can be used within Adobe Commerce to drive performance on the platform:

| Zweck | Tool |
|------------------------------------------|-------------------------|
| Database | MySQL, MariaDB, Percona |
| Programmiersprache | PHP, JS, HTML, LESS CSS |
| Integrierte Entwicklungsumgebung (IDE) | Eclipse, PHPStorm |
| Webserver | Nginx, Apache |
| Caching services | Redis, Varnish |
| Search services | Elasticsearch |
| Nachrichtenwarteschlangendienste | RabbitMQ |
| Sicherheitsscan-Tool | SonarQube, ZAP |

## Datenbank

Je nach Markenbedürfnissen werden drei verschiedene Tools verwendet. MySQL is a great baseline solution as the Adobe Commerce database if you don’t expect your store to handle extreme loads.

MariaDB ist Community-orientierter und arbeitet besser für Benutzer, die sich mehr um Funktionen als um reine Leistung kümmern. MariaDB supports a large array of database engines, disk encryption, complex horizontal interconnectivity, and scaling features, which could be interesting for large Adobe Commerce stores.

Percona ist eine Abspaltung von MySQL, die sich um Leistung und Spitzenlast-Handhabung kümmert. Wählen Sie MariaDB, wenn Sie mehr Lebensqualität und DevOps-Funktionen benötigen. Gehen Sie nach Percona, wenn Sie eine hohe Leistung bei großen Datensätzen erzielen möchten.

## Programming language

Adobe Commerce ist eine PHP-basierte Anwendung und die neuesten Versionen sind immer mit der neuesten stabilen PHP-Version kompatibel (z.B. Adobe Commerce Version 2.4 empfiehlt PHP 7.4). Um mehr Sicherheit und Leistung zu erzielen, gibt es mehrere Faktoren, die bei der Konfiguration von PHP berücksichtigt werden müssen, um maximale Geschwindigkeit und Effizienz bei der Anforderungsverarbeitung zu erzielen. Die Web-Storefront von Adobe Commerce wurde mit HTML, JavaScript und dem LESS CSS-Präprozessor erstellt.

## Webserver

Adobe Commerce unterstützt vollständig die Webserver Nginx und Apache. Adobe Commerce bietet Beispielkonfigurationsdateien für beide:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

The Nginx sample contains settings for better performance and is designed so that little reconfiguration is required.

## Caching-Dienste

Adobe Commerce provides numerous options to store your cache and session data, including Redis, Memcache, filesystem, and database. Bei einer Einrichtung mit mehreren Webknoten ist Redis die beste Option.

We highly recommend using Varnish as the full-page cache server for your store. Adobe Commerce verteilt eine Beispielkonfigurationsdatei für Varnish, die alle für die Leistung empfohlenen Einstellungen enthält.

## Suchdienste

For Adobe Commerce version 2.4 and later, all installations must be configured to use Elasticsearch as the catalog search solution. Elasticsearch provides quick and advanced searches on products in the catalog. Elasticsearch is optional for releases prior to 2.4, but it’s recommended.

## Message queue services

Message queues provide an asynchronous communication mechanism in which the sender and the receiver of a message do not contact each other. RabbitMQ ist ein Open-Source-Nachrichtenbroker, der ein zuverlässiges, hochverfügbares, skalierbares und portables Messaging-System bietet.

## Security tools

Mit dem [Adobe Commerce Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html) können Sie Ihre Store-Websites regelmäßig überwachen und Updates auf bekannte Sicherheitsrisiken, Malware und veraltete Software erhalten. Typically, you start using this tool when you begin user-acceptance testing (UAT). Neben dem kostenlosen Adobe Commerce Security Scan Tool, das für alle Implementierungen und Versionen von Adobe Commerce verfügbar ist, gibt es weitere Optionen, die während des CI/CD-Prozesses und vor jeder Veröffentlichung verwendet werden können.

SonarQube is an open-source quality management platform, designed to analyze and measure your code’s technical quality. SonarQube bietet nicht nur einen vollständigen Bericht mit Code-Fehlern, Syntaxfehlern und Schwachstellen, sondern auch Empfehlungen und Beispiele zur Behebung Ihres Codes. SonarQube eignet sich hervorragend für die Verwendung in einer CI/CD-Umgebung als Tool zur Analyse des Codes vor seiner Bereitstellung.

Zed Attack Proxy (ZAP) is a free security testing tool used by thousands of pen-testers around the globe. ZAP is developed by OWASPand is one of the most preferred tools for manual security testing.
