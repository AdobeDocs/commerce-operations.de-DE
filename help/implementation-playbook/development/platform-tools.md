---
title: Plattform-Tools
description: Wählen Sie die empfohlenen Plattformtools für Ihre Adobe Commerce-Implementierung aus.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
feature: Configuration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# Plattformtools

Es gibt keinen Mangel an Aspekten, die gut durchdacht und streng getestet werden müssen, damit eine E-Commerce-Website ohne Interferenzen läuft. Sie müssen nicht nur die richtigen Lösungen finden, um jeden Aspekt der Site anzugehen - von Datenspeicherung und -programmierung über Zwischenspeicherung und Sicherheit bis hin zur Bereitstellung einer Plattform, die reibungslos und effizient erstellt und optimiert werden kann.

Dieser Abschnitt bietet nicht nur einen Überblick über die Tools, Lösungen, Prozesse und Methoden, die über eine Reihe von Adobe Commerce-Implementierungen getestet und perfektioniert wurden, sondern auch über unsere Empfehlungen, für die Lösungen am besten auf spezifische Geschäftsanforderungen und -ziele abgestimmt sind.

Die folgende Tabelle enthält Lösungen, die wir empfehlen und innerhalb von Adobe Commerce zur Leistungssteigerung auf der Plattform verwenden können:

| Zweck | Tool |
|------------------------------------------|-------------------------|
| Datenbank | MySQL, MariaDB, Percona |
| Programmiersprache | PHP, JS, HTML, LESS CSS |
| Integrierte Entwicklungsumgebung (IDE) | Eclipse, PHPStorm |
| Webserver | Nginx, Apache |
| Caching-Dienste | Redis, Varnish |
| Suchdienste | Elasticsearch |
| Nachrichtenwarteschlangendienste | [!DNL RabbitMQ] |
| Sicherheitsscan-Tool | SonarQube, ZAP |

## Datenbank

Je nach Markenbedürfnissen werden drei verschiedene Tools verwendet. MySQL ist eine großartige Basislösung als die Adobe Commerce-Datenbank, wenn Sie nicht erwarten, dass Ihr Store extreme Lasten bewältigt.

MariaDB ist Community-orientierter und arbeitet besser für Benutzer, die sich mehr um Funktionen als um reine Leistung kümmern. MariaDB unterstützt eine Vielzahl von Datenbank-Engines, Festplattenverschlüsselung, komplexe horizontale Vernetzung und Skalierungsfunktionen, die für große Adobe Commerce-Stores interessant sein könnten.

Percona ist eine Abspaltung von MySQL, die sich um Leistung und Spitzenlast-Handhabung kümmert. Wählen Sie MariaDB, wenn Sie mehr Lebensqualität und DevOps-Funktionen benötigen. Gehen Sie nach Percona, wenn Sie eine hohe Leistung bei großen Datensätzen erzielen möchten.

## Programmiersprache

Adobe Commerce ist eine PHP-basierte Anwendung und die neuesten Versionen sind immer mit der neuesten stabilen PHP-Version kompatibel (z.B. empfiehlt Adobe Commerce Version 2.4 PHP 7.4). Um mehr Sicherheit und Leistung zu erzielen, gibt es mehrere Faktoren, die bei der Konfiguration von PHP berücksichtigt werden müssen, um maximale Geschwindigkeit und Effizienz bei der Anforderungsverarbeitung zu erzielen. Die Adobe Commerce-Web-Storefront wurde mit HTML, JavaScript und dem LESS CSS-Präprozessor erstellt.

## Webserver

Adobe Commerce unterstützt die Webserver Nginx und Apache vollständig. Adobe Commerce bietet empfohlene Beispielkonfigurationsdateien für beide:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Das Nginx-Beispiel enthält Einstellungen für eine bessere Leistung und ist so konzipiert, dass nur wenig Neukonfiguration erforderlich ist.

## Caching-Dienste

Adobe Commerce bietet zahlreiche Optionen zum Speichern Ihres Caches und Ihrer Sitzungsdaten, einschließlich Redis, Memcache, Dateisystem und Datenbank. Bei einer Einrichtung mit mehreren Webknoten ist Redis die beste Option.

Es wird dringend empfohlen, Varnish als vollseitigen Cache-Server für Ihren Store zu verwenden. Adobe Commerce verteilt eine Beispielkonfigurationsdatei für Varnish, die alle empfohlenen Leistungseinstellungen enthält.

## Suchdienste

Für Adobe Commerce Version 2.4 und höher müssen alle Installationen so konfiguriert sein, dass Elasticsearch oder OpenSearch als Katalogsuchlösung verwendet wird. Elasticsearch bietet eine schnelle und erweiterte Suche nach Produkten im Katalog. Elasticsearch ist für Versionen vor 2.4 optional, wird jedoch empfohlen.

## Nachrichtenwarteschlangendienste

Nachrichtenwarteschlangen bieten einen asynchronen Kommunikationsmechanismus, bei dem sich Absender und Empfänger einer Nachricht nicht miteinander in Verbindung setzen. [!DNL RabbitMQ] ist ein Open-Source-Message-Broker, der ein zuverlässiges, hochverfügbares, skalierbares und portables Messaging-System bietet.

## Sicherheitswerkzeuge

Mit dem [Adobe Commerce Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html) können Sie Ihre Store-Websites regelmäßig überwachen und Updates auf bekannte Sicherheitsrisiken, Malware und veraltete Software erhalten. Normalerweise beginnen Sie mit der Verwendung dieses Tools, wenn Sie mit dem Benutzerakzeptanztest (UAT) beginnen. Neben dem Adobe Commerce Security Scan-Tool, das für alle Implementierungen und Versionen von Adobe Commerce kostenlos ist, gibt es weitere Optionen, die während des CI/CD-Prozesses und vor jeder Version verwendet werden können.

SonarQube ist eine Open-Source-Plattform für Qualitätsmanagement, die entwickelt wurde, um die technische Qualität Ihres Codes zu analysieren und zu messen. SonarQube bietet nicht nur einen vollständigen Bericht mit Code-Fehlern, Syntaxfehlern und Schwachstellen, sondern auch Empfehlungen und Beispiele zur Behebung Ihres Codes. SonarQube eignet sich hervorragend für die Verwendung in einer CI/CD-Umgebung als Tool zur Analyse des Codes vor seiner Bereitstellung.

Zed Attack Proxy (ZAP) ist ein kostenloses Sicherheitstest-Tool, das von Tausenden von Open-Tester weltweit verwendet wird. ZAP wird von OWASP entwickelt und ist eines der bevorzugten Tools für manuelle Sicherheitstests.
