---
title: Handelsarchitektur ohne Headless-Adobe
description: Erfahren Sie, was den Headless-Architektur-Ansatz von Adobe Commerce einzigartig macht.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Handelsarchitektur ohne Headless-Adobe

Der Vorteil der Architektur von Adobe Commerce besteht darin, dass es sich nicht um ein Allheilmittel-Angebot handelt und dass ein Händler die richtige Lösungsmischung für sein Unternehmen finden kann. Sie können eine PWA Studio-basierte PWA für das primäre Site-Erlebnis erstellen oder Adobe Experience Manager als Ebene in komplexen Kunden-Journey verwenden, während sie gleichzeitig ein benutzerdefiniertes Frontend zum Experimentieren mit neuen Touchpoints erstellen. Keine andere Plattform kann die Zeit an die Marktvorteile und die Flexibilität anpassen, die Adobe Commerce mit seiner Headless-Architektur bietet.

![Abbildung einer Headless-Adobe-Commerce-Storefront-Architektur](../../../assets/playbooks/headless-storefront-architecture.svg)

Jeder Ansatz schließt sich nicht gegenseitig aus. Kunden können ihr eigenes Frontend (head) erstellen, PWA Studio für Web-/Mobilerlebnisse verwenden und/oder Adobe Experience Manager für die Glasversion verwenden (entweder in einer vollständigen oder Hybridimplementierung).

Adobe Commerce hat für Headless-Implementierungen mit REST-APIs immer gesorgt. REST ist zwar leistungsstark, insbesondere bei der Massenverarbeitung, aber wenn es um Headless geht, ermöglichen GraphQL-APIs eine schnellere Entwicklung durch ein intuitives Entwicklererlebnis, größere Flexibilität durch Ermöglichung von Änderungen, die sich nicht auf vorhandene APIs auswirken, und bessere Leistung durch Minimierung der Datenmenge, die abgerufen wird, auf genau das, was benötigt wird.

GraphQL ist ein Branchenstandard für leistungsfähige APIs, der von vielen der führenden E-Commerce-Plattformen verwendet wird. Das ist eine gute Sache, da dies bedeutet, dass es eine bewährte Lösung ist und Fachwissen auf dem Markt existiert.

Adobe Commerce verfügt zwar über eine gekoppelte Storefront, doch ist es keinesfalls erforderlich, dass ein Händler diese Adobe Commerce-Legacy-Frontend verwendet. Ein Händler kann die branchenführenden Commerce-Services von Adobe Commerce nutzen, um die Backend-Geschäftsprozesse zu handhaben und mithilfe unserer Storefront-APIs seine eigene entkoppelte Storefront zu integrieren, um das Frontend-Erlebnis zu optimieren.

Sehen wir uns nun die verschiedenen Headless-Optionen an.

## PWA Studio

Die erste ist eine progressive Webanwendung, die mit PWA Studio entwickelt wurde. Ein Teil davon wird dadurch ermöglicht, dass eine PWA eine Headless-Storefront ist, die vom Commerce-Backend entkoppelt ist. Mit PWA Studio können Händler neben Adobe Commerce leistungsstarke, zuverlässige und kostengünstige PWA erstellen, die sowohl auf Mobilgeräten als auch auf Desktops erstklassige Web-Erlebnisse bieten. Im Laufe der Zeit wird dies die gekoppelte Storefront als Standardoption überschreiben.

Die meisten Händler verstehen, in welche Richtung sich die Branche in Bezug auf die PWA bewegt, und viele potenzielle Blocker werden rasch entfernt.

Wochen um Woche wächst die Anzahl der Partner, die Fachwissen in PWA Studio aufbauen, und wir haben eine immer schnellere Anzahl von Kundenstarts. Die letzte Aktualisierung von PWA Studio umfasste Erweiterbarkeit, die zu erheblichen Fortschritten bei der Kompatibilität mit Adobe Commerce Marketplace-Erweiterungen beitragen wird.

Viele Händler fühlen sich möglicherweise nicht bereit für Headless und PWA, weil sie sich stark auf Entwickler verlassen müssen. Einer der enormen Vorteile, die sowohl die Commerce-Anwendung als auch der Kopf von Adobe Commerce bieten, besteht darin, dass sie zur Gewährleistung der Kompatibilität über Commerce-Funktionen hinweg beiträgt.

Um PWA leichter zugänglich und für unsere Händler leichter zu verwalten, ermöglichen wir es Geschäftsbenutzern, tägliche Inhaltsänderungen zu verwalten, neue Landingpages zu erstellen und vieles mehr mithilfe von Page Builder. Diese beiden leistungsstarken Funktionen ermöglichen die schnelle Vermarktung auf allen Geräten und Erlebnissen.

## Adobe Experience Manager

Dank der leistungsstarken Kombination aus Content und Digital Asset Management-Anforderungen ermöglicht Adobe Experience Manager Händlern die schnellere Bereitstellung personalisierter, inhaltsgesteuerter Erlebnisse auf dem Markt, sodass Digital Asset Management mit maschinellem Lernen, Adobe Sensei-gestützten Inhalten und kundenorientiertem Journey-Management kombiniert werden kann.

Adobe Commerce plus Adobe Experience Manager ist eine leistungsstarke Geschichte, da die Commerce-Engine es Unternehmen ermöglicht, Commerce über Kundenschnittstellen zu ermöglichen, die auf Adobe Experience Manager basieren.

## Benutzerdefinierte Kopfzeilen

Die letzte Option, um hier zu diskutieren, ist die Möglichkeit, ein benutzerdefiniertes Frontend zu erstellen. Diese Option richtet sich an Unternehmen mit vorhandenem Fachwissen und interne Entwickler, die mit einem bestimmten Frontend-Stack wie React vertraut sind. Wenn sie keine Kenntnisse in der herkömmlichen Frontend-Entwicklung von Adobe Commerce haben, können sie entscheiden, dass es kostengünstiger ist, ihr eigenes React-Frontend zu erstellen.

Natürlich erfordert dieses Modell starke Kunden- oder Systemintegrationsfähigkeiten und -ressourcen für die Frontend-Entwicklung und Sie erhalten nicht den Vorteil einer nativen Kompatibilität mit Dingen wie Page Builder, die Sie mit PWA Studio erhalten. Jedes Mal, wenn ein Händler etwas ganz Eigenes baut, verlieren sie möglicherweise die Vorteile der Markteinführungszeit.

Benutzerdefinierte Frontend ermöglichen auch Innovationen und Experimente. Es wird viel über AR/VR oder Voice Commerce gesprochen, und eine Architektur wie Adobe Commerce&#39;s ermöglicht es Händlern, diese Optionen zu erkunden, ohne ihre bestehenden Webstores zu beeinträchtigen.
