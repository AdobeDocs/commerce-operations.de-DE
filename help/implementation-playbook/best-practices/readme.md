---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---
# Best Practices: Workflow zur Inhaltserstellung

In diesem Dokument wird der Benutzer-Workflow beschrieben, mit dem Änderungen oder Ergänzungen des Inhalts von *[Best Practices](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* im *Adobe Commerce-Implementierungs-Playbook* angefordert werden.

## Wer kann eine Anforderung erstellen?

Adobe akzeptiert sowohl interne als auch externe Interessengruppen, einschließlich, aber nicht beschränkt auf Einzelpersonen in den folgenden Gruppen:

- Adobe Partners
- Adobe CTAG (Customer Technical Advisory Group), Kundensupport, Kundenerfolg, Engineering-Teams

## Wie erstelle ich eine Anforderung?

**Interne Stakeholder** können Anfragen einreichen, indem sie ein Jira-Problem im COMDOX-Projekt öffnen. **Externe Stakeholder** können Anforderungen senden, indem sie ein [GitHub-Problem](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) in diesem Repository öffnen.

Sie können die folgenden Anforderungstypen senden:

- Ideen für neue Inhalte
- Aktualisierungen von bereits veröffentlichten Inhalten
- Publish neue Inhalte, die von Interessenträgern oder der Community bereitgestellt werden

## Wie sieht der Gesamtprozess aus?


**Erstellen Sie ein Jira-Ticket oder -Problem** - Interne Stakeholder erstellen ein Jira-Ticket im COMDOX-Projekt. Externe Akteure reichen ein GitHub-Problem ein. Schließen Sie vollständige Details in das Jira- oder [GitHub-Problem](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) ein, damit das Team den Kontext verstehen und die Anfrage priorisieren kann.

**Das Adobe-Projektteam wertet die Anfrage aus und priorisiert sie.** - Das Team überwacht regelmäßig Anfragen, um die Priorität zu bestimmen und die erforderlichen Änderungen für die Aufnahme in die Best Practices für Implementierungs-Playbook zu bewerten. Beispielsweise kann das Team festlegen, dass anstelle eines neuen Best Practices-Themas der angeforderte Inhalt der bestehenden Produktdokumentation auf der Experience League- oder der Adobe Developer-Site hinzugefügt werden soll.

Wenn in einer Anfrage nicht genügend Informationen angegeben sind, fordert das Team vom Anfragenden zusätzliche Informationen an. Wenn der Anfragende nicht innerhalb von 14 Tagen antwortet, schließt das Team die Anfrage.

**Erstellen oder Aktualisieren von Inhalten** - Die Erstellung von Inhalten wird gemäß dem im [Adobe Experience League Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) dokumentierten Vorgang abgeschlossen. Je nach Anforderung kann die Arbeit das Konvertieren neuer Inhalte in Markdown, das Erstellen eines Themas oder das Aktualisieren eines vorhandenen Themas umfassen.

**Inhaltsüberprüfung, -genehmigung und -veröffentlichung** -Der Inhalt wird bei der Themenerstellung oder -aktualisierung mit [GitHub-Pull-Anforderungen](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests) überprüft und bearbeitet. Alle Inhalte müssen einer redaktionellen Überprüfung unterzogen werden. Die technische Prüfung ist optional und hängt vom Inhalt ab. Wenn keine technische Überprüfung erforderlich ist, wird der Prozess nur mit einer redaktionellen Überprüfung fortgesetzt. Dieser Vorgang kann mehrere Iterationen dauern, bis der Inhalt validiert wurde.

Nachdem ein Artikel genehmigt wurde, kann die Pull-Anforderung mit der Produktionsverzweigung zusammengeführt werden. Die Zusammenführung sollte vom Autor vorgenommen werden. Nachdem ein Thema zusammengeführt wurde, kann es sofort mithilfe eines manuellen Prozesses oder automatisch beim nächsten Ausführen des Veröffentlichungsauftrags in der Produktion veröffentlicht werden. Veröffentlichungsaufträge werden normalerweise alle zwei Stunden ausgeführt.

**Neue Inhaltsbenachrichtigung**-Adobe bietet einen Abschnitt *Neue Funktionen* in der [Übersicht über Best Practices](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) , um Benutzer über kürzlich veröffentlichte oder aktualisierte Themen auf dem Laufenden zu halten. Adobe fördert außerdem neue Best Practices-Inhalte über bestehende Kanäle wie Marketing und interne Kommunikation.

## Backlog und Kanban Board

Um Duplizierungen zu vermeiden, werden erstellte und priorisierte Anforderungen im Jira-Backlog des COMDOX-Projekts und im [GitHub-Projekt](https://github.com/orgs/AdobeDocs/projects/6/views/1) angezeigt. Interne Interessenträger werden ermutigt, sich mit dem Abstimmungssystem in Jira zu befassen, um Anfragen, die sie für notwendig oder relevant halten, zur Abstimmung zu stellen. Die Abstimmung hilft dem Projektteam &quot;Best Practices&quot;auch, die Art von Inhalten zu verstehen, die Interessengruppen erwarten und schätzen. Anfragen, die noch priorisiert und überprüft werden, werden im Rückstand angezeigt, bis sie auf die aktiven Spuren im Kanban-Board verschoben werden.

Auf das Kanban-Board können interne Benutzer zugreifen, um zu sehen (und/oder zu überwachen), an welchen Inhalten gearbeitet wird und welche Fortschritte erzielt wurden. Auf dieser Pinnwand werden nur aktive Anforderungen angezeigt.
