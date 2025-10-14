---
title: Funktionsweise  [!DNL Cloud Automation Patching Service (CAPS)]  Workflows
description: Erfahren Sie mehr über  [!DNL Cloud Automation Patching Service (CAPS)]  Workflow-Prozess, einschließlich Terminologie, Workflow-Phasen und Vorgänge für die automatisierte Patch-Verwaltung.
hide: true
hidefromtoc: true
source-git-commit: eff8c0ae9e1d9db6b46ba7cfbb915685ab5b194d
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 0%

---

# Funktionsweise des [!DNL Cloud Automation Patching Service (CAPS)]-Workflows

Dieses Thema bietet einen allgemeinen Überblick darüber, wie Patch-Vorgänge mithilfe von [!DNL CAPS (Cloud Automation Patching Service)] funktionieren.

## Terminologie

* **Vorgänge** - die wichtigsten von [!DNL CAPS] durchgeführten Aktionen:
   * Übernehmen
   * Zurück zur letzten Version
* **Phasen** - die drei Phasen des Workflows:
   * Vorprüfung
   * Flicken
   * Validierung
* **Umgebung** - die Adobe Commerce-Cloud-Umgebung, in der Patches angewendet werden.

## Vorgänge

[!DNL CAPS] unterstützt zwei *(Vorgänge* zum Verwalten von Patches in Ihrer Adobe Commerce Cloud-Umgebung:

* **Apply operation** - Fügt Ihrer Codebasis über einen sicheren, validierten Prozess Patch-Änderungen hinzu. Patches werden angewendet, indem Patch-Dateien im Ordner „m2-hotfixes“ abgelegt werden.

* **Wiederherstellungsvorgang** - Entfernt zuvor angewendete Patches aus Ihrer Codebasis, indem es Patch-Dateien aus dem Ordner „m2-hotfixes“ entfernt.

>[!IMPORTANT]
>
>Wiederherstellungsvorgänge sind nur für Patches verfügbar, die ursprünglich über [!DNL CAPS] angewendet wurden. Patches, die manuell oder über andere Methoden angewendet wurden, können mit diesem Service nicht rückgängig gemacht werden.

## Phasen

Der [!DNL CAPS]-Workflow verwendet drei *Phasen* die immer in dieser Reihenfolge ausgeführt werden, um sicherzustellen, dass Patches sicher und zuverlässig angewendet werden:

* **Vorprüfung** - Validiert die Patch-Kompatibilität und die Bereitschaft der Umgebung.
* **Patchen** - Wendet den Patch in einer Integrationsumgebung an oder setzt ihn zurück.
* **Validierung** - Validiert die Patch-Anwendung und führt Konsistenzprüfungen durch.

## Phasendetails

### Phase 1: Vorprüfung

Die Vorprüfungsphase überprüft, ob der Patch sicher auf Ihre Umgebung angewendet werden kann.

**Was passiert:**

* **Sicherungen der Produktionsumgebung** (nur Produktionsumgebungen):
   * Prüft, ob der Speicher im Wartungsmodus ist
   * Überprüft, ob Cron-Aufträge deaktiviert sind
   * Blockiert das Patchen, wenn die Bedingungen nicht erfüllt sind
   * Zeigt ein Bestätigungsdialogfeld an, wenn Bedingungen erfüllt sind
* **Patch-Validierung** - Überprüft, ob die Patch-Datei gültig und kompatibel ist
* **Umgebungsbewertung** - Überprüft die Bereitschaft und Ressourcen der Umgebung
* **Konflikterkennung** - Identifiziert potenzielle Konflikte mit vorhandenem Code
* **Abhängigkeitsprüfung** - Validiert die Kompatibilität der Adobe Commerce-Version

### Phase 2: Patchen

In der Patching-Phase wird der Patch zum Testen in einer temporären Integrationsumgebung angewendet oder zurückgesetzt. In dieser Phase erstellt [!DNL CAPS] eine temporäre Testumgebung, damit der Patch sicher angewendet und getestet werden kann, bevor Änderungen an der tatsächlichen Umgebung vorgenommen werden.

Dieser Ansatz bietet:

* **Sicherheit** - Behält Ihre Zielumgebung bis zur Validierung des Patches unberührt
* **Testen** - in einer realen Umgebung, bevor die Produktion beeinträchtigt wird
* **Rollback-Funktion** - wenn Probleme erkannt werden
* **Isolierung** - für jeden Patch-Vorgang

#### Phase 2a: Erstellung der Integrationsumgebung

**Verzweigungserstellung** - [!DNL CAPS] erstellt einen temporären Integrationsumgebungszweig mit dem Namen `{target-environment}-CAPS-{patch-id}`

**Umgebung einrichten** - Die Integrationsumgebung wird als untergeordnetes Element Ihrer Zielumgebung erstellt

**Code-**: Die Integrationsumgebung übernimmt den genauen Status Ihrer Zielumgebung

**Ressourcenanforderungen** - [!DNL CAPS] erstellt eine temporäre Umgebung mithilfe der Code-Basis Ihrer Zielumgebung. Gemäß der Dokumentation zu Adobe Commerce Cloud verfügt jede Umgebung (einschließlich Integrationsumgebungen) über eine separate Speicherzuweisung, die auf Ihrem vertraglich vereinbarten Speicherplan basiert. Die von Ihnen vertraglich vereinbarte Speichermenge entspricht dem Gesamtspeicher für jede Umgebung. In den meisten Fällen treten keine Probleme mit Ressourcenbeschränkungen auf. Wenn bei Ressourcenbeschränkungen ein Fehler auftritt, überprüfen Sie bitte die Größe Ihrer Anwendung und den vertraglich vereinbarten Speicher in Ihrem Plan.

#### Schritt 2b: Patchen der Anwendung in der Integrationsumgebung

**Sichere Tests** - Der Patch wird auf die Integrationsumgebung angewendet, nicht direkt auf Ihre Zielumgebung

**Dateiverwaltung** - Patch-Dateien werden im `m2-hotfixes/` Verzeichnis abgelegt

**Git-Vorgänge** - Änderungen werden übertragen und in den Zweig der Integrationsumgebung übertragen

**Umgebungsaktivierung** - Die Integrationsumgebung wird aktiviert, um den gepatchten Code bereitzustellen

#### Schritt 2c: Zurück zur Zielumgebung

**Umgebungs-Checkout** - [!DNL CAPS] checkt Ihre Zielumgebung lokal aus

**Zusammenführungsvorgang** - Der Zweig der Integrationsumgebung wird mit der Zielumgebung zusammengeführt

**Konfliktauflösung** - Wenn Konflikte auftreten, werden sie nach Möglichkeit automatisch aufgelöst

**Bereitstellung** - Die zusammengeführten Änderungen werden in Ihrer Zielumgebung bereitgestellt

**Überprüfung** - [!DNL CAPS] überprüft, ob die Zusammenführung erfolgreich war und die Umgebungen synchronisiert sind

**Umgebungsbereinigung** - Die temporäre Integrationsumgebung wird gelöscht, um Ressourcen freizugeben

## Lebenszyklus der Integrationsumgebung

Integrationsumgebungen haben während der Patching-Phase einen bestimmten Lebenszyklus:

* **Erstellung** - Wird zu Beginn der Patch-Phase erstellt
* **Aktiver Zeitraum** - Während der Patch-Anwendung und der Tests aktiv bleiben
* **Bereinigung** - Wird nach erfolgreicher Zusammenführung oder bei Fehlschlagen des Vorgangs automatisch gelöscht

### Phase 3: Validierung

Die Validierungsphase stellt sicher, dass die gepatchte Anwendung ordnungsgemäß funktioniert und Konsistenzprüfungen durchführt.

**Was passiert:**

* **Konsistenzprüfung der Anwendung** - Überprüft, ob die Anwendung ordnungsgemäß gestartet und ausgeführt wird
* **Bereinigung** - Entfernt die temporäre Umgebung, aktualisiert Protokolle und benachrichtigt Sie über den Abschluss

## Erfolgsindikatoren

**Vorgang anwenden:**

* „Auftrag erfolgreich abgeschlossen“ - Patch ohne Probleme angewendet
* „Patch wurde angewendet“ - Patch war bereits vorhanden (keine Aktion erforderlich)
* Patch-Datei erfolgreich im Ordner „m2-hotfixes“ abgelegt
* Alle Validierungsprüfungen erfolgreich
* Konsistenzprüfungen der Anwendung erfolgreich

**Wiederherstellungsvorgang:**

* „Auftrag erfolgreich abgeschlossen“ - Patch ohne Probleme zurückgesetzt
* „Patch wurde zurückgesetzt“ - Patch wurde bereits zurückgesetzt (keine Aktion erforderlich)
* Patch-Datei erfolgreich aus dem Ordner „m2-hotfixes“ entfernt
* Alle Validierungsprüfungen erfolgreich
* Konsistenzprüfungen der Anwendung erfolgreich

## Sicherheitsmaßnahmen für die Produktionsumgebung

[!DNL CAPS] umfasst spezielle Sicherheitsmaßnahmen für Produktionsumgebungen, um unbeabsichtigte Unterbrechungen zu verhindern und sicherzustellen, dass Patches vorab sicher validiert werden.

### Voraussetzungen für Produktions-Patches

Bevor Patches auf Produktionsumgebungen angewendet werden, prüft [!DNL CAPS] zwei kritische Bedingungen:

* **Wartungsmodus** - Der Speicher muss sich im Wartungsmodus befinden
* **Cron-Aufträge deaktiviert** - Cron-Aufträge müssen deaktiviert werden

Wenn eine der Bedingungen nicht erfüllt ist, wird die Patch-Anwendung blockiert und der Benutzer wird benachrichtigt.

## Verwandte Themen

* [Einführung von CAPS](intro.md)
* [Zugriff](access.md)
* [Best Practices](best-practices.md)
* [Fehlerbehebung](troubleshooting.md)
