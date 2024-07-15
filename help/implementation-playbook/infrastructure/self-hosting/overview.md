---
title: Überblick über das selbstständige Hosting
description: Erfahren Sie mehr über Best Practices für das selbstständige Hosting. Die Themen reichen von Sicherheitselementen bis hin zur Notfallwiederherstellung und vieles mehr. Diese Themen sollen Unternehmen helfen, die beschlossen haben, ihre eigene Version von Adobe Commerce zu hosten. Die präsentierten Artikel sind nicht alle inklusiv, sollten aber eine gute Palette von Konzepten bieten, um eine sichere, stabile und widerstandsfähige Website zu fördern.
landing-page-description: Lernen Sie einige Konzepte und Aspekte kennen, die Sie beim Hosten von Adobe Commerce selbst beachten sollten.
short-description: Erfahren Sie Strategien und Konzepte für das Hosting von Adobe Commerce selbst.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 1c63d082-c6fb-4795-81cd-75d097c03e6b
feature: Install
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# Selbstständiges Hosting in Adobe Commerce - Überblick

Wenn Sie über den Übergang zu einer E-Commerce-Plattform wie Adobe Commerce nachdenken, haben Sie den Luxus von Optionen. Mit diesen Optionen sind jedoch zusätzliche Kosten, Risiken und Verbindlichkeiten zu berücksichtigen. Das Hosten einer Commerce-Site kann mit einer gepackten Lösung wie [Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} erfolgen, in der Infrastruktur, Server, E-Mail, SSL-Zertifikate und viele andere vorkonfiguriert sind und einsatzbereit sind. Die Suche nach einer guten Hostinglösung wie Adobe Commerce in der Cloud-Infrastruktur erleichtert den gesamten Prozess. Es gibt zwingende Gründe für das selbstständige Hosting Ihrer Commerce-Site. Auf den zugehörigen Seiten finden Sie viele Themen, die Einblicke und Anleitungen zu den Diensten, Techniken und Konzepten bieten, die das Self-Hosting bietet. Die Informationen hier sind nicht vollständig, und es wird nicht erwartet, dass Sie alle Vorschläge umsetzen. Diese Artikel können Ihnen jedoch dabei helfen, die Ideen und Konzepte zu verstehen, die das selbstständige Hosting von Adobe Commerce so stabil und sicher wie möglich machen.

Wenn Sie nicht mit Adobe Commerce in der Cloud-Infrastruktur arbeiten, werden die Begriffe Self-Hosting oder On-Premise verwendet oder sogar On-Premise verwendet. In Gebäuden bedeutet nicht nur in einem Rechenzentrum in einem Gebäude, das ein Unternehmen besitzt. Dieser Begriff stellt alles dar, was nicht von Adobe Commerce in seiner Infrastruktur verwaltet wird. Es gibt Hosting-Unternehmen, die sich für Adobe Commerce eignen. Sie werden auch als selbstständiges Hosting oder On-Premise-Unternehmen betrachtet.

In Bezug auf Adobe Commerce und Magento Open-Source, die meisten Ratschläge und Tipps für beide Versionen. Auch wenn dies nicht direkt angegeben wird, ist die Erwartung, dass es für beide gilt. Bei diesem Thema der Self-Hosting-Optionen für Adobe Commerce werden beide Versionen berücksichtigt. Und schließlich sind die meisten Themen für [Adobe Commerce in der Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} relevant, da diese als Hosting-Anbieter ausgewählt ist.

## Satz auf Terminologieebene

Die folgenden Begriffe werden in allen Experience League-Artikeln verwendet, wenn Sie mit dem DevOps-Team sprechen und mit dem Support des Unternehmens arbeiten:

* **DevOps** ist ein Begriff, der verwendet wird, um die Teams zu beschreiben, die die Servereinrichtung, -konfiguration, -verwaltung, SSL-Zertifikate und alles andere über die eigentlichen Server und Dienste, die zum Ausführen einer Adobe Commerce-Site verwendet werden, verwalten. Dieser Begriff wird verwendet, um zu bestimmen, wann die Verantwortung eines Entwicklers normalerweise endet und wo der Test und die Unterstützung durch ein Infrastrukturteam beginnen.

* **Sicherheitskonzepte** umfassen verschiedene Themen und Überlegungen, um die Adobe Commerce-Codebasis, Dateien und das Dateisystem auf den Servern sowie Konfigurationen oder Aktualisierungen zu erstellen, die die Angriffsfläche für viele bekannte Exploit-Muster reduzieren.

* **Monitoring Tools** umfasst einige vorhandene Tools und Dienste, die Adobe Commerce-Websites überwachen. Diese Tools können manchmal Tipps zur Verbesserung von Dingen geben oder Probleme und Sicherheitslücken aufdecken.

* **Disaster Recovery** hilft Ihnen, einige Konzepte und Überlegungen für das unglückliche Ereignis eines beschädigten oder ausgenutzten Projekts bereitzustellen.

* **Leistungstipps** enthalten einige Tipps und Anleitungen, wie Sie die Adobe Commerce-Anwendung so leistungsstark wie möglich gestalten können.

* **Unangemessener Schauspieler** ist der Begriff, der für eine Person oder ein Team verwendet wird, die versucht, etwas Bösartiges oder Unberechtigtes zu tun. Sie ist nicht auf die Commerce-Anwendung beschränkt, sondern erstreckt sich auch auf die Infrastruktur oder Komponenten, die mit der Website verbunden sind.

* Die **Web Application Firewall** (WAF) unterstützt Sie dabei, die einzelnen Anfragen in die Commerce-Anwendung zu überführen und bekannte Muster und Exploits zu blockieren. Häufig wird eine WAF zusammen mit benutzerdefinierten Filtern und Regeln verwendet, um DDOS-Angriffe zu verwalten.

* **Distributed Denial of Service** (DDoS) ist eine Angriffsmethode, um zu erzwingen, dass die Server, auf denen die Website ausgeführt wird, mit falschen Anfragen mit genügend Volumen genutzt werden, sodass sie nicht mehr auf legitime Anfragen reagieren können.

## Wie geht es weiter?

Diese Themen sind in keiner speziellen Reihenfolge aufgeführt. Sie sollen Gesprächspunkte mit einem Entwickler von DevOps, dem Commerce-Architekten und allen anderen Personen bereitstellen, die an dieser wichtigen Entscheidung beteiligt sind, wo und wie Adobe Commerce aufgenommen werden soll.

{{$include /help/_includes/hosting-related-links.md}}
