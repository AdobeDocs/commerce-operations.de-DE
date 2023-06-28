---
title: Managed Services
description: Überprüfen Sie die Zuständigkeiten von Adobe Managed Services, Kunden und Cloud Service-Anbietern für Ihre Adobe Commerce in Bezug auf die Implementierung der Cloud-Infrastruktur.
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
feature: Cloud, Services
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Managed Services

Adobe Commerce für Cloud-Infrastruktur-verwaltete Dienste sind standardmäßig sicher.

![Abbildung von von Adobe Commerce verwalteten Diensten](../../../assets/playbooks/managed-services.svg)

## Gemeinsame Verantwortung

Adobe Commerce Pro-Pläne basieren auf einem Sicherheitsmodell mit gemeinsamer Verantwortung. In diesem Modell haben verschiedene Parteien unterschiedliche Zuständigkeiten für die Aufrechterhaltung der Sicherheit des Systems. Dieser Ansatz ermöglicht sowohl Flexibilität als auch die Nutzung der besten Cloud-Technologien.

![Abbildung des Modells für die gemeinsame Verantwortung von Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### Verantwortlichkeiten für Adobe Managed Services

Adobe Managed Services ist für die Sicherheit und Verfügbarkeit der Adobe Commerce Pro-Cloud-Umgebung, des Core-Adobe Commerce Pro-Anwendungscodes und der internen Commerce-Systeme verantwortlich. Dazu gehören unter anderem:

- Patchen auf Serverebene
- Betrieb der erforderlichen Dienste zur Bereitstellung von Adobe Commerce Pro-Plänen
- Schwachstellentests
- Protokollierung und Überwachung von Sicherheitsereignissen
- Incident Management
- Operative Überwachung
- Unterstützung rund um die Uhr
- Sicherstellung, dass die Kundeninfrastruktur gemäß SLAs verfügbar ist

Adobe Managed Services ist auch für die Verwaltung von Server-Firewall-Konfigurationen (iptables) und Firewall-Konfigurationen (Sicherheitsgruppen) zuständig. Adobe kann in regelmäßigen Abständen auch Sicherheitsupdates für die Kernanwendung veröffentlichen. Es liegt in der Verantwortung der Kunden, diese Patches anzuwenden. Diese Bereiche werden alle von der PCI-Zertifizierung der Adobe Commerce für Cloud-Infrastruktursysteme abgedeckt.

### AWS-Zuständigkeiten

Adobe Managed Services verwendet Amazon Web Services (AWS) für die Cloud-Server-Infrastruktur. AWS ist für die Sicherheit des Netzwerks verantwortlich, einschließlich Routing, Switching und Reichweitennetzsicherheit über Firewall-Systeme und IDS (Intrusion Detection Systems). AWS ist für die physische Sicherheit der Rechenzentren zuständig, in denen die Cloud-Umgebungen von Adobe Commerce verwaltet werden, sowie für die Umgebungssicherheit, um sicherzustellen, dass geeignete Strom-, Kühlungs- und Mechanismen zur Verfügung stehen.

Adobe Commerce Pro plant die Verwendung von:

- Amazon Elastic Compute Cloud (EC2)
- Amazon Simple Storage Service (S3)
- Amazon Elastic Block Store (EBS)
- Amazon Virtual Private Cloud (VPC)
- Amazon Elastic Load Balancer (ELB)
- Amazon Cloud-Trail-Services.

Amazon verfügt über ein umfangreiches Compliance-Programm, das PCI DSS-, SOC 2- und ISO 27001-Zertifizierungen umfasst.

### Verantwortlichkeiten des Lösungspartners/Kunden

Der Kunde ist in erster Linie für die Sicherheit seiner angepassten Implementierung der Adobe Commerce-Anwendung verantwortlich, die in der Adobe Commerce Pro-Plan-Cloud-Umgebung ausgeführt wird. Dazu gehören:

- Sicherstellen einer sicheren Konfiguration und Codierung der Anwendungs- und Sicherheitsüberwachungsaktivitäten, einschließlich Penetrationstests und regelmäßiger Verwundbarkeits-Scans.

- Die Sicherheit von Anpassungen, Erweiterungen, anderen Anwendungen oder Integrationen, die in ihrem System verwendet werden.

- Die Sicherheit der Benutzer und die Gewährung des Zugriffs auf ihre Konfiguration und Anwendung.

- Der Kunde steuert alle Code-Bereitstellungen in seinen Nicht-Produktionsumgebungen. Dieses Steuerelement ist auch dafür verantwortlich, Anwendungssicherheits-Patches auf die Adobe Commerce-Hauptanwendung, Erweiterungen oder benutzerdefinierten Code anzuwenden.

- Der Kunde sollte Penetrationstests seiner angepassten Anwendung durchführen. Diese Verantwortlichkeiten können durch technische Ressourcen des Kunden, der Implementierungspartner oder der professionellen Adobe Commerce-Dienste abgedeckt werden.

- Kunden sind für die PCI-Anforderungen ihrer angepassten Anwendung und ihrer eigenen Prozesse verantwortlich. Die PCI-Compliance des Kunden baut auf den PCI-Zertifizierungen von AWS und Adobe Commerce auf, um die Bereiche zu minimieren, die überprüft werden müssen.
