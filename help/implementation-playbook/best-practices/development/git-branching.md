---
title: Best Practices für Git-Verzweigungen
description: Erfahren Sie mehr über verschiedene Verzweigungsstrategien für die Quellcodeverwaltung.
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Best Practices für Git-Verzweigungen

Source-Code durchläuft während des Entwicklungsprozesses mehrere Stabilitätsphasen:

- Aktive Entwicklung
- Anfängliche Code-Integration
- Code-Integration für Qualitätssicherung (QA)
- Code-Integration für Endbenutzer-Akzeptanztests (UAT)
- Integration des endgültigen Codes für Produktionsversionen

## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Filialverwaltung

Jede Entwicklungsphase sollte über eine entsprechende Verzweigung in Git verfügen, um Code-Änderungen zu verfolgen und den Bereitstellungsprozess zu erleichtern:

- **Aufgabenverzweigung** Hier übertragen Entwickler ihre individuellen Code-Änderungen bei der Implementierung bestimmter Aufgaben wie Funktionen und Fehlerbehebungen.
- **Entwicklungsverzweigung** Hier führen mehrere Entwicklerinnen und Entwickler Änderungen aus ihren einzelnen Aufgabenverzweigungen zu einer einzigen Entwicklungsverzweigung zusammen, um automatisierte Integrationstests durchzuführen. Diese Verzweigung wird in einer Entwicklungsumgebung bereitgestellt.
- **QA-Verzweigung** Hier führen Entwickler Änderungen zusammen, nachdem die Entwicklung abgeschlossen ist und der Code alle automatisierten Integrationstests und Code-Prüfungen bestanden hat. Diese Verzweigung wird in der QS-Umgebung für manuelle QS-Tests bereitgestellt.
- **Stable/UAT branch** - Wo Code zusammengeführt wird, nachdem er manuelle QA-Tests bestanden hat. Diese Verzweigung wird in einer UAT-Umgebung für Benutzerakzeptanztests bereitgestellt.
- **Produktions-/Versionszweig** - Hier wird Code zusammengeführt, nachdem er UAT übergeben hat. Diese Verzweigung wird für eine Version in der Produktion bereitgestellt.

>[!TIP]
>
>Adobe Commerce in Cloud-Infrastrukturprojekten enthalten spezifische Verzweigungen, die verschiedenen Umgebungen entsprechen. Siehe [Pro-Projekt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html) und [Starter-Projekt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html) im _Cloud-Handbuch_.

## Verzweigungsstrategien

Es gibt mehrere Verzweigungsstrategien, die Sie verwenden können. Wählen Sie eine Strategie aus, die für Ihr Entwicklungsteam und die Komplexität Ihres Projekts am besten geeignet ist.

Weitere Informationen finden Sie in den folgenden externen Ressourcen:

- [Verzweigungs-Workflows](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [Verteilte Workflows](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [Muster für die Verwaltung von Quell-Code-Verzweigungen](https://martinfowler.com/articles/branching-patterns.html)
- [Ein erfolgreiches Git-Verzweigungsmodell](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub-Fluss](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab-Fluss](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
