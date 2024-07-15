---
title: Übersicht über die Cloud-Infrastruktur
description: Erfahren Sie mehr über die Adobe Commerce in der Cloud-Infrastruktur.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# Übersicht

Eine der beliebtesten Managed Hosting-Optionen für Adobe Commerce auf AWS wird von Adobe Commerce selbst angeboten. Adobe Commerce on Cloud Infrastructure ist eine vollständig verwaltete automatisierte Hosting-Plattform für die Adobe Commerce-Software.

Adobe Commerce on Cloud Infrastructure ist ein Plattform-as-a-Service-Angebot, das eine schnelle Bereitstellung vollständig anpassbarer, sicherer und skalierbarer Web-Storefronts in Kombination mit einer führenden Hosting- und Managed Services-Infrastruktur ermöglicht. Es bietet zwei Pläne mit unterschiedlichen Infrastrukturen. Adobe Commerce [Starter](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#starter-projects)-Pläne eignen sich am besten für kleinere Geschäfte mit geringerer Komplexität und kleineren Katalogen. Adobe Commerce [Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#pro-projects)-Pläne sind für größere Geschäfte mit mehr Komplexität, größere Produktkataloge oder Traffic mit Spitzenwerten ausgelegt. Adobe ermittelt die entsprechende Architektur mit der Eingabe von Partnern.

Adobe Commerce ist Cloud-fähig mit einer vollständig redundanten Multi-Cloud-Hosting-Infrastruktur, die optimale Leistung, Ausfallsicherheit und elastische Skalierbarkeit bietet. Sie können Ihre Commerce-Plattform effizient über das Content Delivery Network (CDN) von Fastly ausführen. Mit New Relic für die Überwachung und Verwaltung können Sie Ihre Store-Umgebung reibungslos laufen lassen.

Adobe Commerce bietet alle Vorteile des modernen Cloud-Computing, das am häufigsten mit SaaS-Lösungen in Verbindung gebracht wird, während gleichzeitig die Flexibilität bei der Softwareanpassung gewahrt bleibt:

- Elastische Skalierbarkeit
- Hohe Ausfallsicherheit und Verfügbarkeit
- PCI-Compliance
- Globale Verfügbarkeit und automatisiertes Patchen

![Abbildung von Architekturelementen von Adobe Commerce in der Cloud-Infrastruktur](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Vorteile

Weitere Vorteile von Adobe Commerce sind:

- **Optimiert für Adobe Commerce**. Adobe Commerce-entwickelte Build-Skripte und Dienstkonfigurationen stellen sicher, dass jede Instanz korrekt abgestimmt und für eine optimale Händlerleistung konfiguriert ist.

- **Konsistente, sichere Versionen**. Alle Code-Bereitstellungen sind Git-basiert für Konsistenz und Wiederholbarkeit mit schreibgeschützten Produktionsumgebungen für strengere Sicherheit.

- **Flexibilität für Partner**. Eine vollständige REST-API und eine skriptfähige Befehlszeilenschnittstelle sorgen für einfache Integration in externe Systeme und Kompatibilität mit vorhandenen Code-Management-Workflows.

- **Flexibles Bereitstellungswerkzeug**. Sie können unbegrenzte Umgebungen nach Belieben für Entwicklungsaufgaben, QA-Tests oder Produktionsdiagnosen schnell aufspalten, zusammenführen, klonen und zerreißen.

- **Kontinuierliche Cloud-Bereitstellung**. Mit Konfidenz von der Entwicklung zur UAT zur Produktion wechseln, kontinuierlich über Codezweige und Entwicklungsteams hinweg.

## Dienstleistungen von Drittanbietern

In diesem Abschnitt werden wichtige Dienste und Tools von Drittanbietern für Adobe Commerce zu Cloud-Infrastrukturprojekten zusammengefasst. Weitere Informationen finden Sie unter [Technology Stack](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/tech-stack.html) im _Cloud Guide_ .

- **Fastly CDN**: Wenn Kunden auf Ihre Site und Ihre Stores zugreifen, werden die Anforderungen schnell getroffen, um zwischengespeicherte Seiten schneller zu laden. Fastly WAF bietet auch einen DDoS-Schutzdienst.

- **New Relic**: Bietet eine vollständige Ansicht Ihrer Anwendungen und Betriebsumgebungen. Mit New Relic können Sie Schlüsselmetriken aus mobilen und Browser-Anwendungen mit unterstützenden Diensten, Datenspeichern und Hosts kombinieren, damit Sie die Leistung ganzheitlich optimieren und den Erfolg jeder Initiative sicherstellen können.

- **Composer**: Verwaltet Abhängigkeiten und Aktualisierungen in Adobe Commerce und liefert Kontext über die enthaltenen Pakete, was die Pakete tun und wie sie zusammenpassen.

- **Git**: Bietet die Verwaltung des Quellcodes. Git ermöglicht lokales Verzweigen, praktische Staging-Bereiche und mehrere Workflows mit automatischem Erstellen und Bereitstellen für eine effiziente schnelle Entwicklung und kontinuierliche Bereitstellung.

- **Platform-as-a-Service (PAs)**: Bietet eine vorkonfigurierte Infrastruktur mit PHP-, MySQL-, Redis-, [!DNL RabbitMQ]- und OpenSearch- oder Elasticsearch-Technologien.

- **AWS- oder Azure-Cloud-Hosting**: Stellt die zugrunde liegende Infrastruktur-as-a-Service (IAAs) zur Verfügung, die eine skalierbare und sichere Umgebung für Online-Verkäufe und -Einzelhandel bietet.
