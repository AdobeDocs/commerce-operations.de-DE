---
title: Gemeinsame Verantwortung
description: Erfahren Sie mehr über die Sicherheitsaufgaben aller an Ihrem Adobe Commerce-Projekt beteiligten Parteien in Bezug auf Cloud-Infrastrukturprojekte.
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# Sicherheitsmodell für gemeinsame Verantwortung

Adobe Commerce on Cloud Infrastructure ist ein Plattform-as-a-Service-Angebot, das auf einem Sicherheitsmodell für gemeinsame Verantwortung beruht. Adobe, der Händler, der Cloud-Service-Anbieter und der Anbieter des Content Delivery Network (CDN) tragen jeweils eine eigene Verantwortung für die Aufrechterhaltung der Sicherheit der Adobe Commerce in der Cloud-Infrastrukturanwendung sowie für den Händlerspezifischen Code und Erweiterungen.

Dieser Ansatz ermöglicht es Händlern, eine hochflexible, anpassbare und skalierbare Lösung zu entwickeln und zu implementieren, die ihren Geschäftsanforderungen am besten entspricht und gleichzeitig betriebliche Verantwortlichkeiten und Kosten minimiert.

Im Allgemeinen ist Adobe für die Entwicklung und Pflege von sicherem Kern-Anwendungs-Code, die Gewährleistung der Plattformsicherheit, die Sicherstellung der Konformität von SOC 2 und PCI sowie der Kompatibilität mit PCI-konformen Technologiekomponenten (z. B. PHP, Redis) der Plattform und die Reaktion auf Sicherheitsprobleme im Zusammenhang mit der Kernplattform verantwortlich. Adobe ist auch für die Zusammenarbeit mit Cloud Service-Anbietern und CDN-Partnern zur Lösung von Problemen verantwortlich, die auftreten können.

Händler sind für die Pflege von sicherem benutzerdefiniertem Code und Integrationen mit Drittanbieteranwendungen verantwortlich, die sichere Anwendungsentwicklung sicherstellen, die PCI-Zertifizierung auf Anforderung durch den Zahlungsverarbeiter des Händlers erhalten und auf Sicherheitsvorfälle reagieren und reagieren.

## Adobe

Adobe ist für die Sicherheit und Verfügbarkeit der Adobe Commerce in der Cloud-Infrastruktur-Umgebung und der zentralen Adobe Commerce im Cloud-Infrastruktur-Lösungscode verantwortlich. Darüber hinaus ist Adobe für die erforderlichen Aktivitäten und Mechanismen verantwortlich, die die Sicherheit der Adobe Commerce in der Cloud-Infrastrukturlösung gewährleisten, darunter:

- Anwenden von Sicherheits- und Patches auf Serverebene für von Adobe Commerce unterstützte Anwendungen auf Cloud-Infrastruktur, z. B. Cloud-Datenspeicherung und Suchfunktionen
- Durchführen von Penetrationstests und Scannen des Adobe Commerce-Kerns im Cloud-Infrastrukturcode
- Halbjährliche Prüfungen/Prüfungen der Identitäts- und Zugriffsverwaltungslösungen und -berechtigungsverwaltung (IAM) öffentlicher Cloud-Dienstanbieter (PCI-Compliance-Anforderung)
- Durchführung halbjährlicher Prüfungen/Audits von zugelassenen Nutzern, einschließlich Adobe-Mitarbeitern und Auftragnehmern (PCI-Compliance-Anforderung)
- Durchführung jährlicher Tests und Dokumentation der Sicherungs- und Wiederherstellungsfunktionen
- Konfigurieren von Server- und Perimeter-Firewalls
- Verbinden und Konfigurieren des Adobe Commerce-Repositorys für Cloud-Infrastruktur
- Festlegung, Erprobung, Umsetzung und Dokumentation von Notfallwiederherstellungsplänen für die Gebiete innerhalb des Zuständigkeitsbereichs von Adobe
- Definieren globaler WAF-Regeln (Web Application Firewall) der Plattform
- Härtung des Betriebssystems
- Implementierung und Pflege der Integration von Content Distribution Network (CDN)- und APM-Lösungen (Application Performance Management) mit Adobe Commerce in Cloud-Infrastruktur
- Regelmäßige Sicherheits- und sonstige Aktualisierungen für die Adobe Commerce im Cloud-Infrastrukturcode (Patches werden vom Händler übernommen)
- Verwalten der Händlerunterstützung und Unterstützung von Zugriffskontrollen (z. B. Zendesk)
- Überwachung, Protokollierung und Behebung von Sicherheitsvorfällen im Zusammenhang mit der Adobe Commerce in Bezug auf die Infrastruktur von Cloud-Infrastrukturplattformen
- Überwachung des Betriebs von Plattformen und rund um die Uhr Unterstützung von Adobe Commerce für Cloud-Infrastrukturhändler
- Bereitstellung der Produktions- und Staging-Umgebungen
- Bewertung potenzieller Sicherheitsbedrohungen für den Betrieb und die Infrastruktur von Plattformen
- Skalierung von Computing-, Speicher-, Raster- und anderen Ressourcen, wie im Service-Level Agreement (SLA) mit dem Händler beschrieben
- Einrichten von DNS (Adobe Commerce nur auf Cloud-Infrastruktur-Plattforminfrastruktur)
- Plattform auf Sicherheitslücken testen

Während Adobe die PCI-Zertifizierung für die im Betrieb der Adobe Commerce-Cloud-Infrastrukturlösung verwendete Infrastruktur und Dienste verwaltet, sind Händler für die Einhaltung von benutzerdefiniertem Code, System- und Netzwerkprozessen und für die Organisation verantwortlich.

Adobe stellt auch die Verfügbarkeit der Infrastruktur des Händlers sicher, wie in der geltenden SLA vereinbart.

## Handelspflichten

Der Händler ist für die Einhaltung der Best Practices für die Sicherheit seiner spezifischen, benutzerdefinierten Instanz von Adobe Commerce in der Cloud-Infrastrukturlösung sowie für Folgendes zuständig:

- Hinzufügen der erforderlichen Adobe Commerce-Konfigurationsdateien für die Cloud-Infrastruktur zum Repository
- Anwenden von Sicherheits- und anderen Patches auf benutzerdefinierte Adobe Commerce auf Cloud-Infrastrukturlösungen unmittelbar nach deren Veröffentlichung durch Adobe
- Anwenden von Sicherheits- und anderen Patches auf alle benutzerdefinierten Erweiterungen und Codes unmittelbar nach deren Veröffentlichung durch den Anbieter
- Erstellen, Bereitstellen und Testen benutzerdefinierter VarVL-Dateien
- Entwerfen, Erstellen, Installieren, Integrieren und Sichern der angepassten Adobe Commerce-Lösung für die Cloud-Infrastruktur, einschließlich aller benutzerdefinierten Erweiterungen und Codes
- Gewähren und Widerrufen des Benutzerzugriffs auf die Merchant-Instanz der Adobe Commerce für Cloud-Infrastrukturkonfiguration, -Anwendung und -Plattform
- Beheben von Sicherheitsproblemen im Zusammenhang mit dem internen Netzwerk, den Servern, der Infrastruktur und allen benutzerdefinierten Anwendungen, die auf der Adobe Commerce-Cloud-Infrastrukturplattform erstellt wurden
- Befehlszeilenintegration (CLI)-Tool (Adobe Commerce on Cloud Infrastructure) installieren
- Aufrechterhaltung der erforderlichen PCI-Compliance der angepassten Anwendung und anderer interner Prozesse gemäß den PCI-DSS-Richtlinien

  >[!NOTE]
  >
  >Die PCI-Compliance des Händlers baut auf den PCI-Zertifizierungen von Adobe Commerce in der Cloud-Infrastruktur und dem Cloud-Hosting-Provider auf, um die Bereiche zu minimieren, die überprüft werden müssen.

- Ausführen von PCI ASV-Scans und Beheben von Problemen in der zentralen Adobe Commerce auf Cloud-Infrastrukturcode und -Plattform
- Überwachung aller Anwendungsaktivitäten, die eine potenzielle Sicherheitsbedrohung erkennen könnten, einschließlich Penetrationstests, Schwachstellenanalysen und Protokollen
- Überwachung und Reaktion auf Sicherheitsvorfälle, einschließlich Forensik, Behebung und Reporting im Zusammenhang mit der Adobe Commerce des Händlers für Cloud-Infrastrukturlösungen und Benutzerkonten
- Ermitteln eines DNS-Anbieters und Konfigurieren und Verwalten von handelsspezifischen DNS-Einträgen
- Ausführen von Leistungstests für die angepasste Anwendung
- Zugriff auf Plattformkonten, Instanzzugriff und Anwendung sichern
- Testen und Qualitätssicherung der benutzerdefinierten Anwendung
- Aufrechterhaltung der Sicherheit aller Systeme oder Netzwerke, die der Händler mit der Adobe Commerce in der Cloud-Infrastrukturanwendung verbindet

## Verantwortlichkeiten von Cloud-Service-Anbietern

Adobe verlässt sich bei der Hosting der Cloud-Server-Infrastruktur für Adobe Commerce in der Cloud-Infrastruktur auf etablierte Cloud-Service-Anbieter. Diese Provider sind für die Sicherheit des Netzwerks verantwortlich, einschließlich Routing, Switching und Reichweitennetzsicherheit über Firewall-Systeme und IDS (Intrusion Detection Systems). Cloud-Dienstleister sind auch für die physische Sicherheit von Rechenzentren verantwortlich, in denen die Adobe Commerce auf Cloud-Infrastrukturlösungen gehostet wird, und für die Umweltsicherheit von Rechenzentren.

Cloud-Service-Provider sind auch für Folgendes verantwortlich:

- Warten von PCI DSS-, SOC 2- und ISO 27001-Zertifikaten für ihre Cloud Services
- Sichern des Hypervisors
- Sichern des Rechenzentrums, einschließlich physischem und Netzwerkzugriff

## Verantwortlichkeiten des CDN-Anbieters

Die Adobe Commerce-Lösung für Cloud-Infrastruktur verwendet CDN-Anbieter, um die Seitenladezeit zu verkürzen, Inhalte zwischenzuspeichern und veraltete Inhalte sofort zu bereinigen. Diese Anbieter sind auch für Sicherheitsprobleme zuständig, die in direktem Zusammenhang mit ihrem CDN stehen oder sich auf ihr CDN auswirken, sowie für die Definition und Pflege von CDN-WAF-Regeln.

## Sicherheitsprotokoll

In der folgenden Grafik wird das RACI-Modell (R — Responsible, A — Accountable, C — Consulted, I — Informed) verwendet, um jede Partei in den Sicherheitsaufgaben des Ökosystems in Bezug auf die Adobe Commerce im Rahmen des Lastenmodells für die Cloud-Infrastruktur visuell darzustellen:

<table>
<thead>
  <tr>
    <th>Aufgabe</th>
    <th>Adobe</th>
    <th>Händler</th>
    <th>Cloud Service Provider</th>
    <th>CDN-Anbieter</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Anwenden von Adobe Commerce auf Cloud-Infrastruktur-Patches</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Anwenden von Patches auf unterstützende Dienste<br>(z. B. Nginx, MySQL)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definieren der Ursprungs-WAF-Regeln</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definieren von CDN-WAF-Regeln</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Bereitstellen von Plattform-WAF-Regeln</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Bereitstellen von CDN-WAF-Regeln</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Beheben von Kernfehlern in Adobe Commerce im Cloud-Infrastrukturcode</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Freigabe von Adobe Commerce auf Cloud-Infrastruktur-Patches</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Skalierung (berechnen und speichern)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Skalierung (Seitenanfang/Raster)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gewährleisten des Zugriffs auf den Quellcode, einschließlich repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installieren von Adobe Commerce auf dem CLI-Tool der Cloud-Infrastruktur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Hinzufügen von Adobe Commerce zu Cloud-Infrastruktur-Konfigurationsdateien zum Repository</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Erstellen eines Projekts für den Händler (Onboarding-Benutzeroberfläche)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Verbinden von Repositorys mit Adobe Commerce über Cloud-Infrastruktur</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Quell-Repository konfigurieren<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Erstellen eines Benutzers für den Release Manager (Onboarding-Benutzeroberfläche)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Bereitstellen von Code in der Produktion</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Bereitstellen von Code in der Staging-Umgebung</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Integrieren externer Anwendungen und Erweiterungen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installieren von Erweiterungen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Anpassen von Adobe Commerce an die Cloud-Infrastruktur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Testen der Leistung von angepassten Adobe Commerce in der Cloud-Infrastruktur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Benutzerdefinierte Anwendung testen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Design und Design von benutzerdefinierten Programmen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>Erstellen, Bereitstellen und Testen benutzerdefinierter VCLs</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>DNS konfigurieren (nur Plattforminfrastruktur)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Entwickeln der CDN-Erweiterung und Beheben von Fehlern</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Onboarding-CDN</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Unterstützendes CDN<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>New Relic-APM/Infrastruktur konfigurieren</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installieren von New Relic APM/Infrastruktur</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Unterstützende New Relic-APM/Infrastruktur</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Konfigurieren von Nginx<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Abrufen des DNS-Providers (nur Pro)</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Härtung des Betriebssystems</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Bereitstellung der Produktions- und Staging-Umgebungen</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Zugriff auf Zendesk für Adobe Commerce in der Cloud-Infrastruktur</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Beheben von Problemen mit der Händlersicherheit</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Beheben von Problemen mit der Cloud-Infrastruktur in Adobe Commerce</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Beheben von CDN-Sicherheitsproblemen</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Beheben von APM-Sicherheitsproblemen</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe mit Sicherheitsforschung (Software) unterstützen</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Unterstützung von Adobe mit Sicherheitsforschung (Prüfungen/Audits)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Durchführen von PCI ASV-Scans</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Beheben von Adobe Commerce bei PCI-Scans für Cloud-Infrastruktur<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Beheben von PCI-Scans von PaaS</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Verwalten von Betriebssystem- und Plattformgeheimnissen</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Verwalten von Adobe Commerce-Verschlüsselungsschlüsseln für Cloud-Infrastrukturen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Scannen von benutzerdefinierten Adobe Commerce auf Cloud-Infrastrukturinstanzen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Überwachen von Sicherheitslogs</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Verwalten von IAM und Berechtigungen für Adobe Commerce in der Cloud-Infrastruktur</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Verwalten von Support-Zugriffskontrollen (Teleport)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Support und Zugriff für Händler steuern</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Jährliche Prüfung und Dokumentation des Adobe DR-Plans und Sicherung und Wiederherstellung</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Jährliche Prüfung und Dokumentation des Notfallwiederherstellungsplans</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> Nur wenn das Adobe Commerce on Cloud-Infrastruktur-Repository als Haupt-Repository verwendet wird. Die Nutzung anderer externer Repositorys liegt in der alleinigen Verantwortung des Händlers.</p>
      <p><sup><strong>2</strong></sup> Adobe unterstützt Level 1 bei Problemen mit CDN-Anbietern.</p>
      <p><sup><strong>3</strong></sup> Einige Ngnix-Steuerelemente werden vom Händler für ihre Anwendungen konfiguriert und sind dafür verantwortlich.</p>
      <p><sup><strong>4</strong></sup> Für PCI gelten die Anforderungen an Penetrationstests für Adobe und Händler.</p>
    </td>
  </tr>
</tfoot>
</table>
