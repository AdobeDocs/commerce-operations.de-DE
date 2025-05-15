---
title: Gemeinsames Verantwortungs-, Sicherheits- und Betriebsmodell
description: Erfahren Sie mehr über die Sicherheitsaufgaben der einzelnen an Ihrem Adobe Commerce on Cloud-Infrastrukturprojekt beteiligten Parteien.
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: 4cd71d156ef6833185565180b297ba1b7f42a032
workflow-type: tm+mt
source-wordcount: '2791'
ht-degree: 0%

---

# Gemeinsames Verantwortungs-, Sicherheits- und Betriebsmodell

Adobe Commerce on Cloud Infrastructure ist ein PaaS-Angebot (Platform-as-a-Service), das auf einem Sicherheits- und Betriebsmodell basiert, das sich auf gemeinsame Verantwortung stützt. Diese Zuständigkeiten teilen sich Adobe, der Händler, der Cloud Service-Anbieter und der Content Delivery Network (CDN)-Anbieter. Jede Partei ist für die Sicherung und den Betrieb des Adobe Commerce-Programms und der auf der Cloud-Infrastruktur bereitgestellten händlerspezifischen Codes und Erweiterungen selbst verantwortlich.

Dieses gemeinsame Modell ermöglicht es Händlern, eine hochflexible, anpassbare und skalierbare Lösung zu entwerfen und zu implementieren, die ihren geschäftlichen Anforderungen entspricht und gleichzeitig betriebliche Verantwortlichkeiten und Kosten minimiert.

>[!VIDEO](https://video.tv.adobe.com/v/3458392/?learn=on&enablevpops)

Im Allgemeinen ist Adobe für Folgendes verantwortlich:

- Entwickeln und Verwalten von sicherem Code für Kernanwendungen
- Gewährleistung der Plattformsicherheit
- Sicherstellen, dass die Plattform SOC 2- und PCI-kompatibel und mit PCI-kompatiblen Technologiekomponenten (z. B. PHP, Redis) kompatibel ist
- Reaktion auf Sicherheitsprobleme bezüglich der Kernplattform
- Arbeiten mit Cloud-Service-Anbietern und CDN-Partnern, um auftretende Probleme zu beheben

Händler sind für Folgendes verantwortlich:

- Gewährleistung der Sicherheit für benutzerdefinierten Code und Integrationen mit Anwendungen von Drittanbietern
- Sichere Anwendungsentwicklung
- Einholung der PCI-Zertifizierung, falls vom Zahlungsverarbeiter des Händlers angefordert
- Reaktion auf Sicherheitsvorfälle

## Zuständigkeiten von Adobe

Adobe ist für die Sicherheit und Verfügbarkeit der Adobe Commerce in der Cloud-Infrastrukturumgebung und des zentralen Lösungs-Codes verantwortlich. Darüber hinaus ist Adobe für die erforderlichen Aktivitäten und Mechanismen verantwortlich, die die Sicherheit der Adobe Commerce on Cloud Infrastructure-Lösung gewährleisten, darunter:

- Anwenden von Sicherheit auf Serverebene und Patches für von Adobe Commerce unterstützte Anwendungen auf Cloud-Infrastrukturen wie Cloud-Datenspeicher und Suchfunktionen
- Durchführen von Penetrationstests und Scannen des Kern-Codes von Adobe Commerce auf Cloud-Infrastruktur
- Durchführung halbjährlicher Überprüfungen und Audits von IAM-Lösungen (Identity and Access Management) und Berechtigungsverwaltungslösungen von Public Cloud Service Providern (PCI Compliance Requirement)
- Durchführung halbjährlicher Überprüfungen und Audits autorisierter Anwender, einschließlich Adobe-Mitarbeitern und -Auftragnehmern (PCI-Compliance-Anforderung)
- Durchführung jährlicher Tests und Dokumentation der Sicherungs- und Wiederherstellungsfunktionen
- Server- und Perimeter-Firewalls konfigurieren
- Verbinden und Konfigurieren des Repositorys der Adobe Commerce in der Cloud-Infrastruktur
- Definieren, Testen, Implementieren und Dokumentieren von Notfall-Wiederherstellungsplänen (Disaster Recovery, DR) für die Bereiche, für die Adobe zuständig ist
- Definieren von Regeln für die globale Plattform-Web-Anwendungs-Firewall (WAF)
- Abhärten des Betriebssystems (OS)
- Implementierung und Wartung der Integration von Content Distribution Network (CDN)- und Application Performance Management (APM)-Lösungen mit Adobe Commerce auf Cloud-Infrastrukturen
- Regelmäßige Sicherheits- und andere Updates für den Kern-Code von Adobe Commerce in der Cloud-Infrastruktur (Patches müssen vom Händler angewendet werden)
- Verwalten von Support für Händler und Support-Zugriffssteuerungen (z. B. Zendesk)
- Überwachung, Protokollierung und Behebung von Sicherheitsvorfällen in Bezug auf die Adobe Commerce auf Cloud-Infrastrukturplattformen
- Überwachung des Plattformbetriebs und Bereitstellung von 24/7-Support für Adobe Commerce auf Händlern mit Cloud-Infrastruktur
- Bereitstellung der Produktions- und Staging-Umgebungen
- Bewertung potenzieller Sicherheitsbedrohungen für den Plattformbetrieb und die Infrastruktur
- Skalierung von Datenverarbeitung, Speicher, Raster und anderen Ressourcen, wie in der Service-Level-Vereinbarung (SLA) mit dem Händler beschrieben
- Einrichten des DNS (nur Adobe Commerce auf der Cloud-Infrastrukturplattform)
- Plattform auf Sicherheitslücken testen

Adobe verwaltet die PCI-Zertifizierung für die für die Adobe Commerce-Lösung verwendeten Infrastrukturen und Services.  Händler sind für die Einhaltung von benutzerspezifischem Code, System- und Netzwerkprozessen sowie für die Organisation verantwortlich.

Adobe stellt auch die Verfügbarkeit der Infrastruktur des Händlers sicher, wie im entsprechenden SLA vereinbart.

## Händlerpflichten

Der Händler ist für die Befolgung der Best Practices für die Sicherheit für seine spezifische, angepasste Instanz der Adobe Commerce on Cloud Infrastructure-Lösung verantwortlich:

- Hinzufügen der erforderlichen Konfigurationsdateien für Adobe Commerce in der Cloud-Infrastruktur zum Repository
- Anwenden von Sicherheits- und anderen Patches auf die benutzerdefinierte Adobe Commerce on Cloud-Infrastrukturlösung unmittelbar nach ihrer Veröffentlichung durch Adobe
- Anwenden von Sicherheits- und anderen Patches auf alle benutzerdefinierten Erweiterungen und den Code, unmittelbar nach ihrer Veröffentlichung durch den Anbieter
- Erstellen, Bereitstellen und Testen von benutzerdefinierten VCL-Lackdateien
- Entwurf, Design, Installation, Integration und Sicherung der benutzerdefinierten Adobe Commerce on Cloud-Infrastrukturlösung, einschließlich aller benutzerdefinierten Erweiterungen und Code
- Gewähren und Widerrufen des Benutzerzugriffs auf die Instanz des Händlers von Adobe Commerce auf Cloud-Infrastrukturkonfiguration, -Programm und -Plattform
- Behandlung von Sicherheitsproblemen im Zusammenhang mit dem internen Netzwerk, den Servern, der Infrastruktur und allen benutzerdefinierten Anwendungen des Händlers, die auf der Adobe Commerce on Cloud-Infrastrukturplattform erstellt wurden
- Installieren des Befehlszeilen-Integrations-Tools (Command-Line Integration, CLI) für Adobe Commerce auf der Cloud-Infrastruktur
- Einhaltung der erforderlichen PCI-Compliance der benutzerdefinierten Anwendung und anderer interner Prozesse gemäß den PCI-DSS-Richtlinien

  >[!NOTE]
  >
  >Um die Bereiche zu minimieren, die überprüft werden müssen, basiert die PCI-Compliance für den Händler auf den PCI-Zertifizierungen von Adobe Commerce und dem Cloud-Hosting-Anbieter.

- Ausführen von PCI-ASV-Scans und Beheben von Problemen im Core Adobe Commerce auf Cloud-Infrastrukturcode und -Plattform
- Überwachen aller Anwendungsaktivitäten, die eine potenzielle Sicherheitsbedrohung aufdecken könnten, einschließlich Penetrationstests, Schwachstellenscans und Protokollen
- Überwachung und Reaktion auf Sicherheitsvorfälle, einschließlich Forensik, Behebung und Reporting im Zusammenhang mit der Adobe Commerce der Cloud-Infrastrukturlösung und den Benutzerkonten des Händlers
- Beziehen eines DNS-Anbieters und Konfigurieren und Verwalten von händlerspezifischen DNS-Einträgen
- Ausführen von Leistungstests für das angepasste Programm
- Sichern des Zugriffs auf Platform-Konten, Instanzzugriff und Anwendung
- Tests und Qualitätssicherung des benutzerdefinierten Programms
- Gewährleistung der Sicherheit aller Systeme oder Netzwerke, die der Händler mit der Adobe Commerce on Cloud Infrastructure-Anwendung verbindet

## Zuständigkeiten des Cloud Service-Anbieters

Adobe nutzt etablierte Cloud Service-Anbieter als Host für die Cloud-Server-Infrastruktur für Adobe Commerce in der Cloud-Infrastruktur. Diese Anbieter sind für die Sicherheit des Netzwerks verantwortlich, einschließlich Routing, Switching und Perimeter-Netzwerksicherheit über Firewall-Systeme und Intrusion Detection Systems (IDS). Cloud-Service-Anbieter sind auch für die physische Sicherheit von Rechenzentren, in denen die Adobe Commerce on Cloud Infrastructure-Lösung gehostet wird, und die Umgebungssicherheit von Rechenzentren verantwortlich.

Cloud Service-Anbieter sind auch verantwortlich für:

- Wartung der PCI DSS-, SOC 2- und ISO 27001-Zertifizierungen für ihre Cloud-Services
- Sichern des Hypervisors
- Sicherung des Rechenzentrums, einschließlich physischem und Netzwerkzugriff

## Zuständigkeiten des CDN-Anbieters

Die Adobe Commerce on Cloud Infrastructure-Lösung verwendet CDN-Anbieter, um die Seitenladezeit zu verkürzen, Inhalte zwischenzuspeichern und veraltete Inhalte sofort zu löschen. Diese Anbieter sind auch für Sicherheitsprobleme verantwortlich, die direkt mit ihrem CDN zusammenhängen oder sich auf ihr CDN auswirken, sowie für die Definition und Pflege von CDN-WAF-Regeln.

## Zusammenfassung der Sicherheitsaufgaben

>[!BEGINSHADEBOX]

Die folgende Zusammenfassungstabelle verwendet das RACI-Modell, um die Sicherheitsaufgaben anzuzeigen, die zwischen Adobe, dem Händler und dem Cloud Service-Anbieter geteilt sind:

**R** — Verantwortlich
**a** — Rechenschaftspflichtig
**C** — konsultiert
**i** — informiert

>[!ENDSHADEBOX]

<table>
<thead>
  <tr>
    <th>Aufgabe</th>
    <th>Adobe</th>
    <th>Großhändler</th>
    <th>Cloud-Service-Anbieter</th>
    <th>CDN-Provider</th>
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
    <td>Anwenden von Patches auf unterstützende <br> (z. B. Nginx oder MySQL)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definieren der WAF-Ursprungsregeln</td>
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
    <td>Bereitstellen von Platform-WAF-Regeln</td>
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
    <td>Beheben von Hauptfehlern in Adobe Commerce auf Cloud-Infrastruktur-Code</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Veröffentlichung von Adobe Commerce auf Cloud-Infrastruktur-Patches</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Skalierung (Compute und Storage)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Skalierung (PaaS und Raster)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Sicherstellen des Zugriffs auf Quell-Code, einschließlich repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installieren des CLI-Tools Adobe Commerce on Cloud Infrastructure</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Hinzufügen von Konfigurationsdateien für Adobe Commerce in der Cloud-Infrastruktur zum Repository</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Erstellen eines Projekts für Händler (Onboarding-Benutzeroberfläche)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Verbinden von Repositorys mit Adobe Commerce in der Cloud-Infrastruktur</td>
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
    <td>Erstellen von Benutzern für den Release Manager (Onboarding-Benutzeroberfläche)</td>
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
    <td>Bereitstellen von Code in Staging</td>
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
    <td>Anpassen von Adobe Commerce in Cloud-Infrastrukturen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Testen der Leistung von benutzerdefinierten Adobe Commerce in der Cloud-Infrastruktur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Testen des benutzerdefinierten Programms</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Design und Design von benutzerdefinierten Anwendungen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>Erstellen, Bereitstellen und Testen von benutzerdefinierten VCLs für Lackierungen</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Konfigurieren von DNS (nur Plattforminfrastruktur)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Entwickeln einer CDN-Erweiterung und Beheben von Fehlern</td>
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
    <td>Unterstützung von CDN<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Konfigurieren von New Relic APM- und Infrastrukturanwendungen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Installieren von New Relic APM- und Infrastrukturanwendungen</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Unterstützung von New Relic APM- und Infrastrukturanwendungen</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Konfigurieren von nginx<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Beziehen eines DNS-Anbieters (nur Pro)</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Abhärten des Betriebssystems</td>
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
    <td>Beheben von Sicherheitsproblemen von Händlern</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Beheben von Sicherheitsproblemen in der Adobe Commerce-Cloud-Infrastruktur</td>
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
    <td>Unterstützung von Adobe bei der Sicherheitsforschung (Software)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Unterstützung von Adobe bei der Sicherheitsforschung (Scans/Audits)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Durchführen von PCI-ASV-Scans</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adobe Commerce auf Cloud-Infrastruktur wiederherstellen PCI-Scans<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Beheben von PaaS-PCI-Scans</td>
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
    <td>Verwalten von Adobe Commerce auf Verschlüsselungsschlüsseln für die Cloud-Infrastruktur</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Scannen von anwenderdefiniertem Adobe Commerce auf Cloud-Infrastrukturinstanzen</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Überwachen von Sicherheitsprotokollen</td>
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
    <td>Verwalten von Support-Zugriffssteuerungen (Teleport)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Steuerung des Händlersupport und -zugriffs</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Jährliche Tests und Dokumentation des Adobe DR-Plans sowie der Sicherung und Wiederherstellung</td>
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
      <p><sup><strong>1</strong></sup> Nur wenn das Repository Adobe Commerce in der Cloud-Infrastruktur als Haupt-Repository verwendet wird. Die Nutzung anderer externer Repositorys liegt in der alleinigen Verantwortung des Händlers.</p>
      <p><sup><strong>2</strong></sup> Adobe bietet bei Problemen mit CDN-Anbietern Support der Stufe 1.</p>
      <p><sup><strong>3</strong></sup> Der Händler ist für alle Ngnix-Steuerungen verantwortlich, die er für seine Anwendungen konfiguriert.</p>
      <p><sup><strong>4</strong></sup> Für PCI werden die Anforderungen an Penetrationstests zwischen Adobe und dem Händler geteilt.</p>
    </td>
  </tr>
</tfoot>
</table>

## Zusammenfassung der operativen Zuständigkeiten

>[!BEGINSHADEBOX]

In den folgenden Übersichtstabellen werden die betrieblichen Zuständigkeiten für Adobe und Händler bei der Entwicklung, Bereitstellung, Wartung und Sicherung von Adobe Commerce in Cloud-Infrastrukturen erläutert.

>[!ENDSHADEBOX]

### Programmierung und Entwicklung

#### Adobe Commerce-Kerncode

|     | Adobe | Großhändler |
| --- | --- | --- |
| Veröffentlichen von Aktualisierungen und Patches in Adobe Commerce Core | R |     |
| Verfügbarkeit und Patchen des Dateisystems | R |  |
| Veröffentlichen von Updates und Patches in ECE-Tools | R |     |
| Qualität der Adobe Commerce-Kernanwendungen | R |     |

{style="table-layout:auto"}

#### Code-Repository

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit von repo.magento.com | R |     |
| Verfügbarkeit von Adobe Commerce auf dem Cloud-Git-Server | R |     |
| Andere vom Händler ausgewählte Code-Repositorys (GitHub, Bitbucket, gehosteter Git-Server) |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | Großhändler |
| --- | --- | --- |
| Bereitstellen von Cloud Docker-Containern zum Herunterladen | R |   |
| Bereitstellung und Einrichtung von Cloud Docker (optional) |     | R |
| Alle anderen lokalen Entwicklungseinstellungen |     | R |

{style="table-layout:auto"}

#### COMMERCE CLOUD CLI

|     | Adobe | Großhändler |
| --- | --- | --- |
| Laufende Qualität und Aktualisierung der ECE-Tools | R |   |
| Installieren der neuesten ECE-Tools-Version |     | R |

{style="table-layout:auto"}

#### Anpassungen

|  | Adobe | Großhändler |
| --- | --- | --- |
| Benutzerdefinierte Adobe Commerce-Module und -Code |     | R |
| Erweiterungen |     | R |
| Benutzerdefinierte Integrationen |     | R |

{style="table-layout:auto"}

#### Bereitstellungen

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit der Infrastruktur zum Erstellen und Bereitstellen von Code | R |   |
| Laufende Qualität der Konfigurations-Pipeline für das Erstellen und Bereitstellen von Infrastrukturen | R |   |
| Konfiguration des Builds und der Bereitstellung statischer Inhalte |     | R |
| Aufbau und Ausführung des Bereitstellungs-Governance-Prozesses: Kriterien und Änderungsverwaltung |     | R |
| Bereitstellen in der Staging-Umgebung |     | R |
| Bereitstellen in der Produktionsumgebung |     | R |
| Produktions-Rollbacks |     | R |

{style="table-layout:auto"}

#### Synchronisieren von Umgebungen

Händler sind für die Synchronisierung von Daten zwischen Umgebungen verantwortlich.

#### Flicken

|     | Adobe | Großhändler |
| --- | --- | --- |
| Installieren von Updates und Patches für ECE-Tools |     | R |
| Installieren von Updates und Patches für Adobe Commerce Core |     | R |

#### Website-Verfügbarkeit

|  | Adobe | Großhändler |
| --- | --- | --- |
| Angepasste Adobe Commerce-Anwendung und zugehörige Websites |     | R |

#### Leistung

|     | Adobe | Großhändler |
| --- | --- | --- |
| Optimierung und Optimierung von Kernanwendungen | R |   |
| Optimierung von benutzerdefiniertem Code |     | R |
| Benutzerdefinierter Adobe Commerce-Code |     | R |
| Belastungstests |     | R |
| Leistungstests |     | R |

{style="table-layout:auto"}


#### Protokolle und Überwachung

|     | Adobe | Großhändler |
| --- | --- | --- |
| Rotierende Protokolle | R |   |
| Benutzerdefinierte Adobe Commerce-Anwendung | | R |
| Verfügbarkeit von New Relic-Services:<br>APM-Anwendungs- und Agentenintegration, Infrastrukturanwendung<br>Protokollierung und Integration | R |   |
| Einrichten von New Relic-Warnhinweisen |     | R |
| Bereitstellen des New Relic-Agenten auf PaaS-Servern | R |  |

{style="table-layout:auto"}

#### Debugging und Problemisolierung

|     | Adobe | Großhändler |
| --- | --- | --- |
| Debugging und Problemisolierung | R | R |
| Rechtzeitige Unterstützung des Debugging- und Problemisolierungsprozesses |     | R |

{style="table-layout:auto"}

### Anwendungs- und Dienstkonfiguration

#### Commerce-Anwendung

|     | Adobe | Großhändler |
| --- | --- | --- |
| Anwendungskonfiguration |     | R |
| Hinzufügen von Domains zur Adobe Commerce-Anwendung (Basis-URLs) |     | R |
| Konfigurieren von PaaS für die Verwendung von Dienstversionen, die von der bereitgestellten Adobe Commerce-Version unterstützt werden<br><br> Beispielsweise sind verschiedene Commerce-Versionen mit bestimmten Versionen von PHP, Redis usw. kompatibel. |     | R |

{style="table-layout:auto"}

#### Aufgabenplanung mit Cron-Aufträgen

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit von standardmäßigen Cron-Aufträgen | R | |
| Laufende Qualität von benutzerdefinierten Cron-Aufträgen |  | R |

{style="table-layout:auto"}

#### Message Broker für Message Queue Framework

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit des RabbitMQ-Service | R |   |
| Konfiguration der Standard-RabbitMQ-Einstellungen | R |   |
| Laufende Qualität und Patchen von RabbitMQ | R |   |
| Senden einer Service-Anfrage zur Installation einer RabbitMQ-Version, die mit der installierten Adobe Commerce-Version kompatibel ist |   | R |

{style="table-layout:auto"}

#### PHP-Dienst

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit von PHP | R |   |
| Konfiguration der PHP-Standardeinstellungen | R |     |
| Konfiguration von benutzerdefinierten PHP-Einstellungen |     | R |
| Konfiguration der YAML-Datei, um PHP-Versionen mit der installierten Adobe Commerce-Version kompatibel auszurichten |    | R |

{style="table-layout:auto"}

#### Datenbank-Services

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit von Galera- und MariaDB-Services | R | |
| Laufende Pflege der standardmäßigen Datenbankeinstellungen <br><br>Indizierung und Optimierung von Kerntabellen, Optimierung der standardmäßigen Systemadministratoreinstellungen) | R |   |
| Laufende Pflege der Händlerdaten und geänderte Einstellungen<br><br>(Konfigurieren normalisierter oder flacher Tabellen, Indizieren und Optimieren von benutzerdefinierten und Drittanbietertabellen, Archivieren oder Entfernen von Daten, Konfigurieren von Systemadministrationseinstellungen) |     | R |
| Konfiguration von Galera und MySQL | R |   |
| Laufende Qualität und Patches von Galera und MariaDB | R |   |
| Laufende Infrastrukturoptimierung | R |   |
| Identifizieren und Korrigieren langsamer Abfragen |     | R |
| Senden einer Service-Anfrage zur Installation einer MariaDB-Version, die mit der installierten Adobe Commerce-Version kompatibel ist |     | R |
| Einrichten und Verwalten von spezifischen Richtlinien zur Datenaufbewahrung für Händler (die Richtlinien zur Datenaufbewahrung von Adobe werden im Händlervertrag definiert) |     | R |

{style="table-layout:auto"}

#### CDN-Service

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit und Qualität des CDN | R |   |
| Fastly-Service-Konfiguration (über Erweiterung/API) |     | R |
| Fastly-Erweiterungsqualität | R |   |
| Fastly Integration VCL Snippets (mit der Fastly-Erweiterung gebündelt) Qualität | R |   |
| Optimierung des Seiten-Caches |     | R |
| Hinzufügen von Domains zu Services, CDN und zur Infrastruktur | R |   |
| Benutzerdefinierte VCL-Snippets |     | R |
| WAF- und WAF-Regeln | R |   |

{style="table-layout:auto"}

#### Cache-Dienst

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit des Redis-Service | R |   |
| Konfiguration der Standard-Redis-Einstellungen | R |   |
| Kontinuierliche Qualität und Patchen von Redis | R |   |
| Senden einer Service-Anfrage zum Installieren einer Redis-Version, die mit der installierten Adobe Commerce-Version kompatibel ist |     | R |

{style="table-layout:auto"}

#### Suchdienst

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit von Elasticsearch | R |   |
| Konfiguration der standardmäßigen Elasticsearch-Einstellungen | R |   |
| Senden einer Service-Anfrage zur Installation einer Elasticsearch-Version, die mit der installierten Adobe Commerce-Version kompatibel ist |  | R |

{style="table-layout:auto"}

#### E-Mail-Dienst

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit des SendGrid-E-Mail-Dienstes und dessen Integration | R |   |
| Überwachung der SendGrid-Nutzung des Händlers in Bezug auf Beschränkungen | R |   |
| Der Händler ist nur für die Verwendung des Dienstes für ausgehende Transaktions-E<br>Mails verantwortlich. Der Dienst unterstützt nicht den Versand von Marketing-E-Mails. |     | R |
| Konfigurieren optionaler E-Mail-Dienste von Drittanbietern |     | R |

{style="table-layout:auto"}

#### Services von Drittanbietern

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit und Qualität von Drittanbieterdiensten |     | R |

{style="table-layout:auto"}

### Commerce Services-Erweiterungen

#### Advance Reporting Service

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit des erweiterten Reporting-Services | R |   |
| Die Konfiguration des erweiterten Reportings entspricht den Geschäftsbedingungen für erweiterte Berichte |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit von Adobe Commerce Business Intelligence-Services | R |   |
| MBI-Datensynchronisierungsprozesse | R |   |
| Erkennen von MBI-Synchronisierungsproblemen | R |   |
| Konfigurieren der MBI-Datensynchronisation mit Adobe Commerce Cloud Pro, Starter, On-Premise oder Nicht-Adobe Commerce<br> (API, Datenqualität und -formatierung, Händlernetzwerk, <br>DB-Verbindungen sowohl innerhalb als auch außerhalb von Adobe Commerce Cloud DB, über Datenschwellenwerte) |     | R |
| Konfigurieren der MBI-Datensynchronisation mit Adobe Commerce Cloud Pro<br>(Adobe Commerce Cloud-Datenbankkonfiguration) | R |   |

{style="table-layout:auto"}

#### Produkt Recommendations

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit des Product Recommendations-Service | R |   |

{style="table-layout:auto"}

### Netzwerk-Services

#### Bildoptimierung

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit und Qualität der Bildoptimierung | R |  |
| Konfiguration der Bildoptimierung |     | R |

{style="table-layout:auto"}

#### SSL-Zertifikate

|     | Adobe | Großhändler |
| --- | --- | --- |
| Dediziertes SSL-Zertifikat - Gültigkeit | R |  |
| Bereitstellen von SSL-Zertifikaten | R |  |
| Erwerb und Pflege von EV-/spezifischen SSL-Zertifikaten (außer den bereitgestellten Standardwerten) und Bereitstellung an Adobe |     | R |

{style="table-layout:auto"}

#### Web Application Firewall (WAF)

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit und Konfiguration von WAF | R |  |
| Umgang mit falsch positiven WAF-Regeln | R | |
| Meldung von falsch positiven WAF-Regeln |     | R |
| Regeloptimierung für WAF (NICHT UNTERSTÜTZT) |     |     |
| WAF-/CDN-Protokolle |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | Großhändler |
| --- | --- | --- |
| Proaktive IP-Blockierung |     | R |
| Bot-Schutz |     | R |
| DDOS-Erkennung - Ebene 3-4 | R |   |
| DDOS-Erkennung - Ebene 7 |     | R |
| DDOS-Antwort | R |   |

{style="table-layout:auto"}

#### Privater Link

|     | Adobe | Großhändler |
| --- | --- | --- |
| Konfigurieren und Verwalten von PrivateLink-Verbindungen (falls verwendet) mit einer Adobe-eigenen VPC | R |   |
| Konfigurieren und Verwalten von PrivateLink-Verbindungen (falls verwendet) mit einer VPC im Besitz eines Händlers |     | R |
| Verfügbarkeit von SSH (nicht-privater Link) | R |   |
| Konfiguration des privaten Links zum Adobe Commerce Cloud Service-Endpunkt | R |   |
| Akzeptieren des privaten Links zum Adobe Commerce Cloud Service-Endpunkt |     | R |
| Konfiguration von PrivateLink Inbound auf den VPC Service-Endpunkt des Händlers |     | R |
| Akzeptieren des über den VPC-Service-Endpunkt des Händlers eingehenden PrivateLink | R |   |
| Konfiguration von PrivateLink-Integrationen (Endpunkt zu Konto) |     | R |
| Konfiguration des händlereigenen VPC für den PrivateLink-<br><br> (einschließlich VPN-Verbindungen) |     | R |

{style="table-layout:auto"}

### System und Infrastruktur

#### Anwendungs-Server

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit von Nginx | R |   |
| Konfiguration von Nginx | R |   |
| Kontinuierliche Qualität und Patchen von Nginx | R |   |

{style="table-layout:auto"}

#### Betriebssystem

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit des Betriebssystems | R |   |
| Laufende Qualität und Patches des Betriebssystems | R |   |

{style="table-layout:auto"}

#### Sicherung, hohe Verfügbarkeit und Failover

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit von Snapshots und Backup-Prozessen | R |   |
| Planung von Backups für Cloud Pro-Staging- und Produktionsumgebungen | R |   |
| Planung von Backups für Cloud Starter- und Pro Integration-Umgebungen |     | R |
| Verfügbarkeit von HA/Failover | R |   |

{style="table-layout:auto"}

#### Cloud-Server und Skalierung

|     | Adobe | Großhändler |
| --- | --- | --- |
| Verfügbarkeit von CPU-Ressourcen, Rechenzentrum, Festplattenspeicher | R |   |
| Verfügbarkeit und Ausführung der Überlastungskapazität oder Notfall-Upsizing | R |   |
| Anforderung von Überspannungskapazität |     | R |
| Überwachen der vCPU-Auslastung anhand der Limits | R |   |

{style="table-layout:auto"}
