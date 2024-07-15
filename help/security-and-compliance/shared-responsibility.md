---
title: Sicherheit und Betriebsmodell für gemeinsame Verantwortung
description: Erfahren Sie mehr über die Sicherheitsaufgaben aller an Ihrem Adobe Commerce-Projekt beteiligten Parteien in Bezug auf Cloud-Infrastrukturprojekte.
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: 76aafb88855f7f41db8e57b06cf0e82370b57302
workflow-type: tm+mt
source-wordcount: '2802'
ht-degree: 0%

---

# Sicherheit und Betriebsmodell für gemeinsame Verantwortung

Adobe Commerce on Cloud Infrastructure ist ein Plattform-as-a-Service-Angebot, das auf einem Sicherheitsmodell mit gemeinsamer Verantwortung beruht. Diese Zuständigkeiten werden von Adobe, dem Händler, dem Cloud-Service-Provider und dem Content Delivery Network (CDN)-Anbieter gemeinsam wahrgenommen. Jede Partei trägt die spezifische Verantwortung für die Sicherung und den Betrieb der Adobe Commerce-Anwendung sowie des Händlercodes und der Erweiterungen, die in der Cloud-Infrastruktur bereitgestellt werden.

Dieses gemeinsam genutzte Modell ermöglicht es Händlern, eine hochflexible, anpassbare und skalierbare Lösung zu entwickeln und zu implementieren, um ihre Geschäftsanforderungen zu erfüllen und gleichzeitig betriebliche Verantwortlichkeiten und Kosten zu minimieren.

Im Allgemeinen ist Adobe für Folgendes verantwortlich:

- Entwickeln und Verwalten von sicherem Kern-Anwendungs-Code
- Wahrung der Plattformsicherheit
- Sicherstellen, dass die Plattform SOC 2- und PCI-kompatibel ist und mit PCI-kompatiblen Technologiekomponenten kompatibel ist (z. B. PHP, Redis)
- Antworten auf Sicherheitsfragen bezüglich der Kernplattform
- Arbeiten mit Cloud Service-Anbietern und CDN-Partnern zur Lösung von Problemen

Händler sind für Folgendes verantwortlich:

- Gewährleistung der Sicherheit für benutzerdefinierten Code und Integrationen mit Drittanbieteranwendungen
- Sichere Anwendungsentwicklung
- Erhalt der PCI-Zertifizierung, falls vom Zahlungsverarbeiter des Händlers verlangt
- Reaktion auf Sicherheitsvorfälle und Reaktion darauf

## Adobe

Adobe ist für die Sicherheit und Verfügbarkeit der Adobe Commerce in der Cloud-Infrastruktur-Umgebung und des Kernlösungscodes verantwortlich. Darüber hinaus ist Adobe für die erforderlichen Aktivitäten und Mechanismen verantwortlich, die die Sicherheit der Adobe Commerce in der Cloud-Infrastrukturlösung gewährleisten, darunter:

- Anwenden von Sicherheits- und Patches auf Serverebene für von Adobe Commerce unterstützte Anwendungen auf Cloud-Infrastruktur, z. B. Cloud-Datenspeicherung und Suchfunktionen
- Durchführen von Penetrationstests und Scannen des Adobe Commerce-Kerns im Cloud-Infrastrukturcode
- Halbjährliche Prüfungen und Prüfungen der Identitäts- und Zugriffsverwaltungslösungen (IAM) öffentlicher Cloud-Diensteanbieter (PCI-Compliance-Anforderung)
- Durchführung halbjährlicher Überprüfungen und Audits von zugelassenen Nutzern, einschließlich Adobe-Mitarbeitern und Auftragnehmern (PCI-Compliance-Anforderung)
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

Adobe verwaltet die PCI-Zertifizierung für die Infrastruktur und die Dienste, die für die Adobe Commerce-Lösung verwendet werden.  Merchants sind für die Einhaltung von benutzerdefiniertem Code, System- und Netzwerkprozessen sowie der Organisation verantwortlich.

Adobe stellt auch die Verfügbarkeit der Infrastruktur des Händlers sicher, wie in der geltenden SLA vereinbart.

## Handelspflichten

Der Händler ist für die Einhaltung der Best Practices für die Sicherheit seiner spezifischen, benutzerdefinierten Instanz von Adobe Commerce in der Cloud-Infrastrukturlösung verantwortlich:

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
  >Um die Bereiche zu minimieren, die überprüft werden müssen, basiert die PCI-Compliance für den Händler auf den PCI-Zertifizierungen von Adobe Commerce und dem Cloud-Hosting-Anbieter.

- Ausführen von PCI ASV-Scans und Beheben von Problemen in der zentralen Adobe Commerce auf Cloud-Infrastrukturcode und -Plattform
- Überwachung aller Anwendungsaktivitäten, die eine potenzielle Sicherheitsbedrohung erkennen könnten, einschließlich Penetrationstests, Schwachstellenanalysen und Protokollen
- Überwachung und Reaktion auf Sicherheitsvorfälle, einschließlich Forensik, Behebung und Reporting im Zusammenhang mit der Adobe Commerce des Händlers für Cloud-Infrastrukturlösungen und Benutzerkonten
- Ermitteln eines DNS-Anbieters und Konfigurieren und Verwalten von handelsspezifischen DNS-Einträgen
- Ausführen von Leistungstests für die angepasste Anwendung
- Zugriff auf Plattformkonten, Instanzzugriff und Anwendung sichern
- Testen und Qualitätssicherung der benutzerdefinierten Anwendung
- Aufrechterhaltung der Sicherheit aller Systeme oder Netzwerke, die der Händler mit der Adobe Commerce in der Cloud-Infrastrukturanwendung verbindet

## Verantwortlichkeiten des Cloud Service-Anbieters

Adobe verlässt sich bei der Hosting der Cloud-Server-Infrastruktur für Adobe Commerce in der Cloud-Infrastruktur auf etablierte Cloud-Service-Anbieter. Diese Provider sind für die Sicherheit des Netzwerks verantwortlich, einschließlich Routing, Switching und Reichweitennetzsicherheit über Firewall-Systeme und IDS (Intrusion Detection Systems). Cloud-Dienstleister sind auch für die physische Sicherheit von Rechenzentren verantwortlich, in denen die Adobe Commerce auf Cloud-Infrastrukturlösungen gehostet wird, und für die Umweltsicherheit von Rechenzentren.

Cloud-Service-Provider sind auch für Folgendes verantwortlich:

- Warten von PCI DSS-, SOC 2- und ISO 27001-Zertifikaten für ihre Cloud Services
- Sichern des Hypervisors
- Sichern des Rechenzentrums, einschließlich physischem und Netzwerkzugriff

## Verantwortlichkeiten des CDN-Anbieters

Die Adobe Commerce-Lösung für Cloud-Infrastruktur verwendet CDN-Anbieter, um die Seitenladezeit zu verkürzen, Inhalte zwischenzuspeichern und veraltete Inhalte sofort zu bereinigen. Diese Anbieter sind auch für Sicherheitsprobleme zuständig, die in direktem Zusammenhang mit ihrem CDN stehen oder sich auf ihr CDN auswirken, sowie für die Definition und Pflege von CDN-WAF-Regeln.

## Zusammenfassung der Sicherheitsaufgaben

>[!BEGINSHADEBOX]

Die folgende Zusammenfassungstabelle verwendet das RACI-Modell, um die zwischen Adobe, dem Händler und dem Cloud-Dienstleister geteilten Sicherheitsaufgaben anzuzeigen:

**R** — verantwortlich
**A** — Accountable
**C** — Consulted
**I** — Informatisiert

>[!ENDSHADEBOX]

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
    <td>Anwenden von Patches auf unterstützende Dienste<br> (z. B. Nginx oder MySQL)</td>
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
    <td>Skalierung (Pfade und Raster)</td>
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
    <td>Konfigurieren des Quell-Repositorys<sup>1</sup></td>
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
    <td>Testen der benutzerdefinierten Anwendung</td>
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
    <td>Konfigurieren von New Relic-APM- und Infrastrukturanwendungen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installieren von New Relic-APM- und Infrastrukturanwendungen</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Unterstützende New Relic-APM- und Infrastrukturanwendungen</td>
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
    <td>Abrufen eines DNS-Providers (nur Pro)</td>
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
    <td>Beheben von Adobe Commerce auf PCI-Scans für Cloud-Infrastruktur<sup>4</sup></td>
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
      <p><sup><strong>3</strong></sup> Der Händler ist für alle Ngnix-Steuerelemente verantwortlich, die er für seine Anwendungen konfiguriert.</p>
      <p><sup><strong>4</strong></sup> Für PCI gelten die Anforderungen an Penetrationstests für Adobe und Händler.</p>
    </td>
  </tr>
</tfoot>
</table>

## Übersicht über die operativen Zuständigkeiten

>[!BEGINSHADEBOX]

In den folgenden Zusammenfassungstabellen werden die operativen Zuständigkeiten für Adobe und Merchants bei der Entwicklung, Bereitstellung, Wartung und Sicherung von Adobe Commerce in Cloud-Infrastrukturen erläutert.

>[!ENDSHADEBOX]

### Kodierung und Entwicklung

#### Adobe Commerce-Core-Code

|     | Adobe | Händler |
| --- | --- | --- |
| Veröffentlichen von Aktualisierungen und Patches in Adobe Commerce Core | R |     |
| Verfügbarkeit und Patch des Dateisystems | R |  |
| Veröffentlichen von Aktualisierungen und Patches in den ECE-Tools | R |     |
| Adobe Commerce-Anwendungsqualität | R |     |

{style="table-layout:auto"}

#### Code-Repository

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit von repo.magento.com | R |     |
| Verfügbarkeit von Adobe Commerce auf dem Cloud Git-Server | R |     |
| Andere vom Händler ausgewählte Code-Repositorys (GitHub, Bitbucket, gehosteter Git-Server) |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | Händler |
| --- | --- | --- |
| Bereitstellen von Cloud Docker-Containern zum Herunterladen | R |   |
| Implementierung und Einrichtung von Cloud Docker (optional) |     | R |
| Alle anderen lokalen Entwicklungseinstellungen |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | Händler |
| --- | --- | --- |
| Laufende Qualität und Aktualisierung der ECE-Instrumente | R |   |
| Installieren der neuesten ECE Tools-Version |     | R |

{style="table-layout:auto"}

#### Anpassungen

|  | Adobe | Händler |
| --- | --- | --- |
| Benutzerdefinierte Adobe Commerce-Module und -Code |     | R |
| Erweiterungen |     | R |
| Benutzerdefinierte Integrationen |     | R |

{style="table-layout:auto"}

#### Bereitstellungen

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit der Infrastruktur zum Erstellen und Bereitstellen von Code | R |   |
| Laufende Qualität der Build-und-Bereitstellungs-Konfigurationspipeline der Infrastruktur | R |   |
| Konfiguration der Erstellung und Bereitstellung statischer Inhalte |     | R |
| Aufbau und Ausführung des Governance-Prozesses für Implementierungen: Kriterien und Änderungsmanagement |     | R |
| In der Staging-Umgebung bereitstellen |     | R |
| In der Produktionsumgebung bereitstellen |     | R |
| Produktionsrückgänge |     | R |

{style="table-layout:auto"}

#### Synchronisieren von Umgebungen

Merchants sind für die Synchronisierung von Daten zwischen Umgebungen verantwortlich.

#### Patchen

|     | Adobe | Händler |
| --- | --- | --- |
| Installieren von Updates und Patches für ECE-Tools |     | R |
| Installieren von Updates und Patches für Adobe Commerce Core |     | R |

#### Website-Verfügbarkeit

|  | Adobe | Händler |
| --- | --- | --- |
| Benutzerdefinierte Adobe Commerce-Anwendung und zugehörige Websites |     | R |

#### Leistung

|     | Adobe | Händler |
| --- | --- | --- |
| Kernanwendungsoptimierung | R |   |
| Optimieren und Optimieren von benutzerspezifischem Code |     | R |
| Benutzerdefinierter Adobe Commerce-Code |     | R |
| Belastungstests |     | R |
| Leistungstests |     | R |

{style="table-layout:auto"}


#### Protokolle und Überwachung

|     | Adobe | Händler |
| --- | --- | --- |
| Rotieren von Protokollen | R |   |
| Benutzerdefinierte Adobe Commerce-Anwendung | | R |
| Verfügbarkeit von New Relic-Diensten:<br>APM-Anwendungs- und Agentenintegration, Infrastrukturanwendung,<br>Protokollierung und Integration | R |   |
| Einrichten von New Relic-Warnhinweisen |     | R |
| Bereitstellen des New Relic-Agenten auf PaaS-Servern |     | R |

{style="table-layout:auto"}

#### Debuggen und Isolieren von Problemen

|     | Adobe | Händler |
| --- | --- | --- |
| Debuggen und Isolieren von Problemen | R | R |
| Schnelle Unterstützung des Debugging- und Problemisolierungsprozesses |     | R |

{style="table-layout:auto"}

### Anwendungs- und Dienstkonfiguration

#### Commerce-Anwendung

|     | Adobe | Händler |
| --- | --- | --- |
| Anwendungskonfiguration |     | R |
| Hinzufügen von Domänen zur Adobe Commerce-Anwendung (Basis-URLs) |     | R |
| Konfigurieren von APIs für die Verwendung von Dienstversionen, die von der bereitgestellten Adobe Commerce-Version unterstützt werden<br><br>Beispielsweise sind verschiedene Commerce-Versionen mit bestimmten PHP-, Redis- usw. kompatibel. |     | R |

{style="table-layout:auto"}

#### Aufgabenplanung mit Cron-Aufträgen

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit standardmäßiger Cron-Aufträge | R | |
| Laufende Qualität von benutzerdefinierten Cron-Aufträgen |  | R |

{style="table-layout:auto"}

#### Nachrichtenbroker für das Framework für Nachrichtenwarteschlangen

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit des RabbitMQ-Dienstes | R |   |
| Konfiguration der standardmäßigen RabbitMQ-Einstellungen | R |   |
| Laufende Qualität und Patchierung von RabbitMQ | R |   |
| Senden Sie eine Dienstanforderung, um eine mit der installierten Adobe Commerce-Version kompatible RabbitMQ-Version zu installieren. |   | R |

{style="table-layout:auto"}

#### PHP-Dienst

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit von PHP | R |   |
| Konfiguration der Standard-PHP-Einstellungen | R |     |
| Konfiguration benutzerdefinierter PHP-Einstellungen |     | R |
| Konfiguration der YAML-Datei zur Anpassung von PHP-Versionen, die mit der installierten Adobe Commerce-Version kompatibel sind |    | R |

{style="table-layout:auto"}

#### Datenbankdienste

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit von Galera- und MariaDB-Diensten | R | |
| Laufende Wartung der Standardeinstellungen für die Datenbank<br><br> (Indizierung und Optimierung der Kerntabellen, Optimierung der Standardeinstellungen für sys-admin) | R |   |
| Laufende Pflege von Handelsdaten und geänderten Einstellungen<br><br> (Konfigurieren von normalisierten vs. flachen Tabellen, Indizierung und Optimierung von benutzerdefinierten und Drittanbieter-Tabellen, Archivierung oder Entfernung von Daten, Konfigurieren von Systemverwaltungseinstellungen) |     | R |
| Konfiguration von Galera und MySQL | R |   |
| Laufende Qualität und Patching von Galera und MariaDB | R |   |
| Laufende Optimierung der Infrastruktur | R |   |
| Langsame Abfragen identifizieren und beheben |     | R |
| Senden Sie eine Dienstanfrage, um eine mit der installierten Adobe Commerce-Version kompatible MariaDB-Version zu installieren. |     | R |
| Festlegen und Verwalten von Merchant-spezifischen Datenaufbewahrungsrichtlinien (Adobe zur Datenaufbewahrung werden in der Händlervereinbarung definiert) |     | R |

{style="table-layout:auto"}

#### CDN-Dienst

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit und Qualität des CDN | R |   |
| Schnelle Dienstkonfiguration (über Erweiterung/API) |     | R |
| Schnelle Erweiterungsqualität | R |   |
| Fastly Integration VCL Snippets (gebündelt mit der Fastly Extension) - Qualität | R |   |
| Seiten-Cache-Optimierung |     | R |
| Hinzufügen von Domänen zu Diensten, zu CDN und zur Infrastruktur | R |   |
| Benutzerdefinierte VCL-Snippets |     | R |
| WAF- und WAF-Regeln | R |   |

{style="table-layout:auto"}

#### Cache-Dienst

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit des Redis-Dienstes | R |   |
| Konfiguration der standardmäßigen Redis-Einstellungen | R |   |
| Laufende Qualität und Patchen von Redis | R |   |
| Senden Sie eine Dienstanforderung, um eine Redis-Version zu installieren, die mit der installierten Adobe Commerce-Version kompatibel ist. |     | R |

{style="table-layout:auto"}

#### Suchdienst

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit von Elasticsearch | R |   |
| Konfiguration der standardmäßigen Elasticsearch-Einstellungen | R |   |
| Senden Sie eine Dienstanforderung, um eine mit der installierten Adobe Commerce-Version kompatible Elasticsearch-Version zu installieren. |  | R |

{style="table-layout:auto"}

#### Email-Dienst

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit des SendGrid-E-Mail-Diensts und seiner Integration | R |   |
| Überwachen der SendGrid-Nutzung des Händlers mit Einschränkungen | R |   |
| Der Händler ist für die Verwendung des Dienstes nur für ausgehende Transaktions-E-Mails verantwortlich<br>Der Dienst unterstützt nicht das Senden von Marketing-E-Mails. |     | R |
| Konfigurieren optionaler E-Mail-Dienste von Drittanbietern |     | R |

{style="table-layout:auto"}

#### Dienstleistungen von Dritten

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit und Qualität von Drittanbieterdiensten |     | R |

{style="table-layout:auto"}

### Commerce Services-Erweiterungen

#### Advance Reporting Service

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit des erweiterten Berichterstellungsdienstes | R |   |
| Die Konfiguration der erweiterten Berichterstellung entspricht den allgemeinen Geschäftsbedingungen für die erweiterte Berichterstellung |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit von Adobe Commerce Business Intelligence-Diensten | R |   |
| MBI-Datensynchronisierungsprozesse | R |   |
| MBI-Synchronisierungsprobleme erkennen | R |   |
| Konfigurieren der MBI-Datensynchronisierung mit Adobe Commerce Cloud Pro, Starter, On-Premises oder Nicht-Adobe Commerce<br>(API, Datenqualität und -formatierung, Händlernetzwerk, <br>DB-Verbindungen innerhalb und außerhalb von Adobe Commerce Cloud DB, über Datenschwellen) |     | R |
| Konfigurieren der MBI-Datensynchronisierung mit Adobe Commerce Cloud Pro<br> (Adobe Commerce Cloud-Datenbankkonfiguration) | R |   |

{style="table-layout:auto"}

#### Produkt-Recommendations

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit des Product Recommendations-Dienstes | R |   |

{style="table-layout:auto"}

### Netzwerkdienste

#### Bildoptimierung

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit und Qualität der Bildoptimierung | R |  |
| Konfiguration der Bildoptimierung |     | R |

{style="table-layout:auto"}

#### SSL-Zertifikate

|     | Adobe | Händler |
| --- | --- | --- |
| SSL-dediziertes Zertifikat - Ablauf | R |  |
| Bereitstellen von SSL-Zertifikaten | R |  |
| Kauf und Pflege des EV/spezifischen SSL-Zertifikats (außer den Standardeinstellungen) und Bereitstellung für Adobe |     | R |

{style="table-layout:auto"}

#### Web Application Firewall (WAF)

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit und Konfiguration der WAF | R |  |
| Beheben von falsch positiven WAF-Regeln | R | |
| Falsch positive Berichterstellung für WAF-Regeln |     | R |
| WAF-Regelverfeinerung (NICHT UNTERSTÜTZT) |     |     |
| WAF-/CDN-Protokolle |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | Händler |
| --- | --- | --- |
| Proaktive IP-Blockierung |     | R |
| Bot Protection |     | R |
| DDOS-Erkennung - Layer 3-4 | R |   |
| DDOS-Erkennung - Ebene 7 |     | R |
| DDOS-Antwort | R |   |
| Konfiguration der Beschränkung der Fastly Extension Rate und des Bot Protection (begrenzt) |     | R |

{style="table-layout:auto"}

#### Privater Link

|     | Adobe | Händler |
| --- | --- | --- |
| Konfigurieren und Verwalten von PrivateLink-Verbindungen (falls verwendet) mit einem Adobe-eigenen VPC | R |   |
| Konfigurieren und Verwalten von PrivateLink-Verbindungen (falls verwendet) mit einem Merchant-eigenen VPC |     | R |
| Verfügbarkeit von SSH (nicht privater Link) | R |   |
| Konfiguration des Endpunkts PrivateLink Inbound to Adobe Commerce Cloud Service | R |   |
| Annahme des Endpunkts PrivateLink Inbound to Adobe Commerce Cloud Service |     | R |
| Konfiguration des VPC-Dienstendpunkts von PrivateLink Inbound to Merchant |     | R |
| Annahme des VPC-Service-Endpunkts von PrivateLink Inbound to Merchant | R |   |
| Konfiguration von PrivateLink-Integrationen (Endpunkt des Kontos) |     | R |
| Konfiguration des im Handelsbesitz befindlichen VPC für den PrivateLink-Endpunkt<br><br> (einschließlich aller VPN-Verbindungen) |     | R |

{style="table-layout:auto"}

### System und Infrastruktur

#### Anwendungsserver

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit von Nginx | R |   |
| Konfiguration von Nginx | R |   |
| Laufende Qualität und Patchen von Nginx | R |   |

{style="table-layout:auto"}

#### Betriebssystem

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit des Betriebssystems | R |   |
| Laufende Qualität und Patchen des Betriebssystems | R |   |

{style="table-layout:auto"}

#### Backup, hohe Verfügbarkeit und Failover

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit von Snapshots und Backup-Prozessen | R |   |
| Planen von Backups für Staging- und Produktionsumgebungen von Cloud Pro | R |   |
| Planen von Sicherungen für Cloud Starter- und Pro-Integrationsumgebungen |     | R |
| Verfügbarkeit von HA/Failover | R |   |

{style="table-layout:auto"}

#### Cloud-Server und Skalierung

|     | Adobe | Händler |
| --- | --- | --- |
| Verfügbarkeit von CPU-Ressourcen, Rechenzentrum, Festplattenspeicher | R |   |
| Verfügbarkeit und Ausführung von Überlastungskapazitäten oder Notfallvergrößerung | R |   |
| Anfordern der Übernahmekapazität |     | R |
| Überwachen der vCPU-Auslastung anhand der Grenzwerte | R |   |

{style="table-layout:auto"}
