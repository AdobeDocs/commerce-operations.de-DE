---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# Best Practices: Workflow zur Inhaltserstellung

In diesem Dokument wird der Benutzer-Workflow beschrieben, mit dem Änderungen oder Ergänzungen der *[Best Practices](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* Inhalt in *Adobe Commerce-Implementierungs-Playbook*.

## Wer kann eine Anforderung erstellen?

Die Adobe akzeptiert sowohl interne als auch externe Interessengruppen, insbesondere aber nicht nur Einzelpersonen in den folgenden Gruppen:

- Adobe Partner
- Adobe CTAG (Customer Technical Advisory Group), Kundensupport, Kundenerfolg, Engineering-Teams

## Wie erstelle ich eine Anforderung?

**Interne Interessengruppen** kann Anfragen einreichen, indem ein Jira-Problem im COMDOX-Projekt geöffnet wird. **Externe Akteure** kann Anforderungen senden, indem eine [GitHub-Problem](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) in diesem Repository.

Sie können die folgenden Anforderungstypen senden:

- Ideen für neue Inhalte
- Aktualisierungen von bereits veröffentlichten Inhalten
- Veröffentlichen neuer Inhalte, die von den Interessenträgern oder der Community bereitgestellt werden

## Wie sieht der Gesamtprozess aus?


**Jira-Ticket oder -Problem erstellen**—Interne Stakeholder erstellen ein Jira-Ticket im COMDOX-Projekt. Externe Akteure reichen ein GitHub-Problem ein. Vollständige Details in die Jira aufnehmen oder [GitHub-Problem](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) , um dem Team zu helfen, den Kontext zu verstehen und die Anfrage zu priorisieren.

**Das Adobe-Projektteam bewertet und priorisiert die Anfrage.**—Das Team überwacht regelmäßig Anfragen, um die Priorität zu bestimmen und die erforderlichen Änderungen für die Aufnahme in die Best Practices für Implementierungs-Playbook zu bewerten. Beispielsweise kann das Team festlegen, dass anstelle eines neuen Best Practices-Themas der angeforderte Inhalt der bestehenden Produktdokumentation auf der Experience League- oder der Adobe Developer-Site hinzugefügt werden soll.

Wenn in einer Anfrage nicht genügend Informationen angegeben sind, fordert das Team vom Anfragenden zusätzliche Informationen an. Wenn der Anfragende nicht innerhalb von 14 Tagen antwortet, schließt das Team die Anfrage.

**Inhalt erstellen oder aktualisieren**-Die Erstellung von Inhalten wird nach dem im Abschnitt [Adobe Experience League Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). Je nach Anforderung kann die Arbeit das Konvertieren neuer Inhalte in Markdown, das Erstellen eines Themas oder das Aktualisieren eines vorhandenen Themas umfassen.

**Inhaltsüberprüfung, -genehmigung und -veröffentlichung**-Inhalte werden bei der Themenerstellung oder -aktualisierung mit [GitHub-Pull-Anforderungen](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). Alle Inhalte müssen einer redaktionellen Überprüfung unterzogen werden. Die technische Prüfung ist optional und hängt vom Inhalt ab. Wenn keine technische Überprüfung erforderlich ist, wird der Prozess nur mit einer redaktionellen Überprüfung fortgesetzt. Dieser Vorgang kann mehrere Iterationen dauern, bis der Inhalt validiert wurde.

Nachdem ein Artikel genehmigt wurde, kann die Pull-Anforderung mit der Produktionsverzweigung zusammengeführt werden. Die Zusammenführung sollte vom Autor vorgenommen werden. Nachdem ein Thema zusammengeführt wurde, kann es sofort mithilfe eines manuellen Prozesses oder automatisch beim nächsten Ausführen des Veröffentlichungsauftrags in der Produktion veröffentlicht werden. Veröffentlichungsaufträge werden normalerweise alle zwei Stunden ausgeführt.

**Benachrichtigung zu neuen Inhalten**-Adobe bietet eine *Neue Funktionen* im Abschnitt [Best Practices - Überblick](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) Thema, um Benutzer über kürzlich veröffentlichte oder aktualisierte Themen auf dem Laufenden zu halten. Adobe wird auch neue Best Practices-Inhalte über bestehende Kanäle wie Marketing und interne Kommunikation fördern.

## Backlog und Kanban Board

Um Duplizierungen zu vermeiden, werden die erstellten und priorisierten Anforderungen im Jira-Backlog des COMDOX-Projekts angezeigt und [GitHub-Projekt zu Problemen](https://github.com/orgs/AdobeDocs/projects/6/views/1). Interne Interessenträger werden ermutigt, sich mit dem Abstimmungssystem in Jira zu befassen, um Anfragen, die sie für notwendig oder relevant halten, zur Abstimmung zu stellen. Die Abstimmung hilft dem Projektteam &quot;Best Practices&quot;auch, die Art von Inhalten zu verstehen, die Interessengruppen erwarten und schätzen. Anfragen, die noch priorisiert und überprüft werden, werden im Rückstand angezeigt, bis sie auf die aktiven Spuren im Kanban-Board verschoben werden.

Auf das Kanban-Board können interne Benutzer zugreifen, um zu sehen (und/oder zu überwachen), an welchen Inhalten gearbeitet wird und welche Fortschritte erzielt wurden. Auf dieser Pinnwand werden nur aktive Anforderungen angezeigt.
