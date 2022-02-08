---
title: Headless-Adobe Commerce-Architektur
description: Erfahren Sie mehr darüber, was den Ansatz der Headless-Architektur von Adobe Commerce einzigartig macht.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Headless-Adobe Commerce-Architektur

Der Vorteil der Architektur von Adobe Commerce besteht darin, dass es sich nicht um ein Allheilmittel-Angebot handelt und dass ein Händler die richtige Mischung aus Lösungen für sein Geschäft finden kann. Sie können eine PWA Studio-gestützte PWA für ihr primäres Site-Erlebnis erstellen oder Adobe Experience Manager als Ebene in komplexen Kunden-Journey verwenden, während sie gleichzeitig ein benutzerdefiniertes Frontend zum Experimentieren mit neuen Touchpoints erstellen. Keine andere Plattform kann die Zeit an die Marktvorteile und die Flexibilität anpassen, die Adobe Commerce mit seiner Headless-Architektur bietet.

![Abbildung einer Headless-Adobe Commerce-Storefront-Architektur](../../../assets/playbooks/headless-storefront-architecture.svg)

Jeder Ansatz schließt sich nicht gegenseitig aus. Kunden können ihr eigenes Frontend (head) erstellen, PWA Studio für Web-/Mobilerlebnisse verwenden und/oder Adobe Experience Manager für die Glasversion verwenden (entweder in einer vollständigen oder Hybridimplementierung).

Adobe Commerce hat für Headless-Implementierungen mit REST-APIs immer gesorgt. REST ist zwar leistungsstark, insbesondere bei der Massenverarbeitung, aber wenn es um Headless geht, ermöglichen GraphQL-APIs eine schnellere Entwicklung durch ein intuitives Entwicklererlebnis, größere Flexibilität durch Ermöglichung von Änderungen, die sich nicht auf vorhandene APIs auswirken, und bessere Leistung durch Minimierung der Datenmenge, die abgerufen wird, auf genau das, was benötigt wird.

GraphQL ist ein Branchenstandard für leistungsfähige APIs, der von vielen der führenden E-Commerce-Plattformen verwendet wird. Das ist eine gute Sache, da dies bedeutet, dass es eine bewährte Lösung ist und Fachwissen auf dem Markt existiert.

Adobe Commerce verfügt zwar über eine gekoppelte Storefront, es ist jedoch keinesfalls erforderlich, dass ein Händler dieses alte Adobe Commerce-Frontend verwendet. Ein Händler kann die branchenführenden Commerce-Services von Adobe Commerce nutzen, um die Backend-Geschäftsprozesse zu handhaben und mithilfe unserer Storefront-APIs seine eigene entkoppelte Storefront zu integrieren, um das Frontend-Erlebnis zu optimieren.

Sehen wir uns nun die verschiedenen Headless-Optionen an.

## PWA Studio

Die erste ist eine progressive Webanwendung, die mit PWA Studio entwickelt wurde. Ein Teil davon wird dadurch ermöglicht, dass eine PWA eine Headless-Storefront ist, die vom Commerce-Backend entkoppelt ist. Mit PWA Studio können Händler leistungsstarke, zuverlässige und kostengünstige PWA auf Adobe Commerce aufbauen, um erstklassige Web-Erlebnisse sowohl auf Mobilgeräten als auch auf Desktops bereitzustellen. Im Laufe der Zeit wird dies die gekoppelte Storefront als Standardoption überschreiben.

Die meisten Händler verstehen, in welche Richtung sich die Branche in Bezug auf die PWA bewegt, und viele potenzielle Blocker werden rasch entfernt.

Wochen um Woche wächst die Anzahl der Partner, die Fachwissen in PWA Studio aufbauen, und wir haben eine immer schnellere Anzahl von Kundenstarts. Die neueste Aktualisierung von PWA Studio beinhaltet Erweiterbarkeit, die zu erheblichen Fortschritten bei der Kompatibilität mit Adobe Commerce Marketplace-Erweiterungen beitragen wird.

Viele Händler fühlen sich möglicherweise nicht bereit für Headless und PWA, weil sie sich stark auf Entwickler verlassen müssen. Einer der enormen Vorteile, die sowohl die Commerce-Anwendung als auch der Kopf von Adobe Commerce bieten, besteht darin, dass sie dazu beiträgt, die Kompatibilität über Commerce-Funktionen hinweg sicherzustellen.

Um PWA leichter zugänglich und für unsere Händler leichter zu verwalten, ermöglichen wir es Geschäftsbenutzern, tägliche Inhaltsänderungen zu verwalten, neue Landingpages zu erstellen und vieles mehr mithilfe von Page Builder. Diese beiden leistungsstarken Funktionen ermöglichen die schnelle Vermarktung auf allen Geräten und Erlebnissen.

## Adobe Experience Manager

Adobe Experience Manager ist eine leistungsstarke Kombination aus Inhalten und Digital Asset Management-Anforderungen und ermöglicht es Händlern, personalisierte, inhaltsgesteuerte Erlebnisse schneller auf den Markt zu bringen, indem digitales Asset-Management mit maschinellem Lernen, Adobe Sensei-gestützten Inhalten und kundenorientiertem Journey-Management kombiniert wird.

Adobe Commerce plus Adobe Experience Manager ist eine leistungsstarke Geschichte, da die Commerce-Engine Unternehmen die Möglichkeit gibt, Commerce über Kundenschnittstellen zu ermöglichen, die auf Adobe Experience Manager basieren.

## Benutzerdefinierte Kopfzeilen

Die letzte Option, um hier zu diskutieren, ist die Möglichkeit, ein benutzerdefiniertes Frontend zu erstellen. Diese Option richtet sich an Unternehmen mit vorhandenem Fachwissen und interne Entwickler, die mit einem bestimmten Frontend-Stack wie React vertraut sind. Wenn sie keine Kenntnisse in Adobe Commerces herkömmlicher Frontend-Entwicklung haben, können sie entscheiden, dass es kostengünstiger ist, ihr eigenes React-Frontend zu erstellen.

Natürlich erfordert dieses Modell starke Kunden- oder Systemintegrationsfähigkeiten und -ressourcen für die Frontend-Entwicklung und Sie erhalten nicht den Vorteil einer nativen Kompatibilität mit Dingen wie Page Builder, die Sie mit PWA Studio erhalten. Jedes Mal, wenn ein Händler etwas ganz Eigenes baut, verlieren sie möglicherweise die Vorteile der Markteinführungszeit.

Benutzerdefinierte Frontend ermöglichen auch Innovationen und Experimente. Es wird viel über AR/VR oder Voice Commerce gesprochen, und eine Architektur wie die von Adobe Commerce ermöglicht es Händlern, diese Optionen zu erforschen, ohne ihre bestehenden Webstores zu beeinträchtigen.
