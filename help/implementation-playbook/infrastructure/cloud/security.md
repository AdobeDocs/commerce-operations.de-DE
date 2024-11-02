---
title: Sicherheit der Cloud-Infrastruktur
description: Erfahren Sie, wie Adobe Adobe Commerce in der Cloud-Infrastruktur sicher hält.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
feature: Cloud, Security
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1691'
ht-degree: 0%

---


# Sicherheit

Die Adobe Commerce [Pro-Planarchitektur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) ist für eine äußerst sichere Umgebung ausgelegt. Jeder Kunde wird in einer eigenen isolierten Serverumgebung bereitgestellt, die von anderen Kunden getrennt ist. Die Sicherheitsdetails der Produktionsumgebung werden nachfolgend beschrieben.

## Webbrowser

Der Großteil des in die Cloud-Umgebung eingehenden und aus ihr ausgehenden Traffics stammt aus den Webbrowsern der Verbraucher. Der Kundentraffic kann mit HTTPS für alle Seiten auf der Website gesichert werden (entweder mithilfe eines gemeinsam genutzten SSL-Zertifikats oder des eigenen SSL-Zertifikats des Kunden gegen eine zusätzliche Gebühr). Checkout- und Kontoseiten werden immer über HTTPS bereitgestellt. Die Best Practice ist, alle Seiten unter HTTPS bereitzustellen.

## Netzwerk zur Inhaltsbereitstellung

Fastly bietet einen CDN-Schutz (Content Delivery Network) und verteilte Denial of Service (DDoS). Das Fastly CDN hilft, den direkten Zugriff auf die Herkunftsserver zu isolieren. Das öffentliche DNS verweist nur auf das Fastly Network. Die Fastly DDoS-Lösung schützt vor hochgradig störenden Angriffen auf Layer 3 und Layer 4 sowie komplexeren Angriffen auf Layer 7. Layer-7-Angriffe können mithilfe benutzerdefinierter Regeln blockiert werden, die auf den gesamten HTTP/HTTPS-Anforderungen basieren und auf Client- und Anforderungskriterien basieren, einschließlich Kopfzeilen, Cookies, Anfragepfad und Client-IP, oder Indikatoren wie Geolocation.

Siehe [Übersicht über schnelle Dienste](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html) im _Cloud-Handbuch_.

## Web-Anwendungs-Firewall

Die Fastly Web Application Firewall (WAF) wird verwendet, um zusätzlichen Schutz zu bieten. Die Cloud-basierte WAF von Fastly verwendet Drittanbieterregeln aus kommerziellen und Open-Source-Quellen wie dem OWASP Core Ruleset. Darüber hinaus werden Adobe Commerce-spezifische Regeln angewendet. Die Kunden sind vor wichtigen Angriffen auf Anwendungsebene geschützt, darunter Injizierungsangriffe und schädliche Eingaben, Cross-Site-Scripting, Datenexfiltration, HTTP-Protokollverletzungen und anderen OWASP Top-10-Bedrohungen.

Die WAF-Regeln werden von Adobe Commerce aktualisiert, wenn neue Schwachstellen erkannt werden, die es Managed Services ermöglichen, Sicherheitsprobleme vor Softwarepatches zu &quot;virtuell zu patchen&quot;. Der Fastly WAF bietet keine Dienste zur Ratenbegrenzung oder Bot-Erkennung. Bei Bedarf können Kunden einen Drittanbieter-Bot-Erkennungsdienst lizenzieren, der mit Fastly kompatibel ist.

Siehe [Web Application Firewall (WAF)](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service.html) im _Cloud-Handbuch_.

## Virtual Private Cloud

Die Adobe Commerce Pro-Planproduktionsumgebung ist als Virtual Private Cloud (VPC) konfiguriert, sodass Produktionsserver isoliert sind und nur über eingeschränkte Möglichkeiten zur Verbindung mit und aus der Cloud-Umgebung verfügen. Nur sichere Verbindungen zu den Cloud-Servern sind zulässig. Für Dateiübertragungen können sichere Protokolle wie SFTP oder rsync verwendet werden.

Kunden können SSH-Tunnel verwenden, um die Kommunikation mit der Anwendung zu sichern. Der Zugriff auf AWS PrivateLink ist gegen eine zusätzliche Gebühr möglich. Alle Verbindungen zu diesen Servern werden über AWS Security Groups gesteuert, eine virtuelle Firewall, die Verbindungen zur Umgebung einschränkt. Die technischen Ressourcen der Kunden können über SSH auf diese Server zugreifen.

## Verschlüsselung

Amazon Elastic Block Store (EBS) wird für die Speicherung verwendet. Alle EBS-Volumes werden mit dem AES-256-Algorithmus verschlüsselt, was bedeutet, dass die Daten im Ruhezustand verschlüsselt werden. Das System verschlüsselt auch Daten während der Übertragung zwischen dem CDN und dem Herkunftsserver sowie zwischen den Herkunftsservern. Kundenkennwörter werden als Hashes gespeichert. Vertrauliche Zugangsdaten, einschließlich Zahlungsdaten-Gateway-Anmeldeinformationen, werden mit dem SHA-256-Algorithmus verschlüsselt.

Die Adobe Commerce-Anwendung unterstützt keine Verschlüsselung oder Verschlüsselung auf Spalten- oder Zeilenebene, wenn sich die Daten nicht im Ruhezustand befinden oder sich nicht im Durchlauf zwischen Servern befinden. Der Kunde kann Verschlüsselungsschlüssel innerhalb der Anwendung verwalten. Die vom System verwendeten Schlüssel werden im Schlüsselverwaltungssystem von AWS gespeichert und müssen von Managed Services verwaltet werden, um Teile des Dienstes bereitzustellen.

## Endpunkterkennung und -antwort

[!DNL CrowdStrike Falcon], ein leichtgewichtiger Agent der nächsten Generation der Endpunkterkennung und -antwort (EDR) wird auf allen Endpunkten (einschließlich Servern) innerhalb von Adobe installiert. EDR-Agenten schützen Adobe-Daten und -Systeme mit kontinuierlicher Echtzeit-Überwachung und -Erfassung, was eine schnelle Ermittlung und Reaktion von Bedrohungen ermöglicht.

## Penetrationstests

Managed Services führt regelmäßige Penetrationstests für das Adobe Commerce-Cloud-System mit der nativen Anwendung durch. Kunden sind für alle Penetrationstests ihrer angepassten Anwendung verantwortlich.

## Zahlungseingang

Adobe Commerce erfordert Payment Gateway-Integrationen, bei denen Kreditkartendaten direkt vom Browser des Verbrauchers an das Payment Gateway weitergeleitet werden. Die Kartendaten sind in keiner der Adobe Commerce Pro Plan Managed Services-Umgebungen verfügbar. Aktionen, die die Transaktionen der E-Commerce-Anwendung betreffen, werden mithilfe eines Verweises auf die Transaktion vom Gateway ausgeführt.

## Adobe Commerce-Anwendung

Adobe testet regelmäßig den Kernanwendungscode auf Sicherheitslücken. Patches für Mängel und Sicherheitsprobleme werden den Kunden zur Verfügung gestellt. Das Produktsicherheitsteam validiert Adobe Commerce-Produkte gemäß den Sicherheitsrichtlinien der OWASP-Anwendung. Zur Prüfung und Überprüfung der Einhaltung werden verschiedene Tools zur Bewertung von Sicherheitslücken und externe Anbieter verwendet. Zu den Sicherheitstools gehören:

- Statische und dynamische Veracode-Prüfung
- Quellcode-Scannen von RIPS
- Sicherheitsüberprüfungsdienste von Trustwave und Alert Logic
- Burp Suite Pro
- OWASPZAP
- undSqlMap

Die vollständige Codebasis wird mit diesen Tools alle zwei Wochen überprüft. Kunden werden durch direkte E-Mails, Benachrichtigungen in der Anwendung und im [Sicherheitscenter](https://helpx.adobe.com/security.html) über Sicherheits-Patches benachrichtigt.

Kunden müssen sicherstellen, dass diese Patches gemäß den PCI-Richtlinien innerhalb von 30 Tagen nach ihrer Veröffentlichung auf ihre benutzerdefinierte Anwendung angewendet werden. Adobe bietet außerdem ein [Sicherheits-Scan-Tool](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan), mit dem Händler ihre Websites regelmäßig überwachen und Updates zu bekannten Sicherheitsrisiken, Malware und unbefugtem Zugriff erhalten können. Das Security Scan Tool ist ein kostenloser Service und kann auf jeder beliebigen Version von Adobe Commerce ausgeführt werden.

Um Sicherheitsforscher dazu zu ermutigen, Schwachstellen zu identifizieren und zu melden, verfügt Adobe Commerce zusätzlich zu internen Tests über ein [Bugbounty-Programm](https://hackerone.com/magento) . Darüber hinaus erhält der Kunde bei Bedarf den vollständigen Quellcode der Anwendung für seine eigene Überprüfung.

## Schreibgeschütztes Dateisystem

Der gesamte ausführbare Code wird in einem schreibgeschützten Dateisystembild bereitgestellt, wodurch die für Angriffe verfügbaren Oberflächen erheblich reduziert werden. Der Bereitstellungsprozess erstellt ein Squash-FS-Bild, um die Möglichkeiten für das Einfügen von PHP- oder JavaScript-Code in das System zu reduzieren oder die Adobe Commerce-Anwendungsdateien zu ändern.

## Remote-Implementierung

Die einzige Möglichkeit, ausführbaren Code in die Managed Services-Produktionsumgebung zu übertragen, besteht darin, ihn über einen Bereitstellungsprozess auszuführen. Bei der Bereitstellung wird Quellcode aus dem Quell-Repository in ein Remote-Repository gepusht, das einen Bereitstellungsprozess initiiert. Der Zugriff auf dieses Bereitstellungsziel wird gesteuert, sodass Sie die vollständige Kontrolle darüber haben, wer auf das Bereitstellungsziel zugreifen kann. Alle Implementierungen von Anwendungs-Code in der Nicht-Produktionsumgebung werden vom Kunden gesteuert.

## Protokollierung

Alle AWS-Aktivitäten werden in AWS CloudTrail protokolliert. Die Protokolle für Betriebssystem, Anwendungsserver und Datenbank werden auf den Produktionsservern gespeichert und in Backups gespeichert. Alle Quellcodeänderungen werden in einem Git-Repository aufgezeichnet. Der Bereitstellungsverlauf ist in der Adobe Commerce-[Projekt-Webschnittstelle](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/overview) verfügbar. Der gesamte Support-Zugriff wird protokolliert und Support-Sitzungen werden aufgezeichnet.

Siehe [Anzeigen und Verwalten von Protokollen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html) im _Cloud-Handbuch_.

## Sensible Daten

Vertrauliche Daten können entweder personenbezogene Daten von Verbrauchern oder vertrauliche Daten von Managed Services-Kunden umfassen. Der Schutz sensibler Kunden- und Verbraucherdaten ist eine wichtige Verpflichtung für Adobe Commerce Managed Services. Sowohl Managed Services- als auch Adobe-Kunden haben rechtliche Verpflichtungen in Bezug auf personenbezogene Daten. Zusätzlich zu den Sicherheitsfunktionen der Architektur gibt es weitere Steuerelemente, um die Verteilung und den Zugriff auf vertrauliche Daten zu beschränken.

Kunden besitzen ihre Daten und haben die Kontrolle darüber, wo sich diese Daten befinden. Der Kunde gibt den Speicherort an, an dem sich seine Produktions- und Entwicklungsinstanzen befinden. Sie geben außerdem an, welcher Speicherort für die Adobe Commerce-Reporting-Umgebung mit Commerce verwendet wird und ob diese Adobe Commerce-Berichtsanwendung Zugriff auf persönlich identifizierbare Informationen hat. Produktionsinstanzen können in den meisten AWS-Regionen auftreten, während Entwicklungs- und Adobe Commerce-Reporting-Umgebungen derzeit entweder in den USA oder in der Europäischen Union zu finden sind.

Sensible Daten können über das Fastly CDN-Server-Netzwerk übermittelt werden, werden jedoch nicht im Fastly-Netzwerk gespeichert. Alle in die Managed Services einbezogenen Partner, die ein Angebot anbieten, haben vertragliche Verpflichtungen, den Schutz sensibler Daten sicherzustellen. Managed Services verschiebt keine sensiblen Kunden- oder Verbraucherdaten von den vom Kunden angegebenen Speicherorten.

Als Teil der im Managed Services-Angebot enthaltenen Dienstleistungen benötigen Managed Services-Mitarbeiter Zugriff auf Produktionssysteme, die sensible Daten enthalten. Diese Mitarbeiter werden entsprechend ihrer Verpflichtung zum Schutz sensibler Kunden- und Verbraucherdaten geschult. Der Zugriff auf diese Systeme ist auf Mitarbeiter beschränkt, die Zugriff benötigen. Diese Mitarbeiter haben nur Zugriff auf die für die Erbringung dieser Dienstleistungen benötigte Zeit.

## Die Datenschutz-Grundverordnung

Die Datenschutz-Grundverordnung (DSGVO) ist ein Rechtsrahmen, der Richtlinien für die Erhebung und Verarbeitung personenbezogener Daten für Einzelpersonen in der Europäischen Union (EU) festlegt. Diese Vorschriften gelten unabhängig davon, wo die Site ihren Sitz hat und EU-Besucher darauf zugreifen können.

Besucher müssen über die Daten informiert werden, die von einer Site erfasst werden, und sie müssen sich ausdrücklich mit der Datenerfassung einverstanden erklären. Sites müssen Besucher benachrichtigen, wenn personenbezogene Daten, die sich auf der Site befinden, verletzt werden.

Der Händler oder das Unternehmen, der bzw. das die Site betreibt, muss über einen speziellen Datenschutzbeauftragten verfügen, der die Datensicherheit der Site überwacht. Der Datenschutzbeauftragte (oder das Website-Management-Team) sollte kontaktiert werden können, wenn ein Besucher die Löschung seiner Daten anfordert.

Die DSGVO fordert, dass alle personenbezogenen Daten (wie Namen, Rasse und Geburtsdatum), die erfasst werden, entweder anonymisiert oder pseudonymisiert werden.

>[!NOTE]
>
>Diese Seite bietet einen allgemeinen Überblick darüber, was für die DSGVO zu beachten ist. Weitere Informationen zum Speichern personenbezogener Daten in Adobe Commerce finden Sie im _[Sicherheits- und Compliance-Handbuch](../../../security-and-compliance/privacy/gdpr.md)_ . Um festzustellen, wie Ihr Unternehmen rechtliche Verpflichtungen einhalten sollte, wenden Sie sich an Ihren Rechtsbeistand oder lesen Sie den [offiziellen Text](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Backups

In den letzten 24 Stunden werden stündlich Sicherungen durchgeführt. Nach Ablauf des Zeitraums von 24 Stunden werden Backups mithilfe des AWS EBS Snapshot-Dienstes planmäßig aufbewahrt. Siehe [Bindungsrichtlinie](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#retention-policy) im _Cloud-Handbuch_.

Der Dienst erstellt eine unabhängige Sicherung auf redundanten Speicher. Da die EBS-Volumes verschlüsselt sind, werden die Backups ebenfalls verschlüsselt. Darüber hinaus führt Managed Services On-Demand-Backups auf Kundenwunsch durch.

Ihr Sicherungs- und Wiederherstellungsansatz von Managed Services verwendet eine hochverfügbare Architektur in Kombination mit Vollsystemsicherungen. Jedes Projekt - alle Daten, Code und Assets - wird über drei separate AWS-Verfügbarkeitszonen repliziert, wobei jeder Bereich über ein eigenes Rechenzentrum verfügt.

Siehe [Snapshots und Backup-Verwaltung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/storage/snapshots.html) im _Cloud-Handbuch_.
