---
title: Übersicht über die Cloud-Infrastruktur
description: Erfahren Sie mehr über Adobe Commerce in der Cloud-Infrastruktur.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Übersicht

Eine der beliebtesten Managed Hosting-Optionen für Adobe Commerce auf AWS wird von Adobe Commerce selbst angeboten. Adobe Commerce on Cloud Infrastructure ist eine vollständig verwaltete automatisierte Hosting-Plattform für die Adobe Commerce-Software.

Adobe Commerce on Cloud Infrastructure ist ein Plattform-as-a-Service-Angebot, das eine schnelle Bereitstellung vollständig anpassbarer, sicherer und skalierbarer Web-Storefronts sowie einer führenden Hosting- und Managed Services-Infrastruktur ermöglicht. Es bietet zwei Pläne mit unterschiedlichen Infrastrukturen. Adobe Commerce Starter eignet sich am besten für kleinere Geschäfte mit weniger Komplexität und kleineren Katalogen. Adobe Commerce Pro wurde für größere Geschäfte mit größerer Komplexität, größeren Produktkatalogen oder Traffic mit Spitzenwerten entwickelt. Adobe Commerce wird die geeignete Architektur mit den Beiträgen von Partnern bestimmen.

Adobe Commerce ist Cloud-fähig mit einer vollständig redundanten Multi-Cloud-Hosting-Infrastruktur, die optimale Leistung, Ausfallsicherheit und elastische Skalierbarkeit bietet. Sie können Ihre Commerce-Plattform effizient über das Content Delivery Network (CDN) von Fastly ausführen. Mit New Relic für die Überwachung und Verwaltung können Sie Ihre Store-Umgebung reibungslos laufen lassen.

Adobe Commerce bietet alle Vorteile des modernen Cloud-Computing, das am häufigsten mit SaaS-Lösungen in Verbindung gebracht wird: elastische Skalierbarkeit, hohe Ausfallsicherheit und Verfügbarkeit, PCI-Compliance, globale Verfügbarkeit und automatisiertes Patchen bei gleichzeitiger Wahrung der Flexibilität bei der Softwareanpassung, die unsere Händler benötigen.

![Abbildung architektonischer Elemente von Adobe Commerce in der Cloud-Infrastruktur](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Vorteile

Weitere Vorteile von Adobe Commerce sind:

- **Optimiert für Adobe Commerce**. Adobe Commerce-entwickelte Build-Skripte und Dienstkonfigurationen stellen sicher, dass jede Instanz korrekt abgestimmt und für eine optimale Händlerleistung konfiguriert ist.

- **Konsistente, sichere Versionen**. Alle Code-Bereitstellungen sind Git-basiert für Konsistenz und Wiederholbarkeit mit schreibgeschützten Produktionsumgebungen für strengere Sicherheit.

- **Flexibilität für Partner**. Eine vollständige REST-API und eine skriptfähige Befehlszeilenschnittstelle sorgen für eine einfache Integration in externe Systeme und Kompatibilität mit vorhandenen Code-Management-Workflows.

- **Flexible Bereitstellungs-Tools**. Sie können unbegrenzte Umgebungen nach Belieben für Entwicklungsaufgaben, QA-Tests oder Produktionsdiagnosen schnell aufspalten, zusammenführen, klonen und zerreißen.

- **Kontinuierlicher Cloud-Versand**. Mit Konfidenz von der Entwicklung zur UAT zur Produktion wechseln, kontinuierlich über Codezweige und Entwicklungsteams hinweg.

## Dienstleistungen von Drittanbietern

Sehen wir uns auch die Software an, die die Vorteile von Adobe Commerce Wirklichkeit werden lässt.

![Abbildung von Adobe Commerce auf dem Technologiestapel der Cloud-Infrastruktur](../../../assets/playbooks/cloud-tech-stack.svg)

- Schnelles CDN: Wenn Kunden auf Ihre Site und Ihre Stores zugreifen, werden die Anforderungen schnell getroffen, um zwischengespeicherte Seiten schneller zu laden. Fastly WAF bietet auch einen DDoS-Schutz.

- New Relic bietet Ihnen einen vollständigen Überblick über Ihre Anwendungen und Betriebsumgebungen. Sie können damit Schlüsselmetriken aus mobilen und Browser-Anwendungen mit unterstützenden Diensten, Datenspeichern und Hosts kombinieren, damit Sie die Leistung ganzheitlich optimieren und den Erfolg jeder Initiative sicherstellen können.

- Der Composer verwaltet Abhängigkeiten und Aktualisierungen in Adobe Commerce und bietet Kontext zu den enthaltenen Paketen, was die Pakete tun und wie sie zusammenpassen.

- Git ist Ihr Code in Repositorys. Es ermöglicht lokales Verzweigen, bequeme Staging-Bereiche und mehrere Workflows mit automatischem Erstellen und Bereitstellen für eine effiziente schnelle Entwicklung und kontinuierliche Bereitstellung.

- Platform-as-a-Service (PAs) bietet eine vorkonfigurierte Infrastruktur, die PHP, MySQL, Redis, [!DNL RabbitMQ], und OpenSearch- oder Elasticsearch-Technologien.

- Das Cloud-Hosting von AWS oder Azure basiert auf Infrastruktur-as-a-Service (IAAS), das eine skalierbare und sichere Umgebung für Online-Verkäufe und -Einzelhandel bietet.
