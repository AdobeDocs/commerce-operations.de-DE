---
title: Adobe Commerce-Microservices
description: Sie können zwischen Gesundheits- und Mikrodiensten unterscheiden, da sie Adobe Commerce betreffen.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Headless- und Microservices

Es ist wichtig, Headless nicht mit Mikrodiensten zu verwechseln. Oft hören wir Gespräche über Mikrodienste im selben Satz wie Headless. Sie sind völlig andere Dinge. Sie können zusammen verwendet werden, aber sie sind völlig andere Konzepte.

Eine Microservices-Architektur ist ein Begriff, der die Praxis beschreibt, eine Anwendung in eine Sammlung kleinerer, lose gekoppelter Dienste aufzuteilen. Microservices ermöglichen es, einzelne Backend-Dienste wie folgt zu gestalten:

- **Isoliert voneinander** - Beispielsweise ist der Preisdienst nicht vom Katalogdienst abhängig.

- **Bereitstellung eines la carte** - Kunden stellen nur die Teile der Anwendung bereit, die sie benötigen.

- **Eigene Skalierung** - Ressourcen können Services mit hoher Nachfrage zugewiesen werden, z. B. der Inventarsuche.

- **Autom entwickelt** - Kann unabhängig voneinander entwickelt und eingesetzt werden.

Microservices haben nichts damit zu tun, den Kopf vom Commerce-Stack oder den APIs abzuschneiden. Wenn wir an jene Commerce-Dienste im Kerncode denken, die sich im Backoffice von Adobe Commerce befinden, geht es darum, diese Dienste voneinander zu isolieren. Eine Microservices-Architektur bricht also locker alle diese Dienste wie Preisdienste, Katalogdienst und Inventardienst auf und macht jeden isoliert voneinander. Dadurch wird sichergestellt, dass sie ein &quot;la cart&quot; sind, sodass Sie nicht alle Adobe Commerce-Produkte auf einmal kaufen und bereitstellen müssen.

Microservices können unabhängig skaliert und autonom entwickelt werden. Microservices entsprechen einem mehrmandantenfähigen SaaS-Entwicklungsprozess. Viele moderne SaaS-Produkte mit mehreren Mandanten werden mit einem Multi-Service-Ansatz entwickelt. Sogar die SaaS-Produkte der Adobe, wie Order Management, das neue AI-gestützte Produkt-Recommendations-Tool und andere SaaS-Komponenten von Adobe Commerce, werden mithilfe eines Microservices-Ansatzes entwickelt. Um es ganz deutlich zu sagen: Adobe Commerce 2.4.x ist keine Microservices-Architektur, sondern eine Headless-Architektur.
