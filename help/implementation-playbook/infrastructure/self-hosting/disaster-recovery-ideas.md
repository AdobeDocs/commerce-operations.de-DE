---
title: Self-Hosting Adobe Commerce Disaster Recovery
description: Erfahren Sie mehr über die Self-Hosting Disaster Recovery Ideen und Konzepte und Best Practices, die Sie berücksichtigen sollten.
landing-page-description: Lernen Sie einige Konzepte und Überlegungen zur Notfallwiederherstellung kennen, wenn Sie Adobe Commerce selbst hosten.
short-description: Erfahren Sie Strategien und Disaster Recovery-Konzepte für das Hosting von Adobe Commerce selbst.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: cab6213b-da44-498f-b5c1-e7f89e95038e
feature: Install
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 0%

---

# Self-Hosting von Adobe Commerce Disaster Recovery-Ideen

Die Notfallwiederherstellung für diesen Artikel umfasst eine fehlgeschlagene Bereitstellung. Auch wenn der gesamte Prozess möglicherweise nicht identisch ist, gelten ähnliche Grundsätze. Eine Katastrophe kann auf eine fehlgeschlagene Produktionsbereitstellung, eine nicht reagierende Serverbereitstellung, die Erkennung einer Exploit und viele andere Szenarien zurückzuführen sein. Wenn der Wiederherstellungsprozess für eine fehlgeschlagene Implementierung nur zwei einfache Schritte erfordert, kann eine Wiederherstellung von einer Exploit viel schwieriger sein. Aufgrund der Komplexität von Umgebungen, Hosting-Varianten und anderen Komplexität bietet dieser Artikel Ideen und Konzepte, aber Sie müssen die Untersuchung selbst fortsetzen. Auf diese Weise können Sie sicherstellen, dass Sie eine Strategie entwickeln, die Ihren Geschäftsanforderungen entspricht.

## Praktischer Wiederherstellungsprozess oft

Übung, Übung. Es gibt einen Grund, warum die Praktiken zuerst auf der Liste der Katastrophenschutzmaßnahmen erscheinen. Es ist bei weitem nicht einfach, einen Wiederherstellungsplan aufzustellen, aber ihn nie auszuführen. Wenn Sie nicht genug üben, sind Sie anfällig für Fehler, verpasste Schritte und verlängern wahrscheinlich die tatsächliche Wiederherstellung. Die Kadenz für Ihre praktische Erholung liegt bei Ihnen und Ihren Geschäftspartnern. Es kann gut genug sein, den Wiederherstellungsprozess zu einem jährlichen Ereignis zu machen, aber ein tiefes Gespräch mit den Entscheidungsträgern in Ihrem Unternehmen sollte mehrere Schlüsselthemen beinhalten. Diese Themen helfen ihnen zu verstehen, warum Übung wichtig ist und erwartet werden sollte. Im Folgenden finden Sie einige Themen, die den Einstieg in die Konversation erleichtern:

* Durch Übung wird die tatsächliche Ausfallzeit reduziert, wenn ein Ereignis tatsächlich eintritt. Wenn eine Übung zum Trocknen Ihre Site pro Stunde im Jahr herunterfährt, kann dies die tatsächliche Ausfallzeit eines realen Ereignisses um mehrere Stunden reduzieren. Es ist nicht ungewöhnlich, dass die Wiederherstellung einer Site mindestens acht Stunden in Anspruch nimmt. Wenn Sie dieses Ereignis oft durchführen, können Sie die Zeit für jede Phase verkürzen und sich schneller erholen.
* Geplante Ausfallzeiten für diese Praxisabläufe können mit Server-Patches, Bestandsanpassungen oder anderen Elementen zusammenfallen, die regelmäßig durchgeführt werden sollen.
* Üben Sie unterschiedliche Szenarien anstelle desselben. Nehmen Sie sich gelegentlich die Zeit, um eine vollständige Wiederherstellung von einem früheren Datum durchzuführen. Dazu gehören beispielsweise das Suchen und Verwenden einer archivierten Kopie der Datenbank und das Zurücksetzen des Codes auf das Datum. Eine einfachere Möglichkeit ist die Wiederherstellung aus einer fehlgeschlagenen Bereitstellung, bei der Sie einfach zum vorherigen Commit zurückkehren müssen.
* Vergewissern Sie sich, dass der Wiederherstellungsprozess tatsächlich funktioniert, manchmal können die archivierten Datenbanken beschädigt werden. Dadurch wird sichergestellt, dass alles wiederhergestellt und funktionsfähig ist. Das Suchen und Wiederherstellen einer alten DB dauert einige Zeit. Es sollte bekannt sein, wie lange dieser Teil des Prozesses dauern kann.
* Überprüfen Sie, ob alle Änderungen in den Konfigurationen dokumentiert sind. Dadurch wird sichergestellt, dass jede Wiederherstellung aus einer älteren Datenbank alle neuen Konfigurationsänderungen in Anspruch nehmen kann. Beispiel: Ihr API-Schlüssel hat sich in den letzten Tagen in Ihrem Zahlungsverarbeiter geändert. Durch einen guten Änderungsmanagementprozess kann der Prozess durch die Suche nach diesen wichtigen Aktualisierungen planmäßig verlaufen.

## DB-Backups

Datenbanksicherungen sollten relativ normal sein. Es ist nicht ungewöhnlich, stündliche, tägliche, wöchentliche und monatliche Momentaufnahmen zu haben. Die Backups sollten schließlich in einen langfristigen Speicher verschoben werden. Diese langfristige Speicherung kann immer dann erfolgen, wenn das Unternehmen oder Technologieteam genügend Zeit für eine rasche Wiederherstellung von ihnen hat. Eine Wiederherstellung aus einer langfristigen Speicherung erhöht die Zeit des Wiederherstellungsprozesses. Daher sollte bei der Entscheidung, wann dies erfolgen soll, mit Vorsicht vorgegangen werden. Die Datenbank-Backups sollten automatisiert werden und nicht auf menschliche Interaktionen angewiesen sein. Dadurch wird sichergestellt, dass Sie über genügend davon verfügen, um einen sicheren und vorhersehbaren Wiederherstellungsprozess zu gewährleisten. Dies hilft auch bei allen forensischen Aktivitäten, wenn eine solche Tätigkeit notwendig ist, ist machbar und zuverlässig. Möglicherweise ist eine forensische Untersuchung erforderlich, nachdem eine Ausbeutung festgestellt wurde, oder wenn Sie versuchen zu diagnostizieren, wann eine Kreditkartenbetrugsaktivität aufgetreten ist oder sogar, wenn jemand auf Ihre Website kam. Es gibt keine Beschränkung für die Verwendung dieser Sicherungen, aber eine gute Anzahl von Backups ist Ihre Speicherschuld, wenn Sie sie tatsächlich benötigen.

Im Folgenden finden Sie ein Beispiel für eine Richtlinie zur Datenaufbewahrung:

* Alle acht Stunden. Die Sicherungen sollten leicht zugänglich sein.
* Tägliche Backups der letzten sieben Tage und sollten leicht zugänglich sein. Eine Kopie von ihnen könnte ein Kandidat für die Verlagerung aus der Site sein.
* Wöchentliche Sicherungen für die letzten vier Wochen erwägen, die Website zu verlassen.
* monatliche Sicherungen für die letzten drei Monate wurden verlegt.
* Ältere Sicherungen werden auf eine langfristige Offsite-Speicherung verschoben.

## Infrastruktur als Code

Diese Methode bedeutet, dass Sie über Tools und Code verfügen, um Teile oder die gesamte Infrastruktur für Ihr Projekt neu zu erstellen. Dies kann bei Problemen mit einem Server erforderlich sein und muss aus der Nutzung entfernt werden. Die Möglichkeit, schnell einen neuen Server online zu stellen, den Code bereitzustellen, PHP-, Nginx- oder Apache-Konfigurationen zu erstellen und was auch immer, bedeutet automatisch weniger Ausfallzeiten. Auch gut dokumentierte Schritte in einem Runbook sind einfacher einzurichten, damit die Ausführung der Schritte viel länger dauert. Beachten Sie auch den menschlichen Fehler, der unter Stress auftreten kann, um eine nicht responsive Site wieder online zu stellen.

## Sekundäre Datenbank

Die Verwendung einer sekundären Datenbank kann aus folgenden Gründen nützlich sein:

* Warme Standby, wenn der primäre Laufwerksfehler auftritt
* Vorbereiten von Anforderungen aus der Anwendung zulassen
* Setzen von mysqldump auf und ermöglichen normale Transaktionen, ohne die Datenbank zu sperren
* Ermöglicht den Zugriff auf Daten aus einer externen Datenquelle, ohne dass die Websites die Möglichkeit haben, Informationen für Kundenanfragen zu übertragen.

Die sekundäre Datenbank kann als `warm standby`. Dies kann zum Tragen kommen, wenn Sie überlegen, wie Sie sich von einem primären Datenbankfehler erholen können. Die Weiterleitung der sekundären Datenbank auf primär ist weniger komplex als die Neuerstellung und Wiederherstellung einer Datenbank auf einer neu erstellten MySQL-Instanz. Dadurch wird die tatsächliche Ausfallzeit während eines Wiederherstellungsvorgangs reduziert.

Es besteht die Möglichkeit, einige der Anfragen an die sekundäre Datenbank abzuleiten. Wenn diese Methode verwendet wird, wird empfohlen, die sekundäre Datenbank schreibgeschützt zu machen. Indem die Adobe Commerce-Anwendung diese sekundäre Datenbank für Lesevorgänge verwenden kann, hilft sie, einige der Leseanfragen zu übernehmen und die sekundäre Datenbank zu aktivieren. Diese Änderung macht jedoch nur 30-50 % aller Anforderungen aus, aber jede Belastung, die Sie aus der primären Datenbank nehmen können, ist ein Sieg.

## Erstellen eines Bereitstellungsplans mit einem Rollback

Jede Bereitstellung sollte einen Rollback-Plan enthalten. Ja, jede Implementierung. Wenn du es vorhast, bist du nie überrascht und bist bereit für das schlechte Ereignis. Manchmal können die einfachsten Code-Updates aus jedem Grund katastrophal fehlschlagen.

Betrachten Sie diese wahre Geschichte eines Teams, das eine kleine, einfache Pull-Anfrage gesendet hat, um eine Schemaänderung in der Datenbank auszuführen. Als der Einsatz von 1 Minute auf 5, dann 10 ging, wurde das Team mehr besorgt. Was sie bis zu diesem Zeitpunkt nicht überprüft und berücksichtigt haben, war eine Diskrepanz zwischen der Produktionsdatenbank und der Staging-Datenbank. Es hat sich bewährt, beim Aktualisieren der Staging-Umgebung mit einer Kopie der Produktion alle Kundendaten zu entfernen. Dies bedeutet, dass alle Tests und Qualitätssicherungen, bevor dies der Implementierung entspricht, nur einige Minuten in Anspruch nehmen sollten. In Wirklichkeit hatten sie über 20 Millionen Kunden, und diese kleine Schemaänderung dauerte außerordentlich lange, bis sie abgeschlossen war. Da sie keine Ahnung hatten, wie lange dies tatsächlich dauern würde, waren sie gezwungen, den mysql-Prozess zu beenden und die Implementierung zurückzusetzen.

Die Vorbereitung auf einen Rollback-Prozess für eine Bereitstellung dauert nur einige Minuten, da der Gesamtprozess ähnlich sein wird. Sie sollten sich jedoch die Zeit nehmen, um genau zu dokumentieren, auf welche Übertragung Sie die HEAD des Git-Repositorys zurücksetzen würden. Sie sollten genau dokumentieren, welche db-Momentaufnahmen verwendet werden sollen oder wo Sie den aktuellen finden, wenn sich dieser immer an derselben Stelle befindet. Sie verfügen über definierte Zeiträume, in denen der Status der Bereitstellung besprochen werden muss und die automatisch wirksam werden. Wenn beispielsweise ein Einsatz länger als 15 Minuten dauert, fragen Sie den Projektmanager und andere Beteiligte, ob die Dinge weitergehen sollen. Führen Sie jedoch automatisch den Rollback-Prozess aus und benachrichtigen Sie alle Interessengruppen, wenn der Prozess 45 Minuten dauert, unabhängig davon, ob der Projektmanager und Architekt zögern.

Stellen Sie sicher, dass mehrere Personen an dem gesamten Prozess und jeder Phase beteiligt sind. Entwickler auf mittlerer Ebene müssen den Bereitstellungsprozess, das Rollback-Verfahren und den Speicherort für Dateien überprüfen. Dies ist eine hervorragende Möglichkeit, um sie in die Arbeit mit einzubeziehen. Sie werden schließlich die Schritte durchführen, damit sie den gesamten Prozess verstehen können, ist der Schlüssel für langfristigen Erfolg. Stellen Sie sicher, dass jeder berechtigt ist, einen Einsatz abzubrechen. Ihr Team so viel Mitsprache zu geben, ist Ermächtigung und Belohnung. Wenn ein junger Entwickler wirklich das Gefühl hat, dass etwas fehlt, sollten sie sich gezwungen fühlen, sich zu äußern und ihre Vorsicht Gehör zu verschaffen. Lassen Sie den Architekten und Projektmanager ihre Angst bestätigen oder mildern. Es ist wichtig, über ein starkes Team zu verfügen, das nach dem Projekt sucht und seine Erfahrung mit fehlerfreien Implementierungen aufrecht erhält.

## Überprüfen des Zugriffs auf Domain Name Management, DMS, SSL, WAF

Da Domain-Namen ablaufen, können DNS-Einträge versehentlich geändert werden, SSL-Zertifikate können ablaufen und vieles mehr. Stellen Sie sicher, dass Sie die Möglichkeit haben, sich anzumelden und zu überprüfen, ob die Verbindung oft erfolgen soll. Diese einfache Prüfung jedes Quartal gibt Ihnen die Gewissheit, dass Sie genau wissen, wo sich die Dinge befinden, insbesondere in einem Notfall. Gehen Sie nicht davon aus, dass Ihr DNS in Ihrer Registrar verwaltet wird, nur um herauszufinden, ob es in Amazon verwaltet wird. Diese Datensätze werden nicht häufig verwendet, daher ist es sehr wahrscheinlich zu vergessen, wo sie sind. Vertraue nicht der schriftlichen Dokumentation für Benutzernamen und Kennwörter allein. Melden Sie sich bei jeder an und überprüfen Sie, ob die Konfigurationen, die Sie suchen, dort tatsächlich verwaltet werden. Allzu oft ändern sich die Dinge während des Managementerwerbs oder des Unternehmenserwerbs, und nur eine Person weiß, was passiert ist, weil sie diejenigen sind, die die Aktualisierung durchgeführt haben. Sie wussten nicht, dass Sie sich auf ein freigegebenes Word-Dokument verlassen haben, was der Ort ist, den Benutzernamen und das Kennwort. Finden Sie einen Kontrollprozess, der für Sie und Ihre Organisation sinnvoll ist, aber dies alle drei bis sechs Monate zu tun, ist ein guter Ausgangspunkt.

{{$include /help/_includes/hosting-related-links.md}}
