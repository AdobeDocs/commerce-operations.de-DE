---
title: Globale Referenzarchitektur
description: Nutzen Sie eine globale Referenzarchitektur, um Ihre Adobe Commerce-Implementierung optimal zu nutzen.
exl-id: a18529a3-da9b-4e1b-8048-0a906e65c740
feature: Deploy
source-git-commit: d33d1e24c38984d0abf0c7f8f5ad2eb804ff621d
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Globale Referenzarchitektur (GRA)

>[!VIDEO](https://video.tv.adobe.com/v/3410528/?quality=12&learn=on)

Wenn Sie Unternehmen betreiben, die über mehrere Sites für mehrere Marken auf mehreren lokalen Märkten verfügen (mit lokalisierten Währungen, Sprachen, Medien, freigegebenen Katalogen und individuellen Warenkörben) und unnötige Kosten für die Implementierung derselben Funktionen und Integrationen vermeiden möchten, ist die globale Referenzarchitektur (GRA) immer eine gute Option.

![Tabelle, die die Kosten der Divergenz in der Architektur erklärt](../../../assets/playbooks/divergent-architecture.svg)

![Tabelle mit den Kosten für konsolidierte Architektur](../../../assets/playbooks/consolidated-architecture.svg)

Die GRA lautet:

- Implementierungskonzept
- Implementierungsstrategie
- Ein Modell für die Prozesssteuerung

GRA ist nicht:

- Eine Produktfunktion
- Eindeutig für jede Commerce-Plattform
- Nur für globale Geschäftsanwendungsfälle

GRA-Auswirkungen:

- Auslieferung von Code

   - Basiert auf zielspezifischen Code-Repositorys, die unterschiedliche Erlebnisse bereitstellen.

- Integration von Unternehmenssystemen

   - Konsolidiert Verbindungen zu Unternehmenssystemen nach Marke und/oder Region.

- Wie die Anpassung entwickelt und verwaltet wird

   - Stellt sicher, dass Anpassungen zentralisiert und domänenspezifisch sind, sodass alle Anpassungsbemühungen aus ganzheitlicher Sicht für das Unternehmen durchgeführt werden.

- Wie neue Märkte aktiviert werden

   - Vereinfacht die Freigabe mehrerer Kanäle und Märkte, die sonst erheblich mehr Zeit und Geld kosten würden.

>[!TIP]
>
>Siehe [GRA-Beispiele](examples.md).
