---
title: Cloud-Infrastruktur-Sicherheit
description: 'Erfahren Sie, wie wir Adobe Commerce in Cloud-Infrastrukturen sicher halten. '
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---


# Sicherheit

Die Adobe Commerce Pro-Planarchitektur ist für eine besonders sichere Umgebung konzipiert. Jeder Kunde wird in einer eigenen isolierten Serverumgebung bereitgestellt, die von anderen Kunden getrennt ist. Die Sicherheitsdetails der Produktionsumgebung werden nachfolgend beschrieben.

## Webbrowser

Der Großteil des in die Cloud-Umgebung eingehenden und aus ihr ausgehenden Traffics stammt aus den Webbrowsern der Verbraucher. Der Kundentraffic kann mit HTTPS für alle Seiten auf der Website gesichert werden (entweder mithilfe eines gemeinsam genutzten SSL-Zertifikats oder des eigenen SSL-Zertifikats des Kunden gegen eine zusätzliche Gebühr). Checkout- und Kontoseiten werden immer über HTTPS bereitgestellt. Die Best Practice ist, alle Seiten unter HTTPS bereitzustellen.

## CDN (Content Delivery Network)

Fastly bietet einen CDN- und verteilten Denial of Service (DDoS)-Schutz. Das Fastly CDN hilft, den direkten Zugriff auf die Herkunftsserver zu isolieren. Das öffentliche DNS verweist nur auf das Fastly Network. Die Fastly DDoS Lösung schützt vor hochgradig störenden Layer 3- und Layer 4-Angriffen sowie komplexeren Layer 7-Angriffen. Layer-7-Angriffe können mithilfe benutzerdefinierter Regeln blockiert werden, die auf den gesamten HTTP/HTTPS-Anforderungen basieren und auf Client- und Anforderungskriterien basieren, einschließlich Kopfzeilen, Cookies, Anfragepfad und Client-IP, oder Indikatoren wie Geolocation.

## Webanwendungs-Firewall (WAF)

Die Fastly Web Application Firewall (WAF) wird verwendet, um zusätzlichen Schutz zu bieten. Die Cloud-basierte WAF von Fastly verwendet Drittanbieterregeln aus kommerziellen und Open-Source-Quellen wie dem OWASP-Kernregelsatz. Darüber hinaus werden Commerce-spezifische Adoben verwendet. Kunden sind vor wichtigen Angriffen auf Anwendungsebene geschützt, einschließlich Injizierungsangriffen und böswilligen Eingaben, Cross-Site-Scripting, Datenexfiltration, HTTP-Protokollverletzungen und anderen OWASP Top 10-Bedrohungen.

Die WAF-Regeln werden von Adobe Commerce aktualisiert, wenn neue Schwachstellen erkannt werden, die es Managed Services ermöglichen, Sicherheitsprobleme vor Softwarepatches zu &quot;virtuell zu patchen&quot;. Die Fastly WAF bietet keine Ratenbegrenzungs- oder Bot-Erkennungsdienste an. Bei Bedarf können Kunden einen Drittanbieter-Bot-Erkennungsdienst lizenzieren, der mit Fastly kompatibel ist.

## Virtual Private Cloud (VPC)

Die Adobe Commerce Pro-Planproduktionsumgebung ist als Virtual Private Cloud (VPC) konfiguriert, sodass Produktionsserver isoliert sind und nur über begrenzte Möglichkeiten zur Verbindung mit und aus der Cloud-Umgebung verfügen. Nur sichere Verbindungen zu den Cloud-Servern sind zulässig. Für Dateiübertragungen können sichere Protokolle wie SFTP oder rsync verwendet werden.

Kunden können SSH-Tunnel verwenden, um die Kommunikation mit der Anwendung zu sichern. Der Zugriff auf AWS PrivateLink ist gegen eine zusätzliche Gebühr möglich. Alle Verbindungen zu diesen Servern werden über AWS Security Groups gesteuert, eine virtuelle Firewall, die Verbindungen zur Umgebung einschränkt. Die technischen Ressourcen der Kunden können über SSH auf diese Server zugreifen.

## Verschlüsselung

Amazon Elastic Block Store (EBS) wird für die Speicherung verwendet. Alle EBS-Volumes werden mit dem AES-265-Algorithmus verschlüsselt. Dies bedeutet, dass die Daten während der Ruhezeit verschlüsselt werden. Das System verschlüsselt auch Daten während der Übertragung zwischen dem CDN und dem Herkunftsserver sowie zwischen den Herkunftsservern. Kundenkennwörter werden als Hashes gespeichert. Sensible Anmeldeinformationen, einschließlich der für das Payment Gateway, werden mit dem SHA-256-Algorithmus verschlüsselt.

Die Adobe Commerce-Anwendung unterstützt keine Verschlüsselung oder Verschlüsselung auf Spalten- oder Zeilenebene, wenn sich die Daten nicht im Ruhezustand befinden oder sich nicht im Durchlauf zwischen Servern befinden. Der Kunde kann Verschlüsselungsschlüssel innerhalb der Anwendung verwalten. Die vom System verwendeten Schlüssel werden im Schlüsselverwaltungssystem von AWS gespeichert und müssen von Managed Services verwaltet werden, um Teile des Dienstes bereitzustellen.

## Penetrationstests

Managed Services führt regelmäßige Penetrationstests für das Adobe Commerce-Cloud-System mit der vordefinierten Anwendung durch. Kunden sind für alle Penetrationstests ihrer angepassten Anwendung verantwortlich.

## Zahlungseingang

Adobe Commerce erfordert Payment Gateway-Integrationen, bei denen Kreditkartendaten direkt vom Browser des Kunden an das Payment Gateway weitergeleitet werden. Die Kartendaten sind in keiner der Adobe Commerce Pro Plan Managed Services-Umgebungen verfügbar. Aktionen, die die Transaktionen der E-Commerce-Anwendung betreffen, werden mithilfe eines Verweises auf die Transaktion vom Gateway ausgeführt.

## Adobe Commerce-Anwendung

Adobe testet den Kernanwendungscode regelmäßig auf Sicherheitslücken. Patches für Mängel und Sicherheitsprobleme werden den Kunden zur Verfügung gestellt. Das Produktsicherheitsteam validiert Adobe Commerce-Produkte gemäß den Sicherheitsrichtlinien der OWASP-Anwendung. Zur Prüfung und Überprüfung der Einhaltung werden verschiedene Tools zur Bewertung von Sicherheitslücken und externe Anbieter verwendet. Zu den Sicherheitstools gehören:

- Statische und dynamische Prüfung mit Veracode
- Quellcode-Scannen von RIPS
- Sicherheitsüberprüfungsdienste von Trustwave und Alert Logic
- Burp Suite Pro
- OWASPZAP
- undSqlMap

Die vollständige Codebasis wird mit diesen Tools alle zwei Wochen überprüft. Kunden werden durch direkte E-Mails, Benachrichtigungen in der Anwendung und im [Sicherheitszentrum](https://magento.com/security) über Sicherheits-Patches benachrichtigt.

Kunden müssen sicherstellen, dass diese Patches gemäß den PCI-Richtlinien innerhalb von 30 Tagen nach ihrer Veröffentlichung auf ihre benutzerdefinierte Anwendung angewendet werden. Adobe bietet außerdem ein [Sicherheitsscan-Tool](https://docs.magento.com/user-guide/magento/security-scan.html), mit dem Händler ihre Sites regelmäßig überwachen und Updates zu bekannten Sicherheitsrisiken, Malware und unbefugtem Zugriff erhalten können. Das Security Scan Tool ist ein kostenloser Service und kann auf jeder Adobe Commerce-Version ausgeführt werden.

Um Sicherheitsforscher dazu zu ermutigen, Schwachstellen zu identifizieren und zu melden, verfügt Adobe Commerce über ein [Fehlerbounty-Programm](https://hackerone.com/magento) sowie interne Tests. Darüber hinaus erhält der Kunde bei Bedarf den vollständigen Quellcode der Anwendung für seine eigene Überprüfung.

## Schreibgeschütztes Dateisystem

Der gesamte ausführbare Code wird in einem schreibgeschützten Dateisystembild bereitgestellt, wodurch die für Angriffe verfügbaren Oberflächen erheblich reduziert werden. Der Implementierungsprozess erstellt ein Squash-FS-Bild. Dieser Ansatz verringert die Möglichkeiten, PHP- oder JavaScript-Code in das System zu injizieren oder die Adobe Commerce-Anwendungsdateien zu ändern.

## Remote-Implementierung

Die einzige Möglichkeit, ausführbaren Code in die Managed Services-Produktionsumgebung zu übertragen, besteht darin, ihn über einen Bereitstellungsprozess auszuführen. Dazu gehört das Pushen von Quellcode aus Ihrem Quell-Repository in ein Remote-Repository, das einen Bereitstellungsprozess initiiert. Der Zugriff auf dieses Bereitstellungsziel wird gesteuert, sodass Sie die vollständige Kontrolle darüber haben, wer auf das Bereitstellungsziel zugreifen kann. Alle Implementierungen von Anwendungs-Code in der Nicht-Produktionsumgebung werden vom Kunden gesteuert.

## Protokollierung

Alle AWS-Aktivitäten werden in AWS CloudTrail protokolliert. Linux-, Anwendungs- und Datenbankprotokolle werden auf den Produktionsservern gespeichert und in Backups gespeichert. Alle Quellcodeänderungen werden in einem Git-Repository aufgezeichnet. Der Bereitstellungsverlauf ist in der Adobe Commerce [Project Web Interface](https://devdocs.magento.com/cloud/project/projects.html#login) verfügbar. Der gesamte Support-Zugriff wird protokolliert und Support-Sitzungen werden aufgezeichnet.

## Sensible Daten

Vertrauliche Daten können entweder personenbezogene Daten von Verbrauchern oder vertrauliche Daten von Managed Services-Kunden umfassen. Der Schutz sensibler Kunden- und Verbraucherdaten ist eine wichtige Verpflichtung für Adobe Commerce Managed Services. Sowohl Managed Services als auch unsere Kunden haben rechtliche Verpflichtungen in Bezug auf personenbezogene Daten. Zusätzlich zu den Sicherheitsfunktionen der Architektur gibt es weitere Steuerelemente, um die Verteilung und den Zugriff auf vertrauliche Daten zu beschränken.

Kunden besitzen ihre Daten und haben die Kontrolle darüber, wo sich diese Daten befinden. Der Kunde gibt den Speicherort an, an dem sich seine Produktions- und Entwicklungsinstanzen befinden. Sie geben außerdem an, welcher Speicherort in Verbindung mit Commerce für die Magento Business Intelligence-Umgebung (MBI) verwendet wird und ob diese MBI-Anwendung Zugriff auf persönlich identifizierbare Informationen hat oder nicht. Produktionsinstanzen können in den meisten AWS-Regionen lokalisiert werden, während Entwicklungs- und MBI-Umgebungen derzeit entweder in den USA oder in der Europäischen Union vorhanden sind.

Sensible Daten können über das Fastly CDN-Server-Netzwerk übermittelt werden, werden jedoch nicht im Fastly-Netzwerk gespeichert. Alle in die Adobe Commerce Managed Services einbezogenen Partner, die vertragliche Verpflichtungen zur Gewährleistung des Schutzes sensibler Daten eingehen, sind verpflichtet. Managed Services verschiebt keine sensiblen Kunden- oder Verbraucherdaten von den vom Kunden angegebenen Speicherorten.

Als Teil der im Adobe Commerce Managed Services-Angebot enthaltenen Dienstleistungen benötigen Managed Services-Mitarbeiter Zugriff auf Produktionssysteme, die sensible Daten enthalten. Diese Mitarbeiter werden entsprechend ihrer Verpflichtung zum Schutz sensibler Kunden- und Verbraucherdaten geschult. Der Zugriff auf diese Systeme ist auf Mitarbeiter beschränkt, die Zugriff benötigen. Diese Mitarbeiter haben nur Zugriff auf die für die Erbringung dieser Dienstleistungen benötigte Zeit.

## Die Datenschutz-Grundverordnung (DSGVO)

Die DSGVO ist ein Rechtsrahmen, der Richtlinien für die Erhebung und Verarbeitung personenbezogener Daten für Einzelpersonen in der Europäischen Union (EU) festlegt. Diese Vorschriften gelten unabhängig davon, wo die Site ihren Sitz hat und EU-Besucher darauf zugreifen können.

Im Wesentlichen müssen Besucher über die Daten informiert werden, die die Site von ihnen erfasst, und sie müssen die Datenerfassung ausdrücklich akzeptieren. Sites müssen Besucher benachrichtigen, wenn personenbezogene Daten, die sich auf der Site befinden, verletzt werden.

Der Händler oder das Unternehmen, der bzw. das die Site betreibt, muss außerdem über einen speziellen Datenschutzbeauftragten verfügen, der die Datensicherheit der Site überwacht. Diese Person (oder dieses Website-Management-Team) sollte für den Fall, dass ein Besucher anfordert, ihre Daten zu löschen, zur Verfügung stehen.

Die DSGVO fordert außerdem, dass alle personenbezogenen Daten (wie Namen, Rasse und Geburtsdatum), die erhoben werden, entweder anonymisiert oder pseudonymisiert werden.

>[!NOTE]
>
> Diese Seite soll lediglich als allgemeine Übersicht darüber dienen, was die DSGVO betrifft. Weitere Informationen erhalten Sie von Ihrem Rechtsbeistand oder im[offiziellen Text](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Backups

In den letzten 24 Stunden werden stündlich Sicherungen durchgeführt. Nach Ablauf des Zeitraums von 24 Stunden werden Backups mithilfe des AWS EBS Snapshot-Dienstes nach folgendem Zeitplan aufbewahrt:

| Zeitraum | Richtlinie zur Sicherung der Aufbewahrung |
|----------------|-------------------------|
| Tage 1 bis 3 | Jedes Backup |
| Tage 4 bis 6 | Ein Backup pro Tag |
| Wochen 2 bis 6 | Ein Backup pro Woche |
| Wochen 8 bis 12 | Ein zweiwöchiges Backup |
| Wochen 12 bis 22 | Ein Backup pro Monat |

Dadurch wird ein unabhängiges Backup des redundanten Speichers erstellt. Da die EBS-Volumes verschlüsselt sind, werden die Backups ebenfalls verschlüsselt. Darüber hinaus führt Managed Services On-Demand-Backups auf Kundenwunsch durch.

Ihr Adobe Commerce Managed Services-Sicherungs- und Wiederherstellungsansatz verwendet eine hochverfügbare Architektur in Kombination mit Vollsystemsicherungen. Jedes Projekt wird - alle Daten, Code und Assets - über drei separate AWS-Verfügbarkeitszonen repliziert. jede Zone mit einem separaten Rechenzentrum.
