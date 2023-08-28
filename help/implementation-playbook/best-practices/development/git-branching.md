---
title: Best Practices für Git-Verzweigungen
description: Erfahren Sie mehr über verschiedene Verzweigungsstrategien für die Verwaltung von Quellcode.
feature: Best Practices
role: Developer
source-git-commit: 9b1c3f7ca56cb6baf262bbd4abc732a30a7eb0ed
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Best Practices für Git-Verzweigungen

Der Quellcode durchläuft während des Entwicklungsprozesses mehrere Stabilitätsphasen:

- Aktive Entwicklung
- Erstmalige Code-Integration
- Codeintegration für Qualitätssicherung (QA)
- Codeintegration für Endbenutzer-Akzeptanztests (UAT)
- Abschließende Codeintegration für Produktionsversionen

## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Zweigverwaltung

Jede Entwicklungsphase sollte über eine entsprechende Verzweigung in Git verfügen, um Code-Änderungen zu verfolgen und den Bereitstellungsprozess zu erleichtern:

- **Aufgabenverzweigung**—Wenn Entwickler ihre individuellen Code-Änderungen bei der Implementierung bestimmter Aufgaben übernehmen, wie Funktionen und Fehlerbehebungen.
- **Entwicklungszweig**—Wenn mehrere Entwickler Änderungen von ihren einzelnen Aufgabenverzweigungen zu einer einzigen Entwicklungszweig zusammenführen, um automatisierte Integrationstests durchzuführen. Diese Verzweigung wird in einer Entwicklungsumgebung bereitgestellt.
- **QA-Verzweigung**—Wenn Entwickler Änderungen nach Abschluss der Entwicklung zusammenführen und der Code alle automatisierten Integrationstests und Codeüberprüfungen bestanden hat. Diese Verzweigung wird für manuelle Qualitätssicherungstests in der QS-Umgebung bereitgestellt.
- **Stable-/UAT-Verzweigung**—Wo Code zusammengeführt wird, nachdem er manuelle QA-Tests bestanden hat. Diese Verzweigung wird für Benutzerakzeptanztests in einer UAT-Umgebung bereitgestellt.
- **Produktions-/Versionsverzweigung**—Wo Code zusammengeführt wird, nachdem er UAT passiert. Diese Verzweigung wird für eine Version in der Produktion bereitgestellt.

>[!TIP]
>
>Adobe Commerce in Cloud-Infrastrukturprojekten enthalten spezifische Verzweigungen, die verschiedenen Umgebungen entsprechen. Siehe [Pro Projekt-Workflow](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html) und [Workflow für Starterprojekte](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html) im _Cloud-Anleitung_.

## Branch-Strategien

Es gibt mehrere Verzweigungsstrategien, die Sie verwenden können. Wählen Sie eine Strategie aus, die am besten für Ihr Entwicklungsteam und die Komplexität Ihres Projekts geeignet ist.

Weitere Informationen finden Sie in den folgenden externen Ressourcen:

- [Verzweigungs-Workflows](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [Verteilte Workflows](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [Muster für die Verwaltung von Quellcodeverzweigungen](https://martinfowler.com/articles/branching-patterns.html)
- [Ein erfolgreiches Git-Verzweigungsmodell](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub-Fluss](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab-Fluss](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
