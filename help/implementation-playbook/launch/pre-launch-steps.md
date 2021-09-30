---
title: Schritte vor dem Start
description: Verwenden Sie unsere Checklisten vor dem Start, um eine reibungslose Implementierung der Commerce-Site in Adobe sicherzustellen.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Schritte vor dem Start

Wenn Sie die Bereitstellung und Tests in den Staging-Umgebungen abgeschlossen haben, können Sie mit der Vorbereitung des Site-Starts beginnen. Staging ist eine nahezu produktionsorientierte Umgebung, die auf ähnlicher Hardware, Konfigurationen, Architektur und Diensten ausgeführt wird. Dadurch können Sie Ihre Ausfallzeiten reduzieren und Ihre Erweiterung, Ihren Dienst, Ihre benutzerdefinierten Konfigurationen und die Tests der Benutzerakzeptanz für Händler zu wichtigen Komponenten für die Freigabe Ihrer Sites und Stores machen.

Die Checkliste vor dem Start muss vor dem Start überprüft werden. Sie enthält die folgenden wichtigen Überprüfungen:

- Code-Einfrieren für Bereitstellung
- Stellen Sie sicher, dass die Ausfallzeit bis mindestens einen Tag vor dem Maintenance Release und bis zu einer Woche vor dem ersten Start kommuniziert wurde.
- Bereitstellungsskripten werden vollständig für Produktions-/Staging-/Integrationsumgebungen eingerichtet/konfiguriert
- Datenbanken sind zwischen Staging- und Produktionsumgebungen alle eingerichtet und identisch
- SSL-Zertifikate (TLS) werden für Staging-/Produktionsumgebungen validiert
- E-Mail-Dienste sind gut konfiguriert und funktionieren für Transaktions-E-Mails
- CDN ist für Staging-/Produktionsumgebungen konfiguriert
- Sicherheitssuche für Staging-/Produktionsumgebungen einrichten
   - Adobe Commerce-Sicherheitsprüfung
- Führen Sie eine Leistungsbewertung durch
   - JMeter
   - Belagung
   - Webseitentest
   - Google-Seitengeschwindigkeit
- Validieren Sie alle Drittanbieterintegrationen, die in der Anwendung funktionieren (OMS, CRM).
- Leistungsüberwachungs-Tool aktivieren (Neue Eigenschaften)
- Aktivitäten zur Datenmigration in der Probe (falls vorhanden)

![Abbildung der Phase 1 des Startvorgangs](../../assets/playbooks/launch-steps-1.svg)

Die Hauptunterschiede zwischen lokalen Adobe Commerce- und Cloud-Implementierungen sind die Bereitstellungsskripte und -werkzeuge sowie die Einrichtung für SSL, Mail-Dienst und CDN. Der Prozess ist jedoch immer noch derselbe.

Für das SSL-(TLS-)Zertifikat stellt Adobe Commerce in der Cloud-Infrastruktur ein Fastly-Platzhalterzertifikat bereit. Um sie verwenden zu können, müssen Sie die Validierung bestehen: Fügen Sie den Fastly TXT-Eintrag in Ihre DNS-Einstellungen zum apex-Domänennamen hinzu. Der Fastly TXT-Eintrag befindet sich im On-boarding-Arbeitsblatt. Andernfalls müssen Sie ein Ticket senden, um es zu erhalten. Ersetzen Sie diesen Text durch Ihre Fragen/Kommentare hier. Wenn Sie Ihr eigenes SSL(TLS)-Zertifikat anstelle eines Wildcard-Zertifikats verwenden, senden Sie ein Supportticket mit Ihrem Zertifikat, das an das Setup angehängt ist.

Adobe Commerce in der Cloud-Infrastruktur bietet die Funktion SendGrid Mail für Ihre Transaktions-E-Mails. Für Pro-Pläne müssen Sie Ihren DNS-Einstellungen SendGrid-Einträge hinzufügen. SendGrid-Datensätze finden Sie im On-Boarding-Arbeitsblatt. Andernfalls sollten SI oder Händler Support-Tickets einreichen, um sie zu erhalten. Zunächst müssen Sie keine Änderungen am DNS vornehmen. SendGrid ist für Sie vorkonfiguriert.

## Checkliste vor dem Start abschließen

Die vollständige Checkliste vor dem Start zeigt alle wichtigen Aktivitäten an, deren Vollständigkeit für den Wechsel zum Launch-Status erforderlich ist.

- Aktualisierte Pläne zur Risikominderung für das aktive Risiko
- Richtige Domänennamen angegeben
- Ausgehende E-Mails wurden getestet
- SSL-Zertifikat wird bereitgestellt und konfiguriert
- Die wichtige Konfiguration der Adobe Commerce-Anwendung wird korrekt aktualisiert
- Basis-URLs und Basis-Admin-URLs sind korrekt auf den endgültigen Hostnamen eingestellt
- Admin-Passwörter werden geändert
- Alle Benutzer mit Zugriff auf die Anwendung, die keinen Zugriff mehr benötigen, werden entfernt
- Zahlungskonfiguration für die Produktionsumgebung (für einige Kunden verwendet die Zahlung zum Testen den Sandbox-Modus)
- Testdaten (Kunde, Wunschliste, Überprüfungen, Bestellungen und zugehörige Daten) aus der Produktionsdatenbank werden gelöscht.

![Abbildung der Phase 2 des Startvorgangs](../../assets/playbooks/launch-steps-2.svg)
