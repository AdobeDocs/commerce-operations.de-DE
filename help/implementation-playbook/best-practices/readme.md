---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---
# Best Practices: Workflow für die Inhaltserstellung

In diesem Dokument wird der Benutzer-Workflow zum Anfordern von Änderungen oder Ergänzungen des *[Best Practices] (https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html*-Inhalts im *Adobe Commerce-Implementierungs-Playbook* beschrieben.

## Wer kann eine Anfrage erstellen?

Adobe akzeptiert Anfragen von internen und externen Stakeholdern, einschließlich, aber nicht beschränkt auf Einzelpersonen in den folgenden Gruppen:

- Adobe-Partner
- Adobe CTAG (Customer Technical Advisory Group), Support, Customer Success, Engineering-Teams

## Wie erstelle ich eine Anfrage?

**Interne Stakeholder** können Anfragen einreichen, indem sie eine Jira-Anfrage im COMDOX-Projekt öffnen. **Externe Stakeholder** können Anfragen senden, indem sie ein [GitHub-Problem](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) in diesem Repository öffnen.

Sie können die folgenden Arten von Anfragen senden:

- Ideen für neue Inhalte
- Aktualisierungen an bereits veröffentlichten Inhalten
- Veröffentlichen neuer Inhalte, die von Stakeholdern oder der Community bereitgestellt werden

## Wie sieht der Gesamtprozess aus?


**Erstellen eines Jira-Tickets oder -Problems** - Interne Stakeholder erstellen ein Jira-Ticket im COMDOX-Projekt. Externe Stakeholder reichen ein GitHub-Problem ein. Geben Sie vollständige Details in das Jira- oder [GitHub-Problem](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) ein, damit das Team den Kontext verstehen und die Anfrage priorisieren kann.

**Das Adobe-Projektteam bewertet und priorisiert die Anfrage**—Das Team überwacht regelmäßig Anfragen, um die Priorität zu bestimmen und die angeforderten Änderungen zur Aufnahme in die Best Practices im Implementierungs-Playbook zu bewerten. Beispielsweise könnte das Team festlegen, dass die angeforderten Inhalte nicht zu einem neuen Thema mit Best Practices, sondern zu der vorhandenen Produktdokumentation auf Experience League oder der Adobe Developer-Site hinzugefügt werden sollen.

Wenn eine Anfrage nicht genügend Informationen enthält, fordert das Team vom Antragsteller zusätzliche Informationen an. Wenn der Antragsteller nicht innerhalb von 14 Tagen antwortet, schließt das Team die Anfrage.

**Erstellen oder Aktualisieren von Inhalten** Die Erstellung von Inhalten wird gemäß dem Prozess abgeschlossen, der im [Adobe Experience League Contributor Guide“ ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). Je nach Anfrage kann die Konvertierung neuen Inhalts in Markdown, die Erstellung eines Themas oder die Aktualisierung eines vorhandenen Themas die Aufgabe sein.

**Inhaltsüberprüfung, -validierung und -veröffentlichung**-Inhalte werden während der Themenerstellung oder -aktualisierung mit (GitHub[Pull-Anfragen) ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). Alle Inhalte müssen einer redaktionellen Überprüfung unterzogen werden. Die technische Überprüfung ist optional und vom Inhalt abhängig. Wenn keine technische Überprüfung erforderlich ist, wird der Prozess nur mit einer redaktionellen Überprüfung fortgesetzt. Dieser Prozess kann mehrere Iterationen dauern, bis der Inhalt genehmigt wird.

Nachdem ein Artikel genehmigt wurde, kann die Pull-Anforderung mit der Produktionsverzweigung zusammengeführt werden. Das Zusammenführen sollte durch den Autor erfolgen. Nachdem ein Thema zusammengeführt wurde, kann es sofort mithilfe eines manuellen Prozesses oder automatisch bei der nächsten Ausführung des Veröffentlichungsauftrags in der Produktion veröffentlicht werden. Veröffentlichungsaufträge werden in der Regel alle zwei Stunden ausgeführt.

**Neue Inhaltsbenachrichtigung**-Adobe bietet einen Abschnitt *Neue Funktionen* zum Thema [Übersicht über Best Practices](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en), um Benutzende über kürzlich veröffentlichte oder aktualisierte Themen zu informieren. Adobe wird auch neue Best Practices für Inhalte mithilfe bestehender Kanäle wie Marketing und interne Kommunikation bekannt machen.

## Backlog und Kanban-Board

Um Duplizierungen zu vermeiden, werden Anforderungen, die erstellt und priorisiert wurden, im Jira-Rückstand des COMDOX-Projekts und im GitHub[Problemeprojekt ](https://github.com/orgs/AdobeDocs/projects/6/views/1). Interne Interessenträger werden ermutigt, sich an das Abstimmungssystem in Jira zu wenden, um Anträge zu unterstützen, die sie für notwendig oder relevant halten. Die Abstimmung hilft dem Projekt-Team mit Best Practices auch, die Art der Inhalte zu verstehen, die von den Stakeholdern erwartet und geschätzt werden. Anforderungen, die noch nicht priorisiert und überprüft wurden, werden im Rückstand angezeigt, bis sie in die aktiven Spuren im Kanban-Board verschoben werden.

Auf das Kanban-Board können interne Benutzende zugreifen, um anzuzeigen (und/oder zu überwachen), an welchen Inhalten gearbeitet wird und welche Fortschritte erzielt wurden. Nur aktive Anfragen werden auf dieser Pinnwand angezeigt.
