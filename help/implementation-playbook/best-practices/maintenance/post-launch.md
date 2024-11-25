---
title: Post-Launch-Support und -Wartung
description: Mit unseren umfassenden Best Practices für Support und Wartung nach dem Start können Sie optimale Leistung und Sicherheit Ihres Adobe Commerce-Stores sicherstellen.
role: Admin, User, Developer
feature: Best Practices
source-git-commit: bcb45d53aba4a73a5730989e9bf29ccba6e9bf35
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---


# Support und Wartung für Adobe Commerce nach dem Start

Support und Wartung nach der Markteinführung sind von entscheidender Bedeutung, um sicherzustellen, dass Ihr Adobe Commerce-Store reibungslos läuft, gut funktioniert, sicher bleibt und weiterhin Ihre Geschäftsziele erreicht. Diese Phase umfasst die kontinuierliche Überwachung, Optimierung, Fehlerbehebung, Aktualisierungen und Benutzerunterstützung. In den folgenden Abschnitten wird die **Post-Launch-Unterstützung** in Schlüsselkategorien unterteilt:

## Regelmäßige Site-Überwachung und Leistungsoptimierung

### Leistungsüberwachung

- **Geschwindigkeit der Site und Belastungstests**: Adobe Commerce kann ressourcenintensiv sein, daher ist eine regelmäßige Leistungsüberwachung von entscheidender Bedeutung.

   - **Zu verwendende Tools**: Alle Adobe Commerce-Projekte für Cloud-Infrastruktur beinhalten Zugriff auf New Relic, was die Überwachung der Leistung und Untersuchung von Ereignissen innerhalb der Commerce-Anwendung und Cloud-Infrastruktur erleichtert. Weitere Tools sind Google PageSpeed Insights und GTMetrix.

   - **Überwachung**: Hier sind die wichtigsten Elemente, die für Adobe Commerce in der Cloud-Infrastruktur überwacht werden sollen:

      - **Statusbenachrichtigungen**: Warnhinweise für Festplattenspeicher und Umgebungszustand.

      - **Beobachtung**: Umfassende Überwachung durch Kombination von Protokolldaten aus mehreren Quellen für eine effektive Site-Verwaltung.

      - **New Relic-Dienst**: überwacht die Leistung in Staging- und Produktionsumgebung und konzentriert sich dabei auf Schlüsselmetriken.

      - **Richtlinie für verwaltete Warnhinweise**: Verfolgt Metriken mit vordefinierten Schwellenwerten auf Trigger-Benachrichtigungen, wenn es sich um Infrastruktur- oder Anwendungsprobleme handelt, die sich auf die Performance auswirken.

  >[!TIP]
  >
  >Siehe [Leistungsüberwachung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) im _Cloud-Handbuch_.


- **Optimierung der Datenbankleistung**: Um die Datenbankleistung in Adobe Commerce Cloud zu optimieren, implementieren Sie Folgendes:

   - **MySQL-Abfragen überwachen und optimieren**: Identifizieren und beheben Sie langsame Abfragen, die mit den Befehlen &quot;VOLLSTÄNDIGE PROZESSLISTE ANZEIGEN&quot;und &quot;EXPLAIN&quot;von MySQL durchgeführt werden können. Für komplexere Setups können Benutzer der Pro-Architektur das Percona Toolkit verwenden, um Abfrageprotokolle auf Leistungsprobleme zu analysieren.

   - **Indexverwaltung**: Stellen Sie sicher, dass jede Tabelle über einen Primärschlüssel verfügt, und entfernen Sie alle doppelten Indizes, da diese die Effizienz verringern und zu Konflikten während gleichzeitiger Schreibvorgänge führen können.

   - **Cron-Auftragsoptimierung**: Cron-Aufträge sollten außerhalb der Spitzenzeiten geplant werden, um die Auswirkungen auf die Leistung zu minimieren, insbesondere wenn Hintergrundaufgaben wie die Indizierung häufig ausgeführt werden.

  >[!TIP]
  >
  >Siehe [Best Practices zur Behebung von Problemen mit der Datenbankleistung](resolve-database-performance-issues.md).

- **CDN überwachen**: Um die schnelle CDN-Leistung in Adobe Commerce Cloud zu überwachen, können Sie die folgenden Aktionen durchführen:

   - **New Relic für die Überwachung nutzen**: Adobe Commerce bietet New Relic, um die schnelle Performance und andere Metriken in Staging- und Produktionsumgebungen zu überwachen. Dieses Tool bietet Einblicke in die Servergesundheit, CDN-Zwischenspeicherung und Netzwerkanfragen im Zeitverlauf, was dazu beiträgt, Muster zu identifizieren und CDN-Einstellungen zu optimieren.

   - **Schnellprotokollanalyse**: Für Adobe Commerce Cloud Pro-Projekte können Sie New Relic-Protokolle verwenden, um CDN- und WAF-Protokolldaten schnell zu überprüfen und zu analysieren, um Leistungstrends, Sicherheitsereignisse und Fehlerdiagnosen oder Latenzprobleme zu verfolgen.

   - **Verwenden Sie cURL-Befehle**: Führen Sie cURL-Befehle mit Fastly-spezifischen Headern aus, um den Cache-Status Ihrer Site zu überprüfen. Zu den wichtigsten Antwortheadern gehören `X-Cache` (HIT/MISS), `Fastly-Module-Enabled`, `Fastly-Magento-VCL-Uploaded` und `Cache-Control`, um die Zwischenspeicherung und den Modulstatus zu überprüfen. Adobe stellt Beispiel-cURL-Befehle für Staging- und Produktionsumgebungen bereit.

   - **Überprüfen Sie die Kopfzeileninformationen**: Inspect-Kopfzeilen wie `Cache-Control`, `Pragma` und `X-Magento-Tags`, um das geeignete Caching-Verhalten und den Umgang mit Tags im zwischengespeicherten Inhalt zu bestätigen. Eigene Header-Werte geben an, ob Caching-Konfigurationen effektiv im gesamten CDN angewendet werden.

   - **Schnelles Debugging und Testen**: Verwenden Sie die Debugging-Funktion von Fastly, um Probleme mit Cache-HIT- und -MISS-Raten, der Caching-Logik oder falschen Kopfzeilenantworten zu identifizieren und zu beheben, die auf Konfigurationsprobleme oder eine falsche Abstimmung mit erwarteten Caching-Regeln verweisen können.

Diese Überwachungsschritte helfen dabei, eine optimale CDN-Leistung zu gewährleisten und Probleme zu beheben, die sich auf die Geschwindigkeit und Zuverlässigkeit der Website auswirken.

>[!TIP]
>
>Siehe [Übersicht über schnelle Dienste](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) im _Cloud-Handbuch_.

#### Regelmäßige Sicherheitsüberwachung

Um eine regelmäßige Sicherheitsüberwachung in Adobe Commerce Cloud zu gewährleisten, empfiehlt Adobe einen facettenreichen Ansatz mit kontinuierlichen Scanvorgängen, Protokollierung und proaktiven Sicherheitsmaßnahmen. Im Folgenden finden Sie einige Kernaktionen zur Gewährleistung der fortlaufenden Sicherheit:

- **Sicherheitsscannen**: Verwenden Sie das Sicherheits-Scan-Tool von Adobe, um bekannte Sicherheitsrisiken und Malware auf all Ihren Commerce-Sites zu überwachen. Dieses Tool bietet Warnhinweise für potenzielle Sicherheitsrisiken und Compliance-Probleme.

- **Regelmäßiges Patch und aktualisierte Wartung**: Wenden Sie Adobe-Sicherheits-Patches und -Updates an, sobald sie verfügbar werden. Durch die Aktualisierung auf die neueste Adobe Commerce-Version wird die aktuelle Abwehr gegen Bedrohungen sichergestellt.

- **Audit- und Protokollüberwachung**: Nutzen Sie Tools wie New Relic Logs (verfügbar für Pro-Projekte), um Sicherheitsprotokolle sowohl aus Staging- als auch aus Produktionsumgebungen zu zentralisieren und zu analysieren, um potenzielle Sicherheitsprobleme und Verstöße besser sichtbar zu machen.

- **Konto- und Zugriffsverwaltung**: Prüfen Sie regelmäßig Benutzer- und Administratorkonten, um nicht autorisierte oder veraltete Konten zu entfernen. Stärkung der Zugangssteuerung mit Multi-Factor-Authentifizierung (MFA) für Administratoren.

- **Web-Anwendungs-Firewall (WAF)**: Verwenden Sie den integrierten Fastly WAF, um Bedrohungen durch schädliche Traffic-Muster, wie z. B. nicht autorisierte Datenextraktionsversuche, zu erkennen und zu minimieren.

- **Benutzerspezifischer Code und Erweiterungssicherheit**: Sichern Sie alle benutzerdefinierten Code- oder Drittanbietererweiterungen, indem Sie regelmäßige Code-Prüfungen durchführen und Erweiterungen auf die von Adobe geprüften Komponenten beschränken.

>[!TIP]
>
>Siehe [Sicherheit](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security) im _Administratorsystemhandbuch_.

#### Fehlerprotokollierung und -überwachung

Um die Fehlerprotokollierung in Adobe Commerce Cloud zu überwachen, bietet Adobe verschiedene Tools und Vorgehensweisen für die wirksame Fehlerbehebung und Leistungsverwaltung:

- **Protokollierung mit New Relic**: New Relic erfasst und zentralisiert Protokolle aus Adobe Commerce-Anwendungen, einschließlich Protokollen zur Infrastruktur, zum CDN und zu WAF. Diese Einrichtung ermöglicht eine optimierte Fehlerverfolgung, das Erstellen von Dashboards und die Abfrage von Protokollen, um tiefere Einblicke in die Anwendungsleistung und Probleme zu erhalten. Der Zugriff auf New Relic-Protokolle ermöglicht das Suchen und Filtern von Protokollen nach verschiedenen Attributen, um Probleme schnell zu diagnostizieren.

- **Fehlerprotokolltypen**: Zu den wichtigsten Fehlerprotokollen in Adobe Commerce Cloud gehören `cloud.log`, die Bereitstellungs-Feedback enthalten, und `cloud.error.log`, die Bereitstellungswarnungen und -fehler protokollieren. Weitere spezifische Protokolle zum Debugging sind `debug.log`, `system.log` und `exception.log`, wobei jede einzelne unterschiedliche Rollen beim Fehler- und Ereignistracking auf der gesamten Commerce-Plattform bereitstellt.

- **Benutzerdefinierte Protokollierung mit Monolog**: Adobe Commerce unterstützt die benutzerdefinierte Protokollierung über Monolog, die es Entwicklern ermöglicht, Protokollmeldungen an verschiedene Ziele wie Dateien, Datenbanken und sogar Warnhinweise zu senden. Diese Flexibilität ist nützlich, um erweiterte Protokollierungsstrategien zu erstellen, die unterschiedlichen Überwachungsanforderungen in Entwicklungs- und Produktionsumgebungen gerecht werden.

- **Überwachung von Ausnahmen mit dem Site-weiten Analyse-Tool**: Das Site-weite Analyse-Tool hilft bei der Überwachung und Verwaltung von Ausnahmeprotokollen, wodurch wiederkehrende Probleme bei Bereitstellung und Anwendungsereignissen erkannt werden. Dieses Tool hebt häufige Probleme hervor, wodurch es einfacher wird, kritische Probleme, die sich auf die Leistung auswirken, zu priorisieren und anzugehen.

>[!TIP]
>
>Weitere Informationen zu Protokollierungs- und Fehlerverfolgungspraktiken in Adobe Commerce Cloud finden Sie unter [New Relic-Protokollverwaltung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) und [Ausnahmeüberwachung](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions).

### Sicherheit und Updates

#### Sicherheits-Patches und -Updates

Um auf dem neuesten Stand zu bleiben und die Sicherheit Ihres Adobe Commerce Cloud-Systems zu gewährleisten, finden Sie hier einige wichtige Vorgehensweisen zur Überwachung von Sicherheits-Patches und -Updates:

- **Adobe Commerce-Sicherheitswarnungen abonnieren**: Halten Sie sich über Sicherheitslücken auf dem Laufenden, indem Sie sich [für Benachrichtigungen von Adobe](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security) registrieren.

- **Versionshinweise überprüfen**: Überprüfen Sie regelmäßig die [Versionshinweise zum Sicherheits-Patch](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/overview), die für Versionen mit &quot;-pN&quot;getaggt sind (z. B. 2.3.5-p1) und wichtige Fehlerbehebungen und Verbesserungen enthalten.

- **Sicherheitspatches sofort anwenden**: Wenden Sie Sicherheits-Patches an, sobald sie verfügbar sind. Dazu gehört das Aktualisieren auf die neuesten Versionen oder das Anwenden bestimmter Patch-Dateien.

- **Verwenden Sie Cloud-Patches**: Für Adobe Commerce Cloud können Sicherheits-Patches in der Cloud Tools Suite gebündelt werden. Stellen Sie sicher, dass Sie die Suite oder die Commerce-Version aktualisieren, um diese Fehlerbehebungen zu erhalten.

- **Automatisierte Patch-Verwaltung**: Erwägen Sie die Verwendung von Tools wie dem zentralisierten Patcher, um [Patches automatisch zu verwalten und über mehrere Stores hinweg anzuwenden](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale).

>[!TIP]
>
>Weitere Informationen und eine schrittweise Anleitung zum Anwenden von Patches und zur Gewährleistung der Sicherheit finden Sie unter [Versionshinweise zum Sicherheits-Patch](../../../release/release-notes/security/overview.md) und [Anwenden von Sicherheitspatches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches). Sie sollten auch die Berichte für das [Site-weite Analyse-Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) lesen.

#### PCI-Compliance

Um PCI-Compliance in Adobe Commerce Cloud sicherzustellen, befolgen Sie die folgenden wichtigen Verfahrensweisen:

- **Protect-Karteninhaberdaten**: Speichern Sie in Adobe Commerce niemals Karteninhaberdaten. Wenn eine Speicherung erforderlich ist, verwenden Sie verschlüsselte und tokenisierte Methoden, um sie zu schützen.

- **Verwenden Sie sichere Übertragungsprotokolle**: Übertragen Sie Zahlungsdaten immer über sichere Protokolle wie TLS mit Verschlüsselung und ordnungsgemäßer Schlüsselverwaltung.

- **Verwenden der Webanwendungs-Firewall (WAF)**: Der leistungsstarke WAF-Dienst unterstützt PCI DSS 6.6-Anforderungen und schützt vor häufigen Sicherheitslücken, indem er bösartigen Datenverkehr blockiert, bevor er Ihre Site erreicht. Weitere Informationen finden Sie [hier](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) und [hier](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service).

- **Zugriffsbeschränkung**: Stellen Sie sicher, dass nur autorisierte Mitarbeiter Zugriff auf vertrauliche Zahlungsdaten haben, und [wenden Sie die Zugriffskontrolle an, um das Risiko einer Belichtung zu verringern](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage).

- **Reguläres Sicherheitsscannen**: Führen Sie regelmäßige PCI ASV-Scans durch und [überwachen Sie Ihre Umgebung](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility), um potenzielle Sicherheitslücken zu schließen.

>[!TIP]
>
>Detailliertere Richtlinien zur Einhaltung der PCI-Compliance mit Adobe Commerce finden Sie unter [Best Practices für die Verarbeitung und Speicherung von Zahlungen](../planning/payment-processing-storage.md).

### Benutzer- und Kundensupport

#### Einrichtung

- **Support-Kanäle**: Implementieren Sie Support-Kanäle für Kunden, z. B.:

   - **Live-Chat**: Bieten Sie Live-Chat-Unterstützung für sofortige Hilfe an. Zu den beliebten Lösungen zählen Zendesk, Intercom und Tidio.

   - **E-Mail-Support**: Verwenden Sie ein Support-Ticketsystem wie Freshdesk oder Zoho Desk, um Kundenanfragen effektiv zu verwalten.

   - **Telefonsupport**: Wenn Sie einen großen Kundenstamm haben, sollten Sie während der Geschäftszeiten Telefonsupport anbieten.

#### Admin-Benutzerschulung

- **Interne Schulung**: Trainieren Sie Ihre Mitarbeiter in der Verwendung des Adobe Commerce-Administrators, der Verarbeitung von Bestellungen, der Verwaltung von Produkten und der Behandlung von Problemen mit dem Kundendienst.

- **Dokumentation**: Verwalten Sie eine interne Wissensdatenbank oder ein Benutzerhandbuch für häufig gestellte Fragen (FAQs), Fehlerbehebung und häufige Aufgaben.

#### Optimierung des Kundenerlebnisses

- **Umfragen und Feedback**: Verwenden Sie Umfragen, um Kundenfeedback zu erfassen und das Kundenerlebnis zu optimieren. Adobe Commerce unterstützt Integrationen mit Tools wie SurveyMonkey oder Google Forms.

- **Verwaltung überprüfen**: Verwalten Sie Kundenbewertungen und -bewertungen für Ihre Produkte. Ermutigen Sie zufriedene Kunden, Bewertungen zu hinterlassen und gleichzeitig auf negative Bewertungen angemessen zu antworten.

- **Personalization**: Implementieren Sie Personalisierungsfunktionen wie personalisierte Produktempfehlungen oder zielgerichtete Promotions.

### Laufende Wartung und Optimierung des Geschäfts

#### Suchmaschinenoptimierung (SEO)

- **Inhaltsoptimierung**: Aktualisieren Sie regelmäßig Produktbeschreibungen, Blog-Beiträge und Kategorieseiten, um Inhalte für Suchmaschinen auf dem neuesten Stand zu halten.

- **SEO-Audits**: Führen Sie regelmäßige SEO-Audits mithilfe von Tools wie Google Search Console oder Screaming Frog durch, um SEO-Probleme zu identifizieren (z. B. fehlerhafte Links, fehlende Metadaten, doppelte Inhalte).

- **URL-Struktur**: Behalten Sie eine saubere, logische URL-Struktur bei und stellen Sie sicher, dass es keine fehlerhaften Links oder Umleitungen gibt.

#### Konversionsratenoptimierung (CRO)

- **A/B-Tests**: Führen Sie A/B-Tests für verschiedene Seitenelemente wie Produktseiten oder Checkout-Prozess durch, um die Konversionsraten zu verbessern.

- **Stehen gelassener Warenkorb**: Implementieren Sie E-Mail-Kampagnen für Warenkorbabbrüche oder Popups mit Exitzweck, um verlorene Verkäufe wiederherzustellen.

- **Checkout-Optimierung**: Vereinfachen Sie Ihren Checkout-Prozess, indem Sie die Anzahl der Schritte reduzieren und einen Gast-Checkout anbieten, um die Konversionen zu verbessern.

#### Marketingintegration

- **E-Mail-Kampagnen**: Richten Sie automatisierte E-Mail-Marketing-Flüsse für Begrüßungs-E-Mails, E-Mails im Warenkorb und Folgenachrichten nach dem Kauf ein. Plattformen wie Adobe Marketo, Mailchimp oder Klaviyo lassen sich gut in Adobe Commerce integrieren.

- **Soziale Medien- und Anzeigenintegration**: Integrieren Sie sie in Plattformen wie Facebook, Instagram und Google Ads, um zielgerichtete Kampagnen auszuführen und die Leistung zu verfolgen.

#### Mobile-Optimierung

- **Mobilgerät - Reaktionsfähigkeit**: Testen Sie regelmäßig die Reaktionsfähigkeit und Benutzerfreundlichkeit Ihrer Website auf Mobilgeräten. Da der mobile Handel wächst, ist ein mobiler First-Ansatz für den weiteren Erfolg von entscheidender Bedeutung.

- **Mobilleistung**: Verwenden Sie die mobilen Test- und Leistungstools von Google, um Ihr mobiles Store-Erlebnis zu optimieren.

### Skalierung und Entwicklung neuer Funktionen

- **Automatische Skalierung für die Traffic-Handhabung**:

   - Adobe Commerce Cloud unterstützt die automatische Skalierung, um Serverressourcen (z. B. Webknoten) dynamisch an Echtzeit-Traffic-Anforderungen anzupassen. Dadurch wird sichergestellt, dass Ihr Store hohe Besuchervolumen ohne manuelles Eingreifen handhaben kann. Siehe [automatische Skalierung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/autoscaling) im _Cloud-Handbuch_.

   - Web- und Service-Ebenen können unabhängig skaliert werden, indem mehr Webknoten für erhöhten Traffic hinzugefügt und Datenbank- oder Dienstknoten für die Backend-Leistung in Spitzenzeiten skaliert werden. Siehe [skalierte Architektur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) im _Cloud-Handbuch_.

- **Leistungsüberwachung**:

   - Verwenden Sie **New Relic**, um Echtzeit-Leistungsmetriken (z. B. CPU-Auslastung, Traffic-Niveaus) zu überwachen und bei Bedarf Anpassungen vorzunehmen.

   - Testen Sie die Leistung in Staging-Umgebungen vor der Skalierung, um Probleme in der Produktion zu vermeiden.

- **Entwicklung neuer Funktionen**:

   - Integrieren Sie erweiterte Funktionen wie **KI-gesteuerte Personalisierung**, **Abonnementverwaltung** und benutzerdefinierte Lösungen.

   - Testen und optimieren Sie Funktionen in Staging-Umgebungen kontinuierlich vor der Bereitstellung in der Produktion, um Ausfallzeiten zu minimieren.

- **Laufende Site-Wartung**:

   - Prüfen Sie regelmäßig Systemprotokolle und Leistungsmetriken, um Verbesserungsbereiche zu ermitteln.

   - Sicherstellen, dass die Infrastruktur skalierbar bleibt und an neue Geschäftsanforderungen und Wachstum angepasst werden kann.

>[!TIP]
>
>Detaillierte Anleitungen finden Sie unter [Best Practices für die Wartung](overview.md), [Personalisierung](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization) und [Funktionsentwicklung](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization).

### Berichterstellung und Analyse

- **Adobe Commerce Intelligence:** Commerce Intelligence, eine Kernfunktion von Adobe Commerce, bietet Einblicke zu Best Practices über mehrere Datenquellen hinweg, sodass Händler wissenschaftliche datenbasierte Entscheidungen treffen und klare und fundierte Maßnahmen treffen können. Weitere Informationen finden Sie im [_Commerce Intelligence-Benutzerhandbuch_](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/getting-started).

- **Adobe Analytics:** Adobe Analytics bietet eine leistungsstarke Lösung zum Verfolgen, Analysieren und Optimieren der Leistung Ihres Online-Stores. Adobe Analytics hilft E-Commerce-Unternehmen, tiefere Einblicke in das Kundenverhalten, die Produktleistung, Konversionsraten und andere Schlüsselmetriken zu erhalten, sodass datenbasierte Entscheidungen getroffen werden können.

- **Google Analytics:** Verwenden Sie Google Analytics, um Kundenverhalten, Traffic-Quellen und Konversionsraten zu verfolgen.

- **Zusätzliche Commerce Intelligence-Tools:** Adobe Commerce enthält erweiterte Berichterstellung. Mit dieser Funktion erhalten Sie Zugriff auf eine Suite dynamischer Berichte, die auf Ihren Produkt-, Bestell- und Kundendaten basieren, sowie auf ein personalisiertes Dashboard, das auf Ihre geschäftlichen Anforderungen zugeschnitten ist. Weitere Informationen finden Sie unter [erweiterte Berichterstellung](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting) im _Benutzerhandbuch für Administratoren_ .

### Schlussfolgerung

Support und Wartung nach der Markteinführung sind fortlaufende Bemühungen, die regelmäßige Aufmerksamkeit erfordern, um sicherzustellen, dass Ihr Adobe Commerce-Store weiterhin eine gute Leistung erzielt, sicher bleibt und sich an die Anforderungen Ihres Unternehmens anpasst. Die Implementierung eines strukturierten Ansatzes für die Site-Überwachung, den Kundensupport, die Optimierung und Updates ist für den langfristigen Erfolg von entscheidender Bedeutung.
