---
title: Überblick über das selbstständige Hosting
description: Erfahren Sie mehr über Best Practices für das selbstständige Hosting. Die Themen reichen von Sicherheitselementen bis hin zur Notfallwiederherstellung und vieles mehr. Diese Themen sollen Unternehmen helfen, die beschlossen haben, ihre eigene Version von Adobe Commerce zu hosten. Die präsentierten Artikel sind nicht alle inklusiv, sollten aber eine gute Palette von Konzepten bieten, um eine sichere, stabile und widerstandsfähige Website zu fördern.
landing-page-description: Lernen Sie einige Konzepte und Aspekte kennen, die Sie beim Hosten von Adobe Commerce selbst beachten sollten.
short-description: Erfahren Sie Strategien und Konzepte für das Hosting von Adobe Commerce selbst.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 63f552f3-836c-4a07-96c3-c0e00614fe39
feature: Install
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Selbstständiges Hosting in Adobe Commerce - Überblick

Wenn Sie über den Übergang zu einer E-Commerce-Plattform wie Adobe Commerce nachdenken, haben Sie den Luxus von Optionen. Mit diesen Optionen sind jedoch zusätzliche Kosten, Risiken und Verbindlichkeiten zu berücksichtigen. Das Hosten einer Commerce-Site kann mit einer gepackten Lösung erfolgen, z. B. [Adobe Commerce auf Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}, wo Infrastruktur, Server, E-Mail, SSL-Zertifikate und viele andere vorkonfiguriert sind und einsatzbereit sind. Wenn Sie eine gute Hostinglösung wie Adobe Commerce in der Cloud-Infrastruktur finden, wird der gesamte Prozess vereinfacht. Es gibt überzeugende Gründe für das selbstständige Hosting Ihrer Commerce-Site. Auf den zugehörigen Seiten finden Sie viele Themen, die Einblicke und Anleitungen zu den Diensten, Techniken und Konzepten bieten, die das Self-Hosting bietet. Die Informationen hier sind nicht vollständig, und es wird nicht erwartet, dass Sie alle Vorschläge umsetzen. Diese Artikel können Ihnen jedoch dabei helfen, die Ideen und Konzepte zu verstehen, die das selbstständige Hosting von Adobe Commerce so stabil und sicher wie möglich machen.

Wenn Sie nicht mit Adobe Commerce in der Cloud-Infrastruktur arbeiten, werden die Begriffe Self-Hosting oder On-Premise verwendet oder sogar On-Premise. In Gebäuden bedeutet nicht nur in einem Rechenzentrum in einem Gebäude, das ein Unternehmen besitzt. Dieser Begriff stellt alles dar, was nicht von Adobe Commerce in seiner Infrastruktur verwaltet wird. Es gibt Hosting-Unternehmen, die sich für Adobe Commerce eignen. Sie werden auch als Self-Hosting oder On-Premise-Unternehmen betrachtet.

In Bezug auf Adobe Commerce und Magento Open Source funktionieren die meisten Ratschläge und Tipps für beide Versionen. Auch wenn dies nicht direkt angegeben wird, ist die Erwartung, dass es für beide gilt. Bei diesem Thema der Self-Hosting-Optionen für Adobe Commerce werden beide Versionen berücksichtigt. Und schließlich sind die meisten Themen relevant für [Adobe Commerce auf Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"} wird als Hosting-Anbieter ausgewählt.

## Satz auf Terminologieebene

Die folgenden Begriffe werden häufig in allen Experience League-Artikeln verwendet, wenn Sie mit dem DevOps-Team sprechen und mit dem Support des Unternehmens arbeiten:

* **DevOps** ist ein Begriff, der verwendet wird, um die Teams zu beschreiben, die die Servereinrichtung, -konfiguration, -verwaltung, SSL-Zertifikate und alles andere über die eigentlichen Server und Dienste, die zum Ausführen einer Adobe Commerce-Site verwendet werden, verarbeiten. Dieser Begriff wird verwendet, um zu bestimmen, wann die Verantwortung eines Entwicklers normalerweise endet und wo der Test und die Unterstützung durch ein Infrastrukturteam beginnen.

* **Sicherheitskonzepte** umfasst verschiedene Themen und Überlegungen, um die Adobe Commerce-Codebase, Dateien und das Dateisystem auf den Servern zu erstellen, sowie Konfigurationen oder Aktualisierungen, die die Angriffsfläche für viele bekannte Exploit-Muster reduzieren.

* **Monitoring-Tools** umfasst einige vorhandene Tools und Dienste, die Adobe Commerce-Websites überwachen. Diese Tools können manchmal Tipps zur Verbesserung von Dingen geben oder Probleme und Sicherheitslücken aufdecken.

* **Notfallwiederherstellung** hilft Ihnen, einige Konzepte und Überlegungen für das unglückliche Ereignis eines beschädigten oder ausgebeuteten Projekts bereitzustellen.

* **Leistungstipps** Hier finden Sie einige Tipps und Anleitungen, wie Sie die Adobe Commerce-Anwendung so leistungsstark wie möglich gestalten können.

* **Unangemessener Akteur** ist der Begriff, der für eine Person oder ein Team verwendet wird, die versucht, etwas böswillig oder nicht autorisiert zu tun. Sie ist nicht auf die Commerce-Anwendung beschränkt, sondern erstreckt sich auch auf die Infrastruktur oder Komponenten, die mit der Website verbunden sind.

* **Web Application Firewall** (WAF) hilft bei der Überwachung der einzelnen Anforderungsüberschriften in die Commerce-Anwendung und blockiert bekannte Muster und Exploits. Häufig wird eine WAF zusammen mit benutzerdefinierten Filtern und Regeln verwendet, um DDOS-Angriffe zu verwalten.

* **Distributed Denial of Service** (DDoS) ist eine Angriffsmethode, um zu erzwingen, dass die Server, auf denen die Website ausgeführt wird, mit falschen Anfragen mit genügend Volumen genutzt werden, sodass sie nicht mehr auf legitime Anfragen reagieren können.

## Wie geht es weiter?

Diese Themen sind in keiner speziellen Reihenfolge aufgeführt. Sie sollen Gesprächspunkte mit einem Entwickler von DevOps, dem Commerce-Architekten und allen anderen Personen bereitstellen, die an dieser wichtigen Entscheidung beteiligt sind, wo und wie Adobe Commerce aufgenommen werden soll.

{{$include /help/_includes/hosting-related-links.md}}
