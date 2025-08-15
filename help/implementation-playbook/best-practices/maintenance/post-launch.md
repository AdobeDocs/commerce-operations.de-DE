---
title: Support und Wartung nach der Markteinführung
description: Mit unseren umfassenden Best Practices für Support und Wartung nach der Markteinführung können Sie die optimale Leistung und Sicherheit Ihres Adobe Commerce-Stores sicherstellen.
role: Admin, User, Developer
feature: Best Practices
exl-id: f02a13ca-c851-4508-a2bd-e5bc196a330c
source-git-commit: 60444d3ef7208d12af3f06af6e3cab2cae93700b
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---

# Support und Wartung für Adobe Commerce nach der Markteinführung

Support und Wartung nach der Markteinführung sind von entscheidender Bedeutung, um sicherzustellen, dass Ihr Adobe Commerce Store reibungslos läuft, gut funktioniert, sicher bleibt und Ihre Geschäftsziele weiterhin erfüllt. Diese Phase umfasst die kontinuierliche Überwachung, Optimierung, Fehlerbehebung, Aktualisierungen und Benutzerunterstützung. In den folgenden Abschnitten werden **Support nach der Markteinführung** in Schlüsselkategorien unterteilt:

## Regelmäßige Site-Überwachung und Leistungsoptimierung

### Leistungsüberwachung

- **Site-Geschwindigkeits- und Belastungstests**: Adobe Commerce kann ressourcenintensiv sein, sodass eine regelmäßige Leistungsüberwachung von entscheidender Bedeutung ist.

   - **Zu verwendende Tools**: Alle Adobe Commerce-Projekte in Cloud-Infrastrukturen enthalten Zugriff auf New Relic, das bei der Leistungsüberwachung und der Untersuchung von Ereignissen in der Commerce-Anwendung und Cloud-Infrastruktur hilft. Weitere Tools sind Google PageSpeed Insights und GTMetrix.

   - **Was zu überwachen ist**: Hier finden Sie die wichtigsten Elemente, die für Adobe Commerce in der Cloud-Infrastruktur überwacht werden müssen:

      - **Konsistenzbenachrichtigungen**: Warnhinweise für Speicherplatz und Umgebungszustand.

      - **Beobachtung**: Umfassende Überwachung durch die Kombination von Protokolldaten aus verschiedenen Quellen für ein effektives Site-Management.

      - **New Relic-Service**: Überwacht die Leistung in Staging und Produktion und konzentriert sich auf Schlüsselmetriken.

      - **Richtlinie für verwaltete Warnhinweise**: Verfolgt Metriken mit vordefinierten Schwellenwerten für Trigger-Benachrichtigungen bei Infrastruktur- oder Anwendungsproblemen, die die Leistung beeinträchtigen.

  >[!TIP]
  >
  >Siehe [Leistungsüberwachung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) im _Cloud-_.


- **Optimieren der Datenbankleistung**: Um die Datenbankleistung in Adobe Commerce Cloud zu optimieren, implementieren Sie Folgendes:

   - **Überwachen und Optimieren von MySQL-Abfragen**: Identifizieren und beheben Sie langsame Abfragen, was mit den Befehlen SHOW FULL PROCESSLIST und EXPLAIN von MySQL möglich ist. Für komplexere Setups können Benutzer der Pro-Architektur das Percona Toolkit verwenden, um Abfrageprotokolle auf Leistungsprobleme zu analysieren.

   - **Indexverwaltung**: Stellen Sie sicher, dass jede Tabelle über einen Primärschlüssel verfügt, und entfernen Sie alle doppelten Indizes, da diese die Effizienz verringern und zu Konflikten beim gleichzeitigen Schreiben führen können.

   - **Cron-Auftragsoptimierung**: Cron-Aufträge sollten außerhalb der Spitzenzeiten geplant werden, um die Auswirkungen auf die Leistung zu minimieren, insbesondere wenn Hintergrundaufgaben wie die Indizierung häufig sind.

  >[!TIP]
  >
  >Siehe [Best Practices zum Beheben von Problemen mit der Datenbankleistung](resolve-database-performance-issues.md).

- **CDN überwachen**: Um die Fastly CDN-Leistung in Adobe Commerce Cloud zu überwachen, können Sie die folgenden Aktionen durchführen:

   - **New Relic für die Überwachung nutzen**: Adobe Commerce bietet New Relic zur Überwachung der Fastly-Leistung und anderer Metriken in Staging- und Produktionsumgebungen. Dieses Tool bietet Einblicke in den Serverzustand, CDN-Caching und Netzwerkanfragen im Laufe der Zeit, was dabei hilft, Muster zu identifizieren und CDN-Einstellungen zu optimieren.

   - **Fastly-Protokollanalyse**: Für Adobe Commerce Cloud Pro-Projekte können Sie New Relic-Protokolle verwenden, um Fastly CDN- und WAF-Protokolldaten zu überprüfen und zu analysieren, um Leistungstrends und Sicherheitsereignisse zu verfolgen und Fehler oder Latenzprobleme zu diagnostizieren.

   - **cURL-Befehle verwenden**: Führen Sie cURL-Befehle mit Fastly-spezifischen Headern aus, um den Cache-Status Ihrer Site zu überprüfen. Zu den wichtigsten Antwortkopfzeilen gehören `X-Cache` (HIT/MISS), `Fastly-Module-Enabled`, `Fastly-Magento-VCL-Uploaded` und `Cache-Control` zur Überprüfung des Caching- und Modulstatus. Adobe bietet Beispiel-cURL-Befehle für Staging- und Produktionsumgebungen.

   - **Kopfzeileninformationen überprüfen** Überprüfen Sie Kopfzeilen wie `Cache-Control`, `Pragma` und `X-Magento-Tags`, um das geeignete Caching-Verhalten und die Tag-Verarbeitung für zwischengespeicherte Inhalte zu bestätigen. Die richtigen Kopfzeilenwerte geben an, ob Caching-Konfigurationen im gesamten CDN effektiv angewendet werden.

   - **Schnelles Debugging und Testen**: Verwenden Sie die Debugging-Funktion von Fastly, um Probleme mit Cache-TREFFER- und -FEHLERRATEN, Caching-Logik oder falschen Header-Antworten zu identifizieren und zu beheben, die auf Konfigurationsprobleme oder eine Fehlausrichtung mit erwarteten Caching-Regeln verweisen können.

Diese Überwachungsschritte helfen, die optimale CDN-Leistung aufrechtzuerhalten und Probleme zu beheben, die die Geschwindigkeit und Zuverlässigkeit der Site beeinträchtigen.

>[!TIP]
>
>Siehe [Fastly Services - Übersicht](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) im _Cloud-Handbuch_.

#### Regelmäßige Sicherheitsüberwachung

Um die Sicherheit in Adobe Commerce Cloud regelmäßig zu überwachen, empfiehlt Adobe einen mehrschichtigen Ansatz, der kontinuierliche Suchvorgänge, Protokollierung und proaktive Sicherheitsmaßnahmen umfasst. Im Folgenden finden Sie einige zentrale Aktionen zur Gewährleistung der fortlaufenden Sicherheit:

- **Sicherheitsüberprüfung**: Verwenden Sie das Adobe-Tool zur Sicherheitsüberprüfung, um bekannte Sicherheitslücken und Malware auf Ihren Commerce-Sites zu überwachen. Dieses Tool bietet Warnhinweise für potenzielle Sicherheitsrisiken und Compliance-Probleme.

- **Regelmäßige Patch- und**: Wenden Sie die Sicherheits-Patches und -Updates von Adobe an, sobald sie verfügbar werden. Durch die Aktualisierung auf die neueste Adobe Commerce-Version wird der neueste Schutz vor Bedrohungen sichergestellt.

- **Audit- und Protokollüberwachung**: Nutzen Sie Tools wie New Relic Logs (für Pro-Projekte verfügbar), um Sicherheitsprotokolle aus Staging- und Produktionsumgebungen zu zentralisieren und zu analysieren und so die Sichtbarkeit potenzieller Sicherheitsprobleme und -verletzungen zu verbessern.

- **Konto- und Zugriffsverwaltung**: Überprüfen Sie regelmäßig Benutzer- und Administratorkonten, um nicht autorisierte oder veraltete Konten zu entfernen. Verbessern Sie die Zugriffskontrolle mit Multifaktor-Authentifizierung (MFA) für Admin-Benutzer.

- **Web Application Firewall (WAF)**: Verwenden Sie die integrierte Fastly-WAF, um Bedrohungen durch bösartige Traffic-Muster, wie z. B. nicht autorisierte Datenextraktionsversuche, zu erkennen und abzuwehren.

- **Benutzerspezifischer Code und Erweiterungssicherheit**: Sichern Sie benutzerdefinierten Code oder Erweiterungen von Drittanbietern, indem Sie regelmäßige Code-Prüfungen durchführen und Erweiterungen auf die von Adobe überprüften Erweiterungen beschränken.

>[!TIP]
>
>Siehe [Sicherheit](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security) im _Admin-_.

#### Fehlerprotokollierung und -überwachung

Um die Fehlerprotokollierung in Adobe Commerce Cloud zu überwachen, bietet Adobe verschiedene Tools und Verfahren für eine effektive Fehlerbehebung und Leistungsverwaltung:

- **Protokollaggregation mit New Relic**: New Relic erfasst und zentralisiert Protokolle aus Adobe Commerce-Programmen, einschließlich Infrastrukturprotokollen, CDN und WAF. Diese Einrichtung ermöglicht eine optimierte Fehlerverfolgung, die Erstellung von Dashboards und die Abfrage von Protokollen, um tiefere Einblicke in die Anwendungsleistung und -probleme zu erhalten. Der Zugriff auf New Relic-Protokolle ermöglicht die Suche und Filterung von Protokollen anhand verschiedener Attribute, um Probleme schnell zu diagnostizieren.

- **Fehlerprotokolltypen**: Zu den wichtigsten Fehlerprotokollen in Adobe Commerce Cloud gehören `cloud.log`, das Bereitstellungs-Feedback enthält, und `cloud.error.log`, das Bereitstellungswarnungen und -fehler protokolliert. Andere spezifische Protokolle für das Debugging umfassen `debug.log`, `system.log` und `exception.log`, wobei jedes einzelne unterschiedliche Rollen bei der Fehler- und Ereignisverfolgung auf der gesamten Commerce-Plattform erfüllt.

- **Benutzerdefinierte Protokollierung mit Monolog**: Adobe Commerce unterstützt benutzerdefinierte Protokollierung über Monolog, mit der Entwickler Protokollmeldungen an verschiedene Ziele wie Dateien, Datenbanken und sogar Warnhinweise weiterleiten können. Diese Flexibilität ist nützlich für die Erstellung erweiterter Protokollierungsstrategien, die unterschiedlichen Überwachungsanforderungen in Entwicklungs- und Produktionsumgebungen gerecht werden.

- **Ausnahmenüberwachung mit dem Site-Wide Analysis Tool**: Das Site-Wide Analysis Tool hilft bei der Überwachung und Verwaltung von Ausnahmeprotokollen und identifiziert wiederkehrende Probleme in Bereitstellungs- und Anwendungsereignissen. Dieses Tool zeigt häufige Probleme auf und erleichtert so die Priorisierung und Behebung kritischer Probleme, die sich auf die Leistung auswirken.

>[!TIP]
>
>Weitere Informationen zu Protokollierung und Fehlerverfolgung in Adobe Commerce Cloud finden Sie unter [New Relic-Protokollverwaltung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) und [Ausnahmeüberwachung](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions).

### Sicherheit und Updates

#### Sicherheits-Patches und -Updates

Im Folgenden finden Sie einige wichtige Verfahren zur Überwachung von Sicherheits-Patches und -Updates, um auf dem neuesten Stand zu bleiben und die Sicherheit Ihres Adobe Commerce Cloud-Systems zu gewährleisten:

- **Adobe Commerce-Sicherheitswarnungen abonnieren**: Bleiben Sie über Sicherheitslücken auf dem Laufenden, indem Sie sich [ Benachrichtigungen von Adobe registrieren](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security).

- **Versionshinweise überprüfen**: Überprüfen Sie regelmäßig [Versionshinweise für Sicherheits-Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/overview), die mit &quot;-pN“ für Versionen getaggt sind (z. B. 2.3.5-p1) und kritische Fehlerbehebungen und Verbesserungen enthalten.

- **Sicherheits-Patches sofort**: Sicherheits-Patches anwenden, sobald sie verfügbar sind. Dazu gehört das Aktualisieren auf die neuesten Versionen oder das Anwenden bestimmter Patch-Dateien.

- **Cloud-Patches verwenden**: Für Adobe Commerce Cloud können Sicherheits-Patches in der Cloud-Tools-Suite gebündelt werden. Stellen Sie sicher, dass Sie die Suite oder die Commerce-Version aktualisieren, um diese Fehlerbehebungen zu erhalten.

- **Automatisiertes Patch-Management**: Erwägen Sie die Verwendung von Tools wie dem zentralen Patcher, um [Patches automatisch zu verwalten und auf mehrere Stores anzuwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale).

>[!TIP]
>
>Weitere Informationen und schrittweise Anweisungen zum Anwenden von Patches und zur Aufrechterhaltung der Sicherheit finden Sie unter [Versionshinweise für Sicherheits-Patches](../../../release/release-notes/security/overview.md) und [Anwenden von Sicherheits-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches). Sie sollten auch Berichte [Site-Wide Analysis Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) überprüfen.

#### PCI-Compliance

Gehen Sie wie folgt vor, um die PCI-Compliance in Adobe Commerce Cloud sicherzustellen:

- **Schutz der**: Speichern Sie niemals Daten von Karteninhabern in Adobe Commerce. Wenn eine Speicherung erforderlich ist, verwenden Sie verschlüsselte und tokenisierte Methoden, um sie zu schützen.

- **Sichere Übertragungsprotokolle verwenden**: Übermitteln Sie Zahlungsdaten immer über sichere Protokolle wie TLS mit Verschlüsselung und ordnungsgemäßer Schlüsselverwaltung.

- **Verwenden der Web Application Firewall (WAF)**: Der Fastly-gestützte WAF-Service unterstützt Sie bei der Erfüllung der PCI DSS 6.6-Anforderungen und schützt vor gängigen Sicherheitslücken, indem er bösartigen Traffic blockiert, bevor er Ihre Site erreicht. Weitere Informationen finden Sie [hier](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) und [hier](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service).

- **Zugriff beschränken**: Sicherstellen, dass nur autorisierte Mitarbeiter Zugriff auf sensible Zahlungsdaten haben, und [Zugriffskontrolle anwenden, um das Risiko einer Exposition zu verringern](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage).

- **Regelmäßige Sicherheitsüberprüfung**: Führen Sie regelmäßige PCI-ASV-Scans durch und [ Sie Ihre Umgebung ](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility), um potenzielle Schwachstellen zu beheben.

>[!TIP]
>
>Ausführlichere Richtlinien zur Einhaltung der PCI-Compliance mit Adobe Commerce finden Sie unter [Best Practices für die Zahlungsverarbeitung und -speicherung](../planning/payment-processing-storage.md).

### Benutzer- und Kunden-Support

#### Setup

- **Support-Kanäle**: Implementieren Sie Support-Kanäle, z. B.:

   - **Live-Chat**: Bieten Sie Live-Chat-Unterstützung für sofortige Hilfe. Zu den beliebten Lösungen gehören Zendesk, Intercom und Tidio.

   - **E-Mail-**: Verwenden Sie ein Support-Ticketing-System wie Freshdesk oder Zoho Desk, um Kundenanfragen effektiv zu verwalten.

   - **Telefonischer Support**: Wenn Sie einen großen Kundenstamm haben, sollten Sie während der Geschäftszeiten telefonischen Support anbieten.

#### Admin-Benutzerschulung

- **Interne Schulung**: Schulung Ihres Personals im Umgang mit Adobe Commerce Admin, der Verarbeitung von Bestellungen, der Verwaltung von Produkten und der Handhabung von Problemen mit dem Kundendienst.

- **Dokumentation**: Führen Sie eine interne Wissensdatenbank oder ein Benutzerhandbuch für häufig gestellte Fragen (FAQs), Fehlerbehebung und allgemeine Aufgaben.

#### Optimierung des Customer Experience

- **Umfragen und Feedback**: Verwenden Sie Umfragen, um Kundenfeedback zu sammeln und das Kundenerlebnis zu optimieren. Adobe Commerce unterstützt Integrationen mit Tools wie SurveyMonkey oder Google Forms.

- **Review-**: Kundenbewertungen und -bewertungen für Ihre Produkte verwalten. Motivieren Sie zufriedene Kunden dazu, Bewertungen zu hinterlassen und gleichzeitig angemessen auf negative Bewertungen zu reagieren.

- **Personalization**: Implementieren Sie Personalisierungsfunktionen wie personalisierte Produktempfehlungen oder zielgerichtete Promotions.

### Laufende Store-Wartung und -Optimierung

#### Suchmaschinenoptimierung (SEO)

- **Inhaltsoptimierung**: Aktualisieren Sie Produktbeschreibungen, Blog-Posts und Kategorieseiten regelmäßig, um Inhalte aktuell und für Suchmaschinen relevant zu halten.

- **SEO-Audits**: Führen Sie regelmäßige SEO-Audits mithilfe von Tools wie Google Search Console oder Screaming Frog durch, um SEO-Probleme (z. B. fehlerhafte Links, fehlende Metadaten, doppelte Inhalte) zu identifizieren.

- **URL-Struktur**: Achten Sie auf eine saubere, logische URL-Struktur und stellen Sie sicher, dass es keine fehlerhaften Links oder Umleitungen gibt.

#### Konversionsratenoptimierung (CRO)

- **A/B-**: Führen Sie A/B-Tests für verschiedene Seitenelemente durch, z. B. Produktseiten oder Checkout-Prozesse, um die Konversionsraten zu verbessern.

- **Warenkorbabbruch**: Implementieren von E-Mail-Kampagnen für Warenkorbabbrüche oder Popup-Fenstern mit Exitintent, um Verkaufsausfälle wiederherzustellen.

- **Checkout-Optimierung**: Vereinfachen Sie Ihren Checkout-Prozess, indem Sie die Anzahl der Schritte reduzieren und einen Gast-Checkout anbieten, um die Konversionen zu verbessern.

#### Marketing-Integration

- **E-Mail-Kampagnen**: Richten Sie automatisierte E-Mail-Marketing-Flüsse für Willkommens-E-Mails, E-Mails zu Transaktionsabbrüchen und Nachverfolgungsmaßnahmen nach dem Kauf ein. Plattformen wie Adobe Marketo, Mailchimp oder Klaviyo lassen sich gut mit Adobe Commerce integrieren.

- **Social Media- und Anzeigenintegration**: Integration mit Plattformen wie Facebook, Instagram und Google Ads, um zielgerichtete Kampagnen durchzuführen und die Leistung zu verfolgen.

#### Optimierung von Mobilgeräten

- **Reaktionsfähigkeit auf Mobilgeräten**: Testen Sie regelmäßig die Reaktionsfähigkeit und Benutzerfreundlichkeit Ihrer Website auf Mobilgeräte. Angesichts der Tatsache, dass der mobile Handel wächst, ist ein Ansatz, bei dem zuerst auf Mobilgeräte geachtet wird, für den weiteren Erfolg unerlässlich.

- **Mobilleistung**: Verwenden Sie die für Mobilgeräte geeigneten Test- und Leistungstools von Google, um Ihr mobiles Store-Erlebnis zu optimieren.

### Skalierung und Entwicklung neuer Funktionen

- **Automatische Skalierung für die Traffic-Verarbeitung**:

   - Adobe Commerce Cloud unterstützt die automatische Skalierung, um Server-Ressourcen (z. B. Web-Knoten) basierend auf Echtzeit-Traffic-Anforderungen dynamisch anzupassen, sodass Ihr Store hohe Besuchermengen ohne manuelles Eingreifen verarbeiten kann. Siehe [Automatische Skalierung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/autoscaling) im _Cloud-_.

   - Web- und Service-Ebenen können unabhängig skaliert werden, sodass mehr Web-Knoten für erhöhten Traffic hinzugefügt und Datenbank- oder Service-Knoten für die Backend-Leistung in Spitzenzeiten skaliert werden können. Siehe [Skalierte Architektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) im _Cloud-_.

- **Leistungsüberwachung**:

   - Verwenden Sie **New Relic**, um Echtzeit-Leistungsmetriken (z. B. CPU-Nutzung, Traffic-Niveaus) zu überwachen und nach Bedarf Anpassungen vorzunehmen.

   - Testen Sie die Leistung in Staging-Umgebungen, bevor Sie skalieren, um Probleme in der Produktion zu vermeiden.

- **Entwicklung neuer Funktionen**:

   - Erweiterte Funktionen wie **KI-gesteuerte Personalisierung**, **Abonnementverwaltung** und benutzerdefinierte Lösungen integrieren.

   - Kontinuierliches Testen und Verfeinern von Funktionen in Staging-Umgebungen vor der Bereitstellung in der Produktion, um Ausfallzeiten zu minimieren.

- **Fortlaufende Site-Wartung**:

   - Überprüfen Sie regelmäßig Systemprotokolle und Leistungsmetriken, um Bereiche zu identifizieren, in denen Verbesserungen vorgenommen werden müssen.

   - Sicherstellen, dass die Infrastruktur skalierbar bleibt und an neue Geschäftsanforderungen und Wachstum angepasst werden kann.

>[!TIP]
>
>Detaillierte Anleitungen finden Sie unter [Best Practices für die ](overview.md), [Personalisierung](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization) und [Funktionsentwicklung](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization).

### Reporting und Analysen

- **Adobe Commerce Intelligence:** Commerce Intelligence, eine Kernfunktion von Adobe Commerce, bietet Best-Practice-Einblicke in mehrere Datenquellen, sodass Händler datengestützte wissenschaftliche Entscheidungen treffen und klare und fundierte Maßnahmen ergreifen können. Siehe [_Commerce Intelligence-Benutzerhandbuch_](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/getting-started).

- **Adobe Analytics:** Adobe Analytics bietet eine leistungsstarke Lösung zum Nachverfolgen, Analysieren und Optimieren der Leistung Ihres Online-Shops. Adobe Analytics hilft E-Commerce-Unternehmen, tiefere Einblicke in das Kundenverhalten, die Produktleistung, Konversionsraten und andere Schlüsselmetriken zu erhalten, was datengestützte Entscheidungsfindung ermöglicht.

- **Google Analytics:** Verwenden Sie Google Analytics, um das Kundenverhalten, Traffic-Quellen und Konversionsraten zu verfolgen.

- **Zusätzliche Commerce Intelligence-Tools:** Adobe Commerce umfasst erweiterte Berichterstellung. Mit dieser Funktion erhalten Sie Zugriff auf eine Suite dynamischer Berichte, die auf Ihren Produkt-, Auftrags- und Kundendaten basieren, und zwar mit einem personalisierten Dashboard, das auf Ihre Geschäftsanforderungen zugeschnitten ist. Weitere Informationen finden Sie unter [Erweiterte Berichterstellung](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting) im _Admin_ Benutzerhandbuch.

### Schlussfolgerung

Support und Wartung nach der Markteinführung sind fortlaufende Bemühungen, die regelmäßiges Augenmerk erfordern, um sicherzustellen, dass Ihr Adobe Commerce-Store weiterhin gut funktioniert, sicher bleibt und sich an die Anforderungen Ihres Unternehmens anpasst. Die Implementierung eines strukturierten Ansatzes zur Überwachung von Sites, Kundenunterstützung, Optimierung und Aktualisierung ist für den langfristigen Erfolg von entscheidender Bedeutung.
