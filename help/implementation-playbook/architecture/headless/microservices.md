---
title: Adobe Commerce Microservices
description: Sie können zwischen Gesundheitsdiensten und Microservices unterscheiden, da sie Adobe Commerce betreffen.
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
source-git-commit: 4e8f6ce05c14195433e7c46e6090a93a76b8b5f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Headless- und Microservices

Es ist wichtig, Headless nicht mit Mikrodiensten zu verwechseln. Oft hören wir Gespräche über Mikrodienste im selben Satz wie Headless. Sie sind völlig andere Dinge. Sie können zusammen verwendet werden, aber sie sind völlig andere Konzepte.

Eine Microservices-Architektur ist ein Begriff, der die Praxis beschreibt, eine Anwendung in eine Sammlung kleinerer, lose gekoppelter Dienste aufzuteilen. Microservices ermöglichen es, einzelne Backend-Dienste wie folgt zu gestalten:

- **Isoliert voneinander**—Beispielsweise ist der Preisdienst nicht vom Katalogdienst abhängig.

- **Bereitstellung eines la carte**—Kunden stellen nur die Teile der Anwendung bereit, die sie benötigen.

- **Eigene Skalierung**- Ressourcen können Diensten mit hoher Nachfrage zugewiesen werden, z. B. der Inventarsuche.

- **Autonome Entwicklung**—Kann unabhängig voneinander entwickelt und eingesetzt werden.

Microservices haben nichts damit zu tun, den Kopf vom Commerce-Stack oder den APIs abzuschneiden. Wenn wir an jene Commerce-Dienste im Kerncode denken, die sich im Backoffice von Adobe Commerce befinden, geht es darum, diese Dienste voneinander zu isolieren. Eine Microservices-Architektur bricht also locker alle diese Dienste wie Preisdienste, Katalogdienst und Inventardienst auf und macht jeden isoliert voneinander.

Microservices können unabhängig skaliert und autonom entwickelt werden. Microservices entsprechen einem mehrmandantenfähigen SaaS-Entwicklungsprozess. Viele moderne SaaS-Produkte mit mehreren Mandanten werden mit einem Multi-Service-Ansatz entwickelt. Sogar die SaaS-Produkte der Adobe, wie Order Management, das neue AI-gestützte Produkt-Recommendations-Tool und andere SaaS-Komponenten von Adobe Commerce, werden mithilfe eines Microservices-Ansatzes entwickelt. Um es ganz deutlich zu sagen: Adobe Commerce 2.4.x ist keine Mikrodienstarchitektur, sondern eine Headless-Architektur.
