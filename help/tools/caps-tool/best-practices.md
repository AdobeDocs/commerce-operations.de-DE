---
title: Handbuch zu Best Practices für [!DNL Cloud Automation Patching Service (CAPS)]
description: Best Practices für die  [!DNL Cloud Automation Patching Service (CAPS)]  und sichere Verwendung
hide: true
hidefromtoc: true
source-git-commit: 9d377babd1059d7ec0af687755965ca4d0b541fb
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 0%

---

# Handbuch zu Best Practices für [!DNL Cloud Automation Patching Service (CAPS)]

Die Befolgung von Best Practices ist für erfolgreiche und sichere Patch-Vorgänge mit [!DNL Cloud Automation Patching Service] ([!DNL CAPS]) unerlässlich. Dieses Handbuch enthält umfassende Best Practices für effektive Patch-Vorgänge, Umgebungs-Management und hervorragende Betriebsabläufe.

## Best Practices für die Vorabinstallation von Patches

### Vorbereitung der Umgebung

**Best Practice:** Bereiten Sie Ihre Umgebung sorgfältig vor, bevor Sie Patches anwenden, um einen erfolgreichen Betrieb zu gewährleisten und Risiken zu minimieren.

Bevor Sie Patches anwenden, stellen Sie sicher, dass Ihre Umgebung ordnungsgemäß vorbereitet ist:

* **Adobe Commerce Cloud-Konto**
   * Aktives Adobe Commerce Cloud-Abonnement
   * Gültige Adobe Commerce-Lizenz
   * Repository-Zugriffsberechtigungen konfiguriert
   * Projekt- und Umgebungsberechtigungen

* **Umgebungsressourcen**
   * Verfügbare Umgebungssteckplätze für temporäre Tests
   * Ausreichende Speicher-, CPU- und Speicherressourcen
   * Netzwerkzugriff auf Adobe-Repositorys
   * Stabile übergeordnete Umgebung für die Synchronisierung

* **Vorbereitung der Produktionsumgebung** (für Produktions-Patching)
   * Wartungsmodus kann aktiviert werden
   * Cron-Aufträge können deaktiviert werden
   * Verfahren für Wartungsfenster eingerichtet
   * Dokumentierte Rollback-Verfahren
   * Kommunikationsplan für Stakeholder fertig

## Best Practices für Patches

### Zeitplanung

**Best Practice:** Sie Patch-Vorgänge in Zeiten geringen Traffics und in Abstimmung mit Stakeholdern, um geschäftliche Auswirkungen zu minimieren.

**Wählen Sie den richtigen Zeitpunkt für die Patch-Anwendung:**

* **Zeiträume mit geringem Traffic**
   * Planen von Patches außerhalb der Spitzenzeiten
   * Vermeiden Sie das Anwenden von Patches bei Ereignissen mit hohem Traffic
   * Planen Sie mögliche Ausfallzeiten während der Validierung ein.

* **Überlegungen zur Produktionsumgebung**
   * **Wartungsfenster** - Planen von Produktions-Patches während geplanter Wartungsfenster
   * **Kundenkommunikation**: Kunden über den Wartungsmodus und erwartete Ausfallzeiten informieren
   * **Team-**: Stellen Sie sicher, dass alle Team-Mitglieder den Wartungsplan kennen.
   * **Rollback-Vorbereitung** - Teammitglieder für sofortiges Rollback verfügbar haben, falls erforderlich

### Überwachung und Validierung

**Bei Patch-Vorgängen:**

* **Überwachen des Fortschritts**
   * Überwachen des Betriebsstatus in Echtzeit
   * Achten Sie auf etwaige Warnungen oder Fehler
   * Unterbrechen Sie den Vorgang nach dem Start nicht

* **Ergebnisse validieren**
   * Testen der kritischen Funktionalität nach erfolgreicher Anwendung
   * Überprüfen Sie die Leistungsmetriken auf mögliche Beeinträchtigungen.
   * Überprüfen, ob die Sicherheitsmaßnahmen intakt bleiben

## Best Practices für Post-Patch

### Überprüfung und Tests

**Best Practice:** Überprüfen Sie den Erfolg von Patch-Anwendungen durch umfassende Tests und Überwachung, um die Systemstabilität und -funktionalität sicherzustellen.

**Nach erfolgreicher Patch-Anwendung:**

* **Funktionstests**
   * Testen aller wichtigen Geschäftsprozesse
   * Checkout- und Zahlungsflüsse überprüfen
   * Überprüfen der Funktionalität des Admin-Bedienfelds

* **Leistungsüberwachung**
   * Überwachen der Seitenladezeiten
   * Überprüfen der Datenbankleistung
   * Auf Ressourcennutzungsspitzen achten

* **Sicherheitsüberprüfung**
   * Überprüfen, ob die Sicherheitsfunktionen funktionieren
   * Auf neue Sicherheitslücken prüfen
   * Testauthentifizierung und -autorisierung

## Best Practices für die Produktionsumgebung

### Vorab-Produktionstests

**Best Practice:** Sie Patches niemals direkt in der Produktion an, ohne gründliche Tests in Vorproduktionsumgebungen durchzuführen, die die Produktionskonfiguration widerspiegeln.

**Patches sollten immer vor der Produktionsbereitstellung getestet werden:**

* **Einrichtung der Testumgebung**
   * Verwenden von Staging- oder Integrationsumgebungen für Tests
   * Sicherstellen, dass die Testumgebung die Produktionskonfiguration widerspiegelt
   * Testen Sie nach Möglichkeit mit produktionsähnlichen Daten

* **Umfassende Tests**
   * Testen aller wichtigen Geschäftsprozesse
   * Checkout- und Zahlungsflüsse überprüfen
   * Überprüfen der Funktionalität des Admin-Bedienfelds
   * Testen von benutzerdefinierten Integrationen

* **Leistungstests**
   * Auswirkungen von Patches auf die Leistung überwachen
   * Überprüfen auf Leistungseinbußen
   * Überprüfen, ob die Ressourcennutzung akzeptabel bleibt

### Risikominderung

**Risiken beim Produktions-Patching minimieren:**

* **Kommunikationsplan**
   * Kunden über Wartungsfenster benachrichtigen
   * Halten Sie die Interessenträger über die Fortschritte auf dem Laufenden
   * Eskalationsverfahren bereit halten

* **Rollback-Strategie**
   * Wissen, wie Patches bei Bedarf schnell zurückgesetzt werden können
   * Teammitglieder für sofortige Reaktion verfügbar haben
   * Verfahren zum Zurücksetzen von Dokumenten

* **Überwachung und Warnhinweise**
   * Einrichten der Überwachung für Probleme nach dem Patch
   * Benachrichtigung bei kritischen Fehlern
   * Leistungsmetriken genau überwachen

## Zusammenfassung der wichtigsten Best Practices

### Wichtige Best Practices für [!DNL CAPS] Erfolg

* Immer in der Vorproduktion testen, bevor Patches auf Produktionsumgebungen angewendet werden
* Wartungsmodus aktivieren und Cron-Aufträge für Produktions-Patch-Vorgänge deaktivieren
* Überwachung der Abläufe und Vorbereitung der Rollback-Verfahren
* Alle Patch-Vorgänge dokumentieren und umfassende Aufzeichnungen führen
* Befolgen Sie die entsprechenden Verfahren für das Änderungsmanagement und erhalten Sie entsprechende Genehmigungen.
* Umgebungen synchronisiert halten und eine ordnungsgemäße Ressourcenzuordnung gewährleisten
* Festlegen klarer Support-Verfahren und Aufrechterhaltung der Teamschulung
* Überprüfen und verbessern Sie Ihre Patch-Verwaltungsprozesse regelmäßig

## Verwandte Themen

* [Einführung von CAPS](intro.md)
* [Zugriff](access.md)
* [Workflow](workflow.md)
* [Fehlerbehebung](troubleshooting.md)
