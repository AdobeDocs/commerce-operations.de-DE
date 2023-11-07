---
title: Antwort auf einen Sicherheitsvorfall
description: Beheben Sie Sicherheitsvorfälle, indem Sie Best Practices befolgen, um auf Sicherheitsprobleme zu reagieren und diese zu beheben, die sich auf die Verfügbarkeit und Leistung der Website auswirken.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 0%

---

# Best Practices zur Reaktion auf einen Sicherheitsvorfall

Im folgenden Artikel werden Best Practices zusammengefasst, um auf einen Sicherheitsvorfall zu reagieren und Probleme zu beheben, die sich auf die Verfügbarkeit, Zuverlässigkeit und Leistung von Adobe Commerce-Sites auswirken.

Die Einhaltung dieser Best Practices kann dazu beitragen, nicht autorisierten Zugriff und Malware-Angriffe zu verhindern. Wenn ein Sicherheitsereignis eintritt, helfen Ihnen diese Best Practices bei der Vorbereitung auf eine sofortige Antwort, bei der Durchführung einer Analyse der Ursachen und bei der Verwaltung des Sanierungsprozesses, um normale Vorgänge wiederherzustellen.

>[!TIP]
>
>Adobe hat herausgefunden, dass die meisten Sicherheitsvorfälle auftreten, wenn Bedrohungsakteure bestehende, nicht gepatchte Schwachstellen, schlechte Passwörter und schwache Eigentums- und Berechtigungseinstellungen in der Commerce-Anwendungs- und Infrastrukturkonfiguration nutzen. Minimieren Sie das Auftreten von Sicherheitsvorfällen, indem Sie die Best Practices für Adobe-Sicherheit beim Einrichten, Konfigurieren und Aktualisieren von Adobe Commerce-Installationen überprüfen und befolgen. Siehe [Sichern Ihrer Commerce-Site und -Infrastruktur](../launch/security-best-practices.md).


## Betroffene Produkte und Versionen

[Alle unterstützten Versionen](../../../release/versions.md) von:

- Adobe Commerce auf Cloud-Infrastruktur
- Adobe Commerce vor Ort

## Reaktion auf einen Vorfall

Wenn Sie vermuten, dass Ihr Adobe Commerce on Cloud-Infrastrukturprojekt von einem Sicherheitsvorfall betroffen ist, sind folgende wichtige erste Schritte:

- Prüfen des Zugriffs auf alle Admin-Benutzerkonten
- Erweiterte MFA-Steuerelemente (Multi-Factor Authentication) aktivieren
- Beibehalten kritischer Protokolle
- Überprüfen Sie die Sicherheitsaktualisierungen für Ihre Adobe Commerce-Version.

Weitere Empfehlungen finden Sie unten.

## Sofortiges Handeln bei einem Angriff

Im unglücklichen Fall eines Site-Kompromisses sind hier einige wichtige Empfehlungen zu beachten:

- Wenden Sie Ihren Systemintegrator und das entsprechende Sicherheitspersonal an, um Untersuchungen und Abhilfemaßnahmen durchzuführen.

- Bestimmen Sie den Umfang des Angriffs:
   - Wurde auf Kreditkarteninformationen zugegriffen?
   - Welche Informationen wurden gestohlen?
   - Wie viel Zeit ist seit dem Kompromiss vergangen?
   - Wurden die Informationen verschlüsselt?

- Versuchen Sie, den Angriffsvektor zu finden, um zu ermitteln, wann und wie die Site kompromittiert wurde, indem Sie die Protokolldateien und Dateiänderungen des Servers überprüfen.

   - Unter bestimmten Umständen kann es ratsam sein, alles zu löschen und neu zu installieren oder im Falle eines virtuellen Hosting eine neue Instanz zu erstellen. Malware kann an einem unverdächtigen Ort versteckt werden, nur darauf warten, sich selbst wiederherzustellen.

   - Entfernen Sie alle unnötigen Dateien. Installieren Sie dann die erforderlichen Dateien aus einer bekannten, sauberen Quelle neu. Beispielsweise können Sie eine Neuinstallation mithilfe von Dateien aus Ihrem Versionskontrollsystem oder aus den Originalverteilungsdateien von Adobe durchführen.

   - Setzen Sie alle Anmeldedaten zurück, einschließlich Datenbank, Dateizugriff, Payment- und Versandintegrationen, Webdiensten und Administratoranmeldung. Setzen Sie außerdem alle Integrations- und API-Schlüssel und -Konten zurück, die für Angriffe auf das System verwendet werden könnten.

## Ereignis analysieren

Der erste Schritt der Incident-Analyse besteht darin, so viele Fakten wie möglich zu sammeln, so schnell es möglich ist. Die Erfassung von Informationen über den Vorfall kann dabei helfen, die potenzielle Ursache des Vorfalls zu ermitteln. Adobe Commerce bietet die folgenden Tools, die Sie bei der Analyse von Vorfällen unterstützen.

- [Admin-Aktionsprotokolle überprüfen](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html).

  Der Bericht &quot;Aktionsprotokolle&quot;zeigt einen detaillierten Datensatz aller Admin-Aktionen an, die für die Protokollierung aktiviert sind. Jeder Datensatz ist mit einem Zeitstempel versehen und registriert die IP-Adresse und den Namen des Benutzers. Die Protokolldetails enthalten Admin-Benutzerdaten und zugehörige Änderungen, die während der Aktion vorgenommen wurden.

- Analysieren Sie Ereignisse mit der [Beobachtung des Adobe Commerce-Tools](../../../tools/observation-for-adobe-commerce/intro.md).

  Mit dem Tool &quot;Beobachtung für Adobe Commerce&quot;können Sie komplexe Probleme analysieren, um Ursachen zu identifizieren. Anstatt unterschiedliche Daten zu verfolgen, können Sie Ihre Zeit damit verbringen, Ereignisse und Fehler zu korrelieren, um tiefere Einblicke in die Ursachen von Leistungsengpässen zu erhalten.

  Verwenden Sie die **Sicherheit** im Tool ein, um einen klaren Überblick über potenzielle Sicherheitsprobleme zu erhalten, die bei der Identifizierung von Grundursachen und der optimalen Leistung von Sites helfen.

- Analysieren von Protokollen mit [New Relic-Protokolle](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html)

  Adobe Commerce on Cloud Infrastructure Pro-Projekte umfassen [New Relic-Protokolle](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html) -Dienst. Der Dienst ist so vorkonfiguriert, dass alle Protokolldaten aus Ihren Staging- und Produktionsumgebungen aggregiert werden, um sie in einem zentralen Protokollverwaltungs-Dashboard anzuzeigen, in dem Sie aggregierte Daten suchen und visualisieren können.

  Für andere Commerce-Projekte können Sie die [New Relic-Protokolle](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) -Dienst, um die folgenden Aufgaben auszuführen:
   - Verwendung [New Relic-Abfragen](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) , um aggregierte Protokolldaten zu durchsuchen.
   - Visualisieren Sie Protokolldaten über die New Relic Logs-Anwendung.

## Audit-Konten, -Code und -Datenbank

Überprüfen Sie Commerce Admin- und Benutzerkonten, Anwendungscode und Datenbankkonfiguration sowie Protokolle, um verdächtigen Code zu identifizieren und zu bereinigen und die Sicherheit des Konto-, Site- und Datenbankzugriffs sicherzustellen. Stellen Sie dann nach Bedarf erneut bereit.

Überwachen Sie die Site nach dem Vorfall weiterhin genau, da viele Sites innerhalb von Stunden wieder kompromittiert werden. Stellen Sie sicher, dass die Protokollprüfung und die Überwachung der Dateiintegrität fortgesetzt werden, um schnell alle Anzeichen eines neuen Kompromisses zu erkennen.

### Benutzerkonten für Audit-Administratoren

- [Administratorzugriff überprüfen](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html)—Entfernen Sie alte, nicht verwendete oder verdächtige Konten und drehen Sie die Passwörter für alle Admin-Benutzer.

- [Überprüfen der Sicherheitseinstellungen für Administratoren](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html)—Stellen Sie sicher, dass die Sicherheitseinstellungen der Admin den Best Practices für die Sicherheit entsprechen.

- [Benutzerkonten für Adobe Commerce für Cloud-Infrastrukturprojekte überprüfen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html)—Entfernen Sie alte, nicht verwendete oder verdächtige Konten und drehen Sie Kennwörter für alle Admin-Benutzer des Cloud-Projekts. Stellen Sie sicher, dass die Sicherheitseinstellungen des Kontos korrekt konfiguriert sind.

- [SSH-Schlüssel überprüfen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) für Adobe Commerce in der Cloud-Infrastruktur - SSH-Schlüssel überprüfen, löschen und drehen.

### Audit-Code

- Überprüfen Sie im Admin die [HTML-Kopf- und Fußzeilenkonfiguration](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html) in allen Anwendungsebenen, einschließlich `website` und `store view`. Entfernen Sie unbekannten JavaScript-Code aus den Skripten und Stylesheets sowie verschiedene HTML-Einstellungen. Behalten Sie nur erkannten Code wie Tracking-Snippets bei.

- Vergleichen Sie die aktuelle Produktions-Code-Basis mit der im Versionskontrollsystem (VCS) gespeicherten Codebasis.

- Quarantäne aller verdächtigen Codes.

- Stellen Sie sicher, dass keine Reste von verdächtigem Code vorhanden sind, indem Sie die Codebase in die Produktionsumgebung neu bereitstellen.

### Prüfen der Datenbankkonfiguration und -protokolle

- Überprüfen Sie alle gespeicherten Verfahren auf Änderungen.

- Stellen Sie sicher, dass die Datenbank nur für die Commerce-Instanz zugänglich ist.

- Vergewissern Sie sich, dass Malware nicht mehr vorhanden ist, indem Sie die Seite mit öffentlich verfügbaren Malware-Scanwerkzeugen durchsuchen.

- Sichern Sie das Admin-Bedienfeld, indem Sie seinen Namen ändern und überprüfen, ob die Site `app/etc/local.xml` und `var` URLs sind nicht öffentlich zugänglich.

- Überwachen Sie die Site nach dem Vorfall weiterhin genau, da viele Sites innerhalb von Stunden wieder kompromittiert werden. Stellen Sie sicher, dass die Protokollprüfung und die Überwachung der Dateiintegrität fortgesetzt werden, um schnell alle Anzeichen eines neuen Kompromisses zu erkennen.

## Entfernen von Google-Warnungen

Wenn die Site von Google als Site mit schädlichem Code gekennzeichnet wurde, fordern Sie nach der Bereinigung der Site eine Überprüfung an. Die Überprüfung von mit Malware infizierten Websites dauert einige Tage. Nachdem Google festgestellt hat, dass die Site sauber ist, sollten Warnungen aus Suchergebnissen und Browsern innerhalb von 72 Stunden verschwinden. Siehe [Überprüfung anfordern](https://web.dev/articles/request-a-review).

## Checkliste der Malware-Ergebnisse überprüfen

Wenn öffentlich verfügbare Malware-Scan-Tools einen Malware-Angriff bestätigen, untersuchen Sie den Vorfall. Arbeiten Sie mit dem Lösungsintegrator zusammen, um die Site zu bereinigen und den empfohlenen Sanierungsprozess zu befolgen.

## Weitere Überprüfungen durchführen

Beim Umgang mit komplexen Angriffen ist es am besten, mit einem erfahrenen Entwickler, einem Drittanbieter oder Lösungsintegrator zusammenzuarbeiten, um die Site vollständig zu reparieren und die Sicherheitsverfahren zu überprüfen. Durch die Zusammenarbeit mit erfahrenen Sicherheitsexperten wird sichergestellt, dass umfassende, fortschrittliche Maßnahmen ergriffen werden, um die Sicherheit Ihres Unternehmens und seiner Kunden zu gewährleisten.

## Zusätzliche Informationen

- [Root Ursache Analysis Framework](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
