---
title: Reagieren auf einen Sicherheitsvorfall
description: Handhabung von Sicherheitsvorfällen durch Befolgen von Best Practices, um auf Sicherheitsprobleme zu reagieren und diese zu beheben, die die Verfügbarkeit und Leistung der Site beeinträchtigen.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# Best Practices für die Reaktion auf einen Sicherheitsvorfall

Im folgenden Artikel werden Best Practices für die Reaktion auf einen Sicherheitsvorfall und die Behebung von Problemen zusammengefasst, die die Verfügbarkeit, Zuverlässigkeit und Leistung der Adobe Commerce-Site beeinträchtigen.

Die Befolgung dieser Best Practices kann helfen, unbefugten Zugriff und Malware-Angriffe zu verhindern. Wenn ein Sicherheitsvorfall auftritt, helfen Ihnen diese Best Practices bei der Vorbereitung auf eine sofortige Reaktion, der Durchführung einer Ursachenanalyse und der Verwaltung des Wiederherstellungsprozesses, um den normalen Betrieb wiederherzustellen.

>[!TIP]
>
>Adobe hat festgestellt, dass die meisten Sicherheitsvorfälle auftreten, wenn Bedrohungsakteure bestehende, ungepatchte Sicherheitslücken, fehlerhafte Kennwörter sowie schwache Eigentums- und Berechtigungseinstellungen in der Commerce-Programm- und Infrastrukturkonfiguration nutzen. Minimieren Sie das Auftreten von Sicherheitsvorfällen, indem Sie die Best Practices für die Sicherheit von Adobe beim Einrichten, Konfigurieren und Aktualisieren von Adobe Commerce-Installationen lesen und befolgen. Siehe [Sichern der Commerce-Site und -Infrastruktur](../launch/security-best-practices.md).


## Betroffene Produkte und Versionen

[Alle unterstützten ](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce On-Premises

## Reagieren auf einen Incident

Wenn Sie vermuten, dass Ihr Adobe Commerce in einem Cloud-Infrastrukturprojekt von einem Sicherheitsvorfall betroffen ist, sind die ersten wichtigen Schritte:

- Zugriff auf alle Admin-Benutzerkonten prüfen
- Erweiterte MFA-Steuerelemente (Multi-Factor Authentication) aktivieren
- Kritische Protokolle beibehalten
- Überprüfen Sie die Sicherheitsaktualisierungen für Ihre Version von Adobe Commerce.

Weitere Empfehlungen finden Sie unten.

## Sofortiges Handeln im Falle eines Angriffs

Im unglücklichen Fall einer Kompromisslösung für die Site gibt es einige wichtige Empfehlungen, die befolgt werden müssen:

- Wenden Sie Ihren Systemintegrator und das entsprechende Sicherheitspersonal an, um Untersuchungen und Korrekturmaßnahmen durchzuführen.

- Bestimmen Sie den Umfang des Angriffs:
   - Wurde auf Kreditkarteninformationen zugegriffen?
   - Welche Informationen wurden gestohlen?
   - Wie viel Zeit ist seit dem Kompromiss verstrichen?
   - Wurden die Informationen verschlüsselt?

- Versuchen Sie, den Angriffsvektor zu finden, um festzustellen, wann und wie die Site kompromittiert wurde, indem Sie die Server-Protokolldateien und Dateiänderungen überprüfen.

   - Unter bestimmten Umständen kann es ratsam sein, alles zu löschen und neu zu installieren oder im Falle des virtuellen Hosting eine neue Instanz zu erstellen. Malware könnte an einem unerwarteten Ort versteckt sein, nur darauf wartend, sich selbst wiederherzustellen.

   - Entfernen Sie alle unnötigen Dateien. Installieren Sie dann die erforderlichen Dateien aus einer bekannten, sauberen Quelle neu. Sie können beispielsweise eine Neuinstallation anhand der Dateien aus Ihrem Versionskontrollsystem oder aus den Originalverteilungsdateien aus Adobe durchführen.

   - Alle Anmeldedaten zurücksetzen, einschließlich Datenbank, Dateizugriff, Zahlungs- und Versandintegrationen, Webservices und Admin-Anmeldung. Setzen Sie außerdem alle Integrations- und API-Schlüssel und -Konten zurück, die möglicherweise zum Angriff auf das System verwendet werden.

## Analysieren eines Vorfalls

Der erste Schritt der Incident-Analyse besteht darin, so schnell wie möglich so viele Fakten wie möglich zu sammeln. Das Sammeln von Informationen über den Vorfall kann dabei helfen, die potenzielle Ursache des Vorfalls zu ermitteln. Adobe Commerce bietet die folgenden Tools zur Unterstützung bei der Analyse von Vorfällen.

- [Audit-Admin-](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html).

  Der Bericht „Aktionsprotokolle“ zeigt einen detaillierten Datensatz aller Admin-Aktionen an, die für die Protokollierung aktiviert sind. Jeder Datensatz erhält einen Zeitstempel und registriert die IP-Adresse und den Namen des Benutzers. Die Protokolldetails enthalten Admin-Benutzerdaten und zugehörige Änderungen, die während der Aktion vorgenommen wurden.

- Analysieren von Ereignissen mit dem [Tool „Observation for Adobe Commerce](../../../tools/observation-for-adobe-commerce/intro.md).

  Mit dem Tool Observation for Adobe Commerce können Sie komplexe Probleme analysieren, um deren Ursachen festzustellen. Anstatt unterschiedliche Daten zu verfolgen, können Sie Ihre Zeit damit verbringen, Ereignisse und Fehler zu korrelieren, um tiefere Einblicke in die Ursachen von Leistungsengpässen zu erhalten.

  Verwenden Sie die **Sicherheit** im Tool, um einen klaren Überblick über potenzielle Sicherheitsprobleme zu erhalten und so die Grundursachen zu identifizieren und die optimale Leistung von Sites sicherzustellen.

- Analysieren von Protokollen mit [New Relic-Protokollen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html)

  Adobe Commerce in Cloud Infrastructure Pro-Projekten umfassen den [Service &quot;New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html)Protokolle“. Der Service ist so vorkonfiguriert, dass er alle Protokolldaten aus Ihren Staging- und Produktionsumgebungen aggregiert, um sie in einem zentralen Protokollverwaltungs-Dashboard anzuzeigen, in dem Sie aggregierte Daten suchen und visualisieren können.

  Für andere Commerce-Projekte können Sie den Dienst [New Relic Logs](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) einrichten und verwenden, um die folgenden Aufgaben auszuführen:
   - Verwenden Sie [New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs)Abfragen, um aggregierte Protokolldaten zu suchen.
   - Visualisieren von Protokolldaten über die New Relic-Protokollanwendung

## Audit-Konten, Code und Datenbank

Überprüfen Sie Commerce-Admin- und -Benutzerkonten, Anwendungs-Code sowie die Datenbankkonfiguration und -protokolle, um verdächtigen Code zu identifizieren und zu bereinigen und die Sicherheit des Konto-, Standort- und Datenbankzugriffs sicherzustellen. Stellen Sie dann bei Bedarf erneut bereit.

Die Site nach dem Vorfall weiterhin genau überwachen, da viele Sites innerhalb von Stunden wieder gefährdet sind. Fortlaufende Protokollüberprüfung und Überwachung der Dateiintegrität sicherstellen, um Anzeichen für neue Kompromisse schnell zu erkennen.

### Administratorkonten prüfen

- [Administratorzugriff überprüfen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html) - Alte, nicht verwendete oder verdächtige Konten entfernen und Kennwörter für alle Administratorbenutzer rotieren.

- [Überprüfen der Admin-Sicherheitseinstellungen](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html) Überprüfen Sie, ob die Admin-Sicherheitseinstellungen den Best Practices für die Sicherheit entsprechen.

- [Überprüfen von Benutzerkonten für Adobe Commerce in Cloud-Infrastrukturprojekten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) - Entfernen Sie alte, nicht verwendete oder verdächtige Konten und rotieren Sie Kennwörter für alle Cloud-Projekt-Admin-Benutzer. Stellen Sie sicher, dass die Sicherheitseinstellungen des Kontos korrekt konfiguriert sind.

- [Audit von SSH-Schlüsseln](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) für Adobe Commerce in der Cloud-Infrastruktur - Überprüfen, Löschen und Drehen von SSH-Schlüsseln.

### Prüfcode

- Überprüfen Sie vom Administrator die Konfiguration der [HTML-Kopf- und -](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html) auf allen Bereichsebenen, einschließlich `website` und `store view`. Entfernen Sie unbekannten JavaScript-Code aus den Skripten und Stylesheets sowie verschiedene HTML-Einstellungen. Nur erkannten Code wie Tracking-Snippets beibehalten.

- Vergleichen Sie die aktuelle Produktions-Code-Basis mit der im Versionskontrollsystem (VCS) gespeicherten Code-Basis.

- Quarantäne von verdächtigem Code

- Stellen Sie sicher, dass es keine Reste von verdächtigem Code gibt, indem Sie die Code-Basis in der Produktionsumgebung erneut bereitstellen.

### Überprüfen der Datenbankkonfiguration und -protokolle

- Überprüfen Sie alle gespeicherten Prozeduren auf Änderungen.

- Stellen Sie sicher, dass auf die Datenbank nur über die Commerce-Instanz zugegriffen werden kann.

- Stellen Sie sicher, dass keine Malware mehr vorhanden ist, indem Sie die Website mit öffentlich verfügbaren Malware-Scan-Tools durchsuchen.

- Sichern Sie das Admin-Bedienfeld, indem Sie dessen Namen ändern und überprüfen, ob die Site-`app/etc/local.xml` und `var`-URLs nicht öffentlich zugänglich sind.

- Die Site nach dem Vorfall weiterhin genau überwachen, da viele Sites innerhalb von Stunden wieder gefährdet sind. Fortlaufende Protokollüberprüfung und Überwachung der Dateiintegrität sicherstellen, um Anzeichen für neue Kompromisse schnell zu erkennen.

## Google-Warnungen entfernen

Wenn die Site von Google als mit bösartigem Code gekennzeichnet wurde, fordern Sie eine Überprüfung an, sobald die Site bereinigt wurde. Bewertungen von mit Malware infizierten Websites dauern ein paar Tage. Nachdem Google festgestellt hat, dass die Site sauber ist, sollten Warnungen aus Suchergebnissen und Browsern innerhalb von 72 Stunden verschwinden. Siehe [Anfordern einer Überprüfung](https://web.dev/articles/request-a-review).

## Überprüfen der Malware-Ergebnisse - Checkliste

Wenn öffentlich verfügbare Malware-Scan-Tools einen Malware-Angriff bestätigen, untersuchen Sie den Vorfall. Arbeiten Sie mit dem Lösungsintegrator zusammen, um die Site zu bereinigen, und befolgen Sie den empfohlenen Bereinigungsprozess.

## Durchführen zusätzlicher Überprüfungen

Bei komplexen Angriffen sollten Sie am besten mit einem erfahrenen Entwickler, einem Drittanbieter oder einem Lösungsintegrator zusammenarbeiten, um die Site vollständig zu reparieren und die Sicherheitsverfahren zu überprüfen. Die Zusammenarbeit mit erfahrenen Sicherheitsexperten stellt sicher, dass umfassende und fortschrittliche Maßnahmen ergriffen werden, um die Sicherheit Ihres Unternehmens und seiner Kunden zu gewährleisten.

## Weitere Informationen

- [Ursachenanalyse-Framework](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
