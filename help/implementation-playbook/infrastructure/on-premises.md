---
title: Vor-Ort-Infrastruktur
description: Erfahren Sie mehr über die On-Premise-Infrastruktur von Adobe Commerce und Cloud-Services von Drittanbietern.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---


# Adobe Handel vor Ort - Infrastruktur

Die Motive für die Einführung einer neuen Adobe Commerce-Implementierung oder die Umstellung einer bestehenden On-Premise-Adobe Commerce-Implementierung auf die Cloud sind vielfältig. Die gängigsten strategischen Faktoren sind jedoch die Reduzierung der Investitionsausgaben, die Senkung laufender Kosten, die Verbesserung der Skalierbarkeit und Elastizität, die Verbesserung der Time-to-Market und die Verbesserung der Sicherheit und Compliance.

Das folgende Diagramm zeigt die Referenzarchitektur für die Bereitstellung von Adobe Commerce in lokalen AWS-Infrastrukturen. Andere Cloud-Anbieter wie Azure, Google Cloud und Alibaba Cloud nutzen ein ähnliches Infrastrukturdesign und homologe Dienste.

![Abbildung einer selbstgehosteten Adobe Commerce-Infrastruktur auf Cloud-Services von Drittanbietern](../../assets/playbooks/on-premises-infrastructure.svg)

Im Folgenden werden die Rollen und Funktionen der einzelnen Aspekte der oben gezeigten Infrastruktur genauer erläutert:

1. Amazon Route 53 bietet eine DNS-Konfiguration.

1. AWS WAF ist eine Webanwendungs-Firewall, die Adobe Commerce vor häufigen Web-Exploits schützt.

1. Amazon CloudFront ist ein CDN (Fast Content Delivery Network), das die Verteilung statischer und dynamischer Webinhalte beschleunigt.

1. Der erste Elastic Load Balancing application load balancer verteilt Traffic auf verschiedene Instanzen in einer AWS Auto Scaling Gruppe in mehreren Verfügbarkeitszonen.

1. Der Varnish-Cache ist ein Webanwendungsbeschleuniger, der HTTP-Reverse-Proxy zwischenspeichert. Die Unternehmensversion, die über den AWS-Marketplace verfügbar ist, wird empfohlen, da sie bessere Funktionen zur Unterstützung von Cloud-Backends und Cache-Bereinigung über dynamische Hosts hinweg bietet.

1. Der zweite Elastic Load Balancing application load balancer verteilt Traffic aus Varnish Cache auf die AWS Auto Scaling-Gruppe von Adobe Commerce-Instanzen in mehreren Verfügbarkeitszonen.

1. Installieren Sie die neueste Version von Magento Open Source oder Adobe Commerce auf Amazon EC2-Instanzen. Die Installation besteht aus der Adobe Commerce-Anwendung, dem Nginx-Webserver und PHP. Erstellen Sie das Amazon Machine Image (AMI), um neue Instanzen in einer Gruppe mit automatischer Skalierung zu starten.

1. Amazon Elasticsearch Service ist ein verwalteter Elasticsearch-Dienst für die Adobe Commerce-Katalogsuche.

1. Amazon ElastiCache for Redis bietet eine Zwischenspeicherschicht für die Datenbank.

1. Verwenden Sie Amazon Aurora oder AmazonRDS, um die Datenbankverwaltung zu vereinfachen (einschließlich hoher Verfügbarkeit und Übergeordneter Multikonfiguration).

1. EFSMount Target erleichtert die Zuordnung des Amazon Elastic File System (AmazonEFS) zu Varnish- und Adobe Commerce-Instanzen.

1. Verwenden Sie Amazon EFS, um auf die freigegebene Konfiguration über verschiedene und freigegebene Medien-Assets in Adobe Commerce-Instanzen hinweg zuzugreifen.

## Cloud Services

AWS bietet nicht nur eine unterstützende Technologieplattform für die Aktivierung von DevOps-Prozessen auf AWS in Ihrer Adobe Commerce-Umgebung, sondern bietet auch eine Reihe von Diensten, die (falls nicht vorhanden) Ihre bestehenden Software Configuration Management (SCM)-Lösungen (Software Configuration Management) bereitstellen oder ergänzen können. Dazu gehören AWSCodeCommit, AWSCodeBuild, AWSCodePipeline und AWSCodeDeploy, die eine verwaltete Quellsteuerung, einen Build, eine kontinuierliche Integration/kontinuierliche Bereitstellung (CI/CD) und Bereitstellungsdienste ermöglichen.

## Cloud-Migration

Das Wertversprechen für die Migration von Adobe Commerce auf AWS wird durch die Verfügbarkeit verschiedener Dienste, die operative Einblicke und Agilität bieten, weiter verbessert. Wir meinen operative Einblicke in die Plattform nicht nur aus technischer Sicht (z. B. Anforderungen pro Stunde), sondern auch aus betrieblicher Sicht (z. B. Bestellungen pro Stunde), insbesondere wenn die beiden Datensätze verheiratet werden können. Dies bietet einen nahezu echtzeitbasierten Überblick über die Kampagnenleistung, die Betriebskosten der Plattform und eine nahezu unendliche Anzahl anderer Indikatoren.

Die Einrichtung von Adobe Commerce auf AWS kann bestimmte Anwendungsabhängigkeiten durch vollständig verwaltete Alternativen ersetzen, die in der Cloud verfügbar sind. Anstatt beispielsweise eine relationale Datenbank direkt auf EC2-Instanzen zu hosten, kann die Datenbank für viele Anwendungen einfach durch den Amazon Relational Database Service (AmazonRDS) ersetzt werden. Der Vorteil dieser Strategie besteht darin, dass die operative Verantwortung nicht differenzierter Komponenten auf AWS übertragen werden kann, ohne dass wesentliche Änderungen an der Kernanwendung erforderlich sind.

Für die Ausführung von Adobe Commerce (Magento Open Source- und Adobe Commerce-Versionen) auf AWS stehen verschiedene Bereitstellungsoptionen zur Verfügung. Die beste Wahl hängt von Ihren Anforderungen an Kosten, Umfang, Verfügbarkeit und Flexibilität sowie den AWS- und Adobe-Commerce-Kompetenzen Ihrer Organisation ab.
