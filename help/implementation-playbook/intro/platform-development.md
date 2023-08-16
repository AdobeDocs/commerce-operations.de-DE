---
title: Grundsätze der Plattformentwicklung
description: Grundlegende Prinzipien der Plattformentwicklung bei der Arbeit mit Adobe Commerce
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Grundsätze der Plattformentwicklung

In diesem Playbook werden einige der wichtigsten Entwicklungsstandards von Adobe Commerce genauer erläutert, darunter:

- Funktionaler und technischer Bereich entsprechend dem Entwicklungsprozess
- Best Practices für die Entwicklung, die mit der MVC-Architektur abgestimmt sind
- Architektonische Aspekte, einschließlich GRA
- Sicherheitsstandards gegen Scripting und Exploits
- Best Practices für die Erweiterungsentwicklung
- Web-API-Integrationen mit REST, SOAP und GraphQL
- Leistungsverbesserungen bei Codierung und Infrastruktur
- Testwerkzeuge, -strategien und -methoden

Einige Lösungsimplementierer haben zwar möglicherweise ihre eigenen Vorlieben in Bezug auf die Methoden, Prozesse und Tools, die während eines Implementierungsprojekts verwendet werden, konzentriert sich dieses Playbook jedoch auf allgemein akzeptierte Best Practices und Methoden, die für die meisten Implementierungen freigegeben werden können.

Wie bei jedem großen IT-Projekt basiert Adobe Commerce auf Kodierungsstandards, die Best Practices und Standardisierungen der zugrunde liegenden Technologien (z. B. PHP/Zend, Symfony, JavaScript, jQuery und HTML) sowie auf Standards nutzen, die innerhalb des Adobe Commerce Coding Standard festgelegt wurden. Die Einhaltung dieser Standards ist ein absolutes Muss, um Fehler zu beseitigen und die Qualität und Wartbarkeit von benutzerdefiniertem Code zu verbessern.

## Adobe Commerce auf Cloud-Infrastruktur

Adobe Commerce on Cloud Infrastructure ist eine verwaltete, automatisierte Hosting-Plattform für die Adobe Commerce-Software. Adobe Commerce in der Cloud-Infrastruktur verfügt über eine Reihe zusätzlicher Funktionen, die es von lokalen Implementierungen von Adobe Commerce und Magento Open Sourcen unterscheidet:

![Infografiken zu Adobe Commerce-Komponenten](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce on Cloud Infrastructure bietet eine vorkonfigurierte Infrastruktur, die PHP, MySQL, Redis, [!DNL RabbitMQ], und Elasticsearch-Technologien; ein Git-basierter Workflow mit automatischen Build- und Bereitstellungsvorgängen für eine effiziente, schnelle Entwicklung und kontinuierliche Bereitstellung jedes Mal, wenn Code-Änderungen in einer Platform as a Service-Umgebung übertragen werden; hochgradig anpassbare Umgebungskonfigurationsdateien und -werkzeuge; und AWS-Hosting, das eine skalierbare und sichere Umgebung für Online-Vertrieb und -Einzelhandel bietet.

![Infografiken zu Adobe Commerce-Komponenten](../../assets/playbooks/cloud-tech-stack.svg)
