---
title: Handbuch zur Fehlerbehebung [!DNL Cloud Automation Patching Service (CAPS)]
description: Beheben häufiger Probleme und Fehlermeldungen in [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---

# Handbuch zur Fehlerbehebung [!DNL Cloud Automation Patching Service (CAPS)]

Wenn Sie [!DNL CAPS] für Patch-Vorgänge verwenden, können Fehlermeldungen und Probleme auftreten, die eine erfolgreiche Patch-Anwendung oder eine Rückgängigmachung verhindern können. Dieses Handbuch bietet Lösungen für die häufigsten Probleme.

## Schritte zur schnellen Fehlerbehebung

### Wenn der Patch-Vorgang fehlschlägt

* Überprüfen Sie den Betriebsstatus, um zu verstehen, welche Phase fehlgeschlagen ist
* Überprüfen von Fehlermeldungen auf bestimmte Fehlerursachen
* Technische Details in den Fehlerprotokollen
* Befolgen Sie die in diesem Handbuch bereitgestellten Lösungen

### Dauer von Patch-Vorgängen

Für die meisten Umgebungen wird in der folgenden Zeitleiste beschrieben, wie lange Patch-Vorgänge dauern sollten. Je nach Größe und Komplexität der Umgebung kann dies jedoch länger dauern:

* **Vorab-Bearbeitung:** 2-5 Minuten
* **Patchen:** 5-15 Minuten
* **Nachbearbeitung:** 10-40 Minuten
* **Gesamt:** 15-60 Minuten

### Abbrechen eines laufenden Patches

>[!WARNING]
>
>Sobald ein Patch-Vorgang beginnt, sollte er abgeschlossen sein. Das System umfasst Bereinigungsverfahren, die auch bei fehlgeschlagenen Vorgängen ausgeführt werden. Wenn Sie den Prozess unterbrechen, kann sich Ihre Umgebung in einem inkonsistenten Zustand befinden.

## Häufige Erfolgsmeldungen

* **„Auftrag erfolgreich abgeschlossen“** - Der Patch wurde ohne Probleme erfolgreich angewendet/zurückgesetzt.

* **„Patch wurde angewendet“** - Sie versuchen, einen Patch anzuwenden, der bereits angewendet wurde. Das System hat erkannt, dass der Patch bereits in Ihrer Umgebung vorhanden ist. Es sind keine Maßnahmen erforderlich.

* **„Patch wurde zurückgesetzt“** - Sie versuchen, einen Patch rückgängig zu machen, der bereits rückgängig gemacht wurde. Das System hat erkannt, dass der Patch derzeit nicht angewendet wird. Es sind keine Maßnahmen erforderlich.

## Häufige Fehlermeldungen und Lösungen

### Patchen von Anwendungsfehlern

#### „Der Patch kann nicht angewendet werden, da [!DNL CAPS] diese Probleme mit Ihrer Codebasis oder der Patch-Datei erkannt hat.“

**Wenn er auftritt:** Während der Vorprüfung

**Ursache:** Der Patch steht in Konflikt mit Ihrer aktuellen Codebasis ODER es gibt ein Problem mit dem Patch selbst

**Lösungen:**

* Überprüfen Sie die bereitgestellten detaillierten Fehlerprotokolle, um festzustellen, ob es sich um eine Code-Basis oder ein Patch-Problem handelt
* Überprüfen auf widersprüchliche Anpassungen im Code
* Überprüfen Sie, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist.
* Erwägen Sie, Konflikte manuell zu lösen, oder wenden Sie sich an den Support

#### „Dieser Patch wurde von [!DNL CAPS] nicht verwaltet. Cannot revert“

**Wenn er auftritt:** Während des Wiederherstellungsvorgangs

**Ursache:** Sie versuchen, einen Patch rückgängig zu machen, der nicht über [!DNL CAPS] angewendet wurde

**Lösung:** Verwenden Sie dieselbe Methode, die ursprünglich zum Anwenden des Patches verwendet wurde, oder wenden Sie sich an den Support, um Hilfe zu erhalten

### Umgebung und Validierungsfehler

#### „Umgebung ist nicht mit übergeordneter Umgebung synchronisiert“

**Wenn dies auftritt:** Während der Validierung

**Ursache:** Ihre Integrationsumgebung unterscheidet sich von der übergeordneten Umgebung

**Lösungen:**

* Synchronisieren Sie Ihre Umgebung mit der übergeordneten Verzweigung
* Patch-Vorgang wiederholen
* Wenden Sie sich an den Support, wenn Synchronisierungsprobleme weiterhin bestehen

#### „Schutzmechanismen in der Produktionsumgebung werden nicht eingehalten“

**Wenn es auftritt:** Während der Vorprüfung für Produktionsumgebungen

**Ursache:** Die Produktionsumgebung erfüllt nicht die erforderlichen Sicherheitsbedingungen

**Lösungen:**

* Aktivieren des Wartungsmodus für den Produktionsspeicher
* Deaktivieren von Cron-Aufträgen in der Produktionsumgebung
* Überprüfen Sie, ob beide Bedingungen erfüllt sind, bevor Sie es erneut versuchen

>[!IMPORTANT]
>
> [!DNL CAPS] aktiviert nicht automatisch den Wartungsmodus oder deaktiviert Cron-Aufträge - diese müssen extern von Ihnen erledigt werden

#### „Patch wurde angewendet, aber Konsistenzprüfung fehlgeschlagen. Bitte überlegen Sie, ob Sie dies rückgängig machen sollten“

**Wenn dies auftritt:** Nach der Patch-Anwendung während der Validierung

**Ursache:** Der Patch wurde erfolgreich angewendet, aber die Konsistenzprüfungen sind fehlgeschlagen

**Lösungen:**

* Überprüfen der Anwendungsprotokolle auf bestimmte Fehler
* Kritische Funktionen manuell testen
* Erwägen, den Patch rückgängig zu machen, wenn die Probleme weiterhin bestehen
* Wenden Sie sich an den Support, wenn Sie Hilfe benötigen

### Authentifizierungs- und Zugriffsfehler

#### „Authentifizierung für Adobe Commerce-Repository fehlgeschlagen“

**Wenn er auftritt:** Während eines beliebigen Stadiums

**Ursache:** oder abgelaufene Adobe Commerce Repository-Anmeldeinformationen

**Lösungen:**

Es gibt zwei empfohlene Optionen zur Lösung dieses Problems:

**Option 1: Beheben `env:COMPOSER_AUTH` Umgebungsvariablen auf Umgebungsebene (empfohlen)**

* Stellen Sie sicher, dass Sie die richtigen Anmeldeinformationen für `env:COMPOSER_AUTH` eingerichtet haben.
* Greifen Sie auf die globale Konfiguration zu, indem Sie oben links in der Benutzeroberfläche Ihres Cloud-Projekts auf das Zahnradsymbol klicken und dann die Registerkarte **Variablen** auswählen.
* Stellen Sie sicher, dass Sie _Zur Build-Zeit verfügbar_ und die Auswahl _Zur Laufzeit verfügbar_ aufheben.

Wenn Option 1 Ihr Problem nicht behebt, fahren Sie mit Option 2 fort.

**Option 2: Erstellen Sie `auth.json` Datei manuell und stellen Sie sie bereit**

* SSH in Ihren Server.
* Abrufen des Inhalts der aktuellen `env:COMPOSER_AUTH`-Variablen mit:\
  `echo $COMPOSER_AUTH`
* Kopieren Sie alle Inhalte aus dem obigen Schritt (im JSON-Format).
* Erstellen Sie eine neue Datei mit dem Namen `auth.json` mit diesen Inhalten.
* Übertragen Sie diese neu erstellte `auth.json` in das Stammverzeichnis Ihres Repositorys.
* Trigger einer neuen Bereitstellung.

#### „Unzureichende Berechtigungen für Umgebungszugriff“

**Wenn es auftritt:** Während der Erstellung oder des Zugriffs auf die Umgebung

**Ursache:** Ihrem Benutzerkonto fehlen die erforderlichen Berechtigungen

**Lösungen:**

* Benutzerrolle und Berechtigungen überprüfen
* Wenden Sie sich an Ihren Systemadministrator
* Vergewissern Sie sich, dass Sie über Berechtigungen zur Umgebungsverwaltung verfügen
* Stellen Sie sicher, dass Sie über Bereitstellungsberechtigungen verfügen

### Fehler bei Ressourcen und Kontingenten

#### „Umgebungskontingent überschritten“

**Wenn er auftritt:** Während der Erstellung der Umgebung

**Ursache:** Sie haben Ihr Umgebungslimit erreicht

**Lösungen:**

* Deaktivieren nicht verwendeter Umgebungen
* Bereinigen alter Verzweigungen und Bereitstellungen
* Support kontaktieren, um eine Quotenerhöhung anzufordern
* Planen Sie ein Upgrade ein

#### „Unzureichende Ressourcen für den Betrieb“

**Wenn er auftritt:** Während eines beliebigen Stadiums

**Ursache:** Ihrer Umgebung fehlt es an ausreichend CPU, Arbeitsspeicher oder Speicher

**Lösungen:**

* Überprüfen der Ressourcennutzung Ihrer Umgebung
* Freigeben von Ressourcen durch Bereinigen von Dateien
* Warten auf die Verfügbarkeit von Ressourcen
* Support kontaktieren, wenn die Ressourcenprobleme weiterhin bestehen

## Hilfe wird abgerufen

**Kontaktaufnahme mit dem Support:**

Wenden Sie sich an den Adobe Commerce Cloud-Support, wenn:

* Fehlermeldungen sind unklar oder nicht detailliert genug
* Patch-Vorgänge schlagen durchgängig fehl
* Sie benötigen Hilfe bei der manuellen Konfliktbewältigung
* Konsistenzprüfungen schlagen fehl, aber die Ursache ist nicht ersichtlich
* Sie benötigen Hilfe bei Synchronisierungsproblemen mit der Umgebung

**Zu liefernde Informationen:**

Geben Sie bei der Kontaktaufnahme mit dem Support Folgendes an:

* **Projekt-ID** - Ihre Adobe Commerce Cloud-Projektkennung
* **Umgebungs-ID** - Die spezifische Umgebung, in der das Problem aufgetreten ist
* **Vorgangs-ID** - Die Kennung des [!DNL CAPS] Vorgangs
* **Fehlerdetails** - Vollständige Fehlermeldungen und -protokolle
* **Schritte zur Reproduktion** - Was Sie bei Auftreten des Fehlers getan haben
* **Frühere Versuche** - Was Sie bereits versucht haben, um das Problem zu beheben

### Zusätzliche Ressourcen

Ausführlichere technische Informationen:

* Überprüfen Sie die vollständigen Fehlerprotokolle zu fehlgeschlagenen Vorgängen
* Informationen zu patchspezifischen Anleitungen finden Sie in der Adobe Commerce-Dokumentation .
* Wenden Sie sich bei umgebungsspezifischen Problemen an den Adobe Commerce Cloud-Support

### Verwandte Themen

* [Dokumentation zu Adobe Commerce Cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview)
* [Adobe Commerce-Installationshandbuch](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview)
* [Einführung von CAPS](intro.md)
* [Zugriff](access.md)
* [Workflow](workflow.md)
* [Best Practices](best-practices.md)
