---
title: Grundsätze der Plattformentwicklung
description: Grundlegende Prinzipien der Plattformentwicklung bei der Arbeit mit Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Grundsätze der Plattformentwicklung

In diesem Playbook werden einige der wichtigsten Entwicklungsstandards für Adobe Commerce genauer erläutert, darunter:

- Funktionaler und technischer Bereich entsprechend dem Entwicklungsprozess
- Best Practices für die Entwicklung, die mit der MVC-Architektur abgestimmt sind
- Architektonische Aspekte, einschließlich GRA
- Sicherheitsstandards gegen Scripting und Exploits
- Best Practices für die Entwicklung von Erweiterungen
- Web-API-Integrationen mit REST, SOAP und GraphQL
- Leistungsverbesserungen bei Codierung und Infrastruktur
- Testwerkzeuge, -strategien und -methoden

Einige Lösungsimplementierer haben zwar möglicherweise ihre eigenen Vorlieben in Bezug auf die Methoden, Prozesse und Tools, die während eines Implementierungsprojekts verwendet werden, konzentriert sich dieses Playbook jedoch auf allgemein akzeptierte Best Practices und Methoden, die für die meisten Implementierungen freigegeben werden können.

Wie bei allen großen IT-Projekten basiert Adobe Commerce auf Kodierungsstandards, die Best Practices und Standardisierungen der zugrunde liegenden Technologien (z. B. PHP/Zend, Symfony, JavaScript, jQuery und HTML) sowie Standards nutzen, die innerhalb der Adobe Commerce Coding Standard festgelegt wurden. Die Einhaltung dieser Standards ist ein absolutes Muss, um Fehler zu beseitigen und die Qualität und Wartbarkeit von benutzerdefiniertem Code zu verbessern.

## Adobe Commerce in Cloud-Infrastruktur

Adobe Commerce in Cloud-Infrastruktur ist eine verwaltete, automatisierte Hosting-Plattform für die Adobe Commerce-Software. Adobe Commerce in Cloud-Infrastrukturen bietet eine Vielzahl zusätzlicher Funktionen, die ihn von lokalen Implementierungen von Adobe Commerce und Magento Open Source unterscheiden:

![Informationen zur Adobe Commerce-Komponente](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce in Cloud-Infrastruktur bietet eine vorkonfigurierte Infrastruktur, die PHP, MySQL, Redis, RabbitMQ und Elasticsearch-Technologien umfasst. einen Git-basierten Workflow mit automatischen Build- und Bereitstellungsvorgängen für eine effiziente schnelle Entwicklung und kontinuierliche Bereitstellung jedes Mal, wenn Code-Änderungen in eine Platform as a Service-Umgebung (PaaS) gepusht werden; hochgradig anpassbare Umgebungskonfigurationsdateien und -werkzeuge; und AWS-Hosting, das eine skalierbare und sichere Umgebung für Online-Verkäufe und -Einzelhandel bietet.

![Informationen zur Adobe Commerce-Komponente](../../assets/playbooks/cloud-tech-stack.svg)
