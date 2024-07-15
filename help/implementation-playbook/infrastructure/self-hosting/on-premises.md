---
title: Vor-Ort-Infrastruktur
description: Erfahren Sie mehr über die lokale Adobe Commerce-Infrastruktur und Cloud-Services von Drittanbietern.
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
feature: Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Vor-Ort-Infrastruktur von Adobe Commerce

Die Gründe für die Einführung einer neuen Adobe Commerce-Implementierung oder die Umstellung einer bestehenden Adobe Commerce-Implementierung vor Ort auf die Cloud sind vielfältig. Die gängigsten strategischen Faktoren sind jedoch die Senkung der Investitionsausgaben, die Senkung der laufenden Kosten, die Verbesserung der Skalierbarkeit und Elastizität, die Verbesserung der Markteinführungszeit und die Verbesserung der Sicherheit und Einhaltung der Vorschriften.

Das folgende Diagramm zeigt die Referenzarchitektur für die Bereitstellung von Adobe Commerce vor Ort in der AWS-Infrastruktur. Andere Cloud-Anbieter wie Azure, Google Cloud und Alibaba Cloud nutzen ein ähnliches Infrastrukturdesign und homologe Dienste.

![Diagramm, das die Self-Hosting-Adobe Commerce-Infrastruktur auf Cloud-Services von Drittanbietern anzeigt](/help/assets/playbooks/on-premises-infrastructure.svg)

Im Folgenden werden die Rollen und Funktionen der einzelnen Aspekte der oben gezeigten Infrastruktur genauer erläutert:

1. Amazon Route 53 bietet eine DNS-Konfiguration.

1. AWS WAF ist eine Web-Anwendungs-Firewall, die Adobe Commerce vor häufigen Web-Exploits schützt.

1. Amazon CloudFront ist ein CDN (Fast Content Delivery Network), das die Verteilung statischer und dynamischer Webinhalte beschleunigt.

1. Der erste Elastic Load Balancing Application Lastenausgleich verteilt den Traffic in einer AWS-Gruppe mit automatischer Skalierung in mehreren Verfügbarkeitszonen auf verschiedene Instanzen.

1. Der Varnish-Cache ist ein Webanwendungsbeschleuniger, der HTTP-Reverse-Proxy zwischenspeichert. Die Unternehmensversion, die über AWS Marketplace verfügbar ist, wird empfohlen, da sie bessere Funktionen zur Unterstützung von Cloud-Backends und Cache-Bereinigung über dynamische Hosts hinweg bietet.

1. Der zweite Elastic Load Balancing application load balancer verteilt Traffic aus Varnish Cache auf die AWS Auto Scaling-Gruppe von Adobe Commerce-Instanzen in mehreren Verfügbarkeitszonen.

1. Installieren Sie die neueste Version von Adobe Commerce auf Amazon EC2-Instanzen. Die Installation besteht aus der Adobe Commerce-Anwendung, dem Nginx-Webserver und PHP. Erstellen Sie das Amazon Machine Image (AMI), um neue Instanzen in einer Gruppe mit automatischer Skalierung zu starten.

1. Amazon Elasticsearch Service ist ein verwalteter Elasticsearch-Dienst für die Adobe Commerce-Katalogsuche.

1. Amazon ElastiCache for Redis bietet eine Zwischenspeicherschicht für die Datenbank.

1. Verwenden Sie Amazon Aurora oder AmazonRDS, um die Datenbankverwaltung zu vereinfachen (einschließlich hoher Verfügbarkeit und Multi-Master-Konfiguration).

1. EFSMount Target erleichtert die Zuordnung des Amazon Elastic File System (AmazonEFS) zu Varnish- und Adobe Commerce-Instanzen.

1. Verwenden Sie Amazon EFS, um auf die freigegebene Konfiguration in verschiedenen und freigegebenen Medien-Assets in Adobe Commerce-Instanzen zuzugreifen.

## Cloud Services

Zusätzlich zur Bereitstellung einer unterstützenden Technologieplattform für die Aktivierung von DevOps-Prozessen in AWS in Ihrer Adobe Commerce-Umgebung bietet AWS eine Reihe von Diensten, die (bei Fehlen von) Ihre bestehenden Software Configuration Management (SCM)-Lösungen bereitstellen oder ergänzen können. Dazu gehören AWSCodeCommit, AWSCodeBuild, AWSCodePipeline und AWSCodeDeploy, die eine verwaltete Quellsteuerung, einen Build, eine kontinuierliche Integration/kontinuierliche Bereitstellung (CI/CD) und Bereitstellungsdienste ermöglichen.

## Cloud-Migration

Das Wertversprechen für die Migration von Adobe Commerce zu AWS wird durch verschiedene Dienste weiter verbessert, die operative Einblicke und Flexibilität bieten. Was wir meinen, ist ein operativer Einblick in die Plattform nicht nur aus technischer Sicht (z. B. Anforderungen pro Stunde), sondern auch aus betrieblicher Sicht (z. B. Bestellungen pro Stunde), insbesondere wenn die beiden Datensätze verheiratet werden können. Dies bietet einen nahezu echtzeitbasierten Überblick über die Kampagnenleistung, die Betriebskosten der Plattform und eine nahezu unendliche Anzahl anderer Indikatoren.

Die Einrichtung von Adobe Commerce in AWS kann bestimmte Anwendungsabhängigkeiten durch vollständig verwaltete Alternativen ersetzen, die in der Cloud verfügbar sind. Anstatt beispielsweise eine relationale Datenbank direkt auf EC2-Instanzen zu hosten, kann die Datenbank für viele Anwendungen einfach durch den Amazon Relational Database Service (AmazonRDS) ersetzt werden. Der Vorteil dieser Strategie besteht darin, dass die Betriebsverantwortung nicht differenzierter Komponenten auf AWS übertragen werden kann, ohne dass die Kernanwendung wesentlich geändert werden muss.

Es stehen verschiedene Bereitstellungsoptionen für die Ausführung von Adobe Commerce auf AWS zur Verfügung. Die beste Wahl hängt von Ihren Anforderungen an Kosten, Umfang, Verfügbarkeit und Flexibilität sowie von den Fertigkeiten Ihrer Organisation in AWS und Adobe Commerce ab.

{{$include /help/_includes/hosting-related-links.md}}
