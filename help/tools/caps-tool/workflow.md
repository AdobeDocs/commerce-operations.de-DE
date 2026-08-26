---
title: Workflow-Übersicht [!DNL Adobe Commerce Patching Automation]
description: Erfahren Sie mehr über  [!DNL Adobe Commerce Patching Automation]  Workflow-Prozess, einschließlich Terminologie, Workflow-Phasen und Vorgänge für die automatisierte Patch-Verwaltung.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---

# Workflow-Übersicht [!DNL Adobe Commerce Patching Automation]

Dieses Thema bietet einen allgemeinen Überblick darüber, wie Patch-Vorgänge mithilfe von [!DNL Adobe Commerce Patching Automation] funktionieren.

## Terminologie

* **Vorgänge** - die wichtigsten vom Service ausgeführten Aktionen:
  * Übernehmen
  * Zurück zur letzten Version
* **Phasen** - die drei Phasen des Workflows:
  * Vorprüfung
  * Flicken
  * Validierung
* **Umgebung** - die Adobe Commerce-Cloud-Umgebung, in der Patches angewendet werden.

## Vorgänge

[!DNL Patching Automation] unterstützt zwei *(Vorgänge* zum Verwalten von Patches in Ihrer Adobe Commerce Cloud-Umgebung:

* **Apply operation** - Fügt Ihrer Codebasis über einen sicheren, validierten Prozess Patch-Änderungen hinzu. Patches werden angewendet, indem Patch-Dateien im `m2-hotfixes` Ordner abgelegt werden.

* **Wiederherstellungsvorgang** - Entfernt zuvor angewendete Patches aus Ihrer Codebasis, indem es Patch-Dateien aus dem `m2-hotfixes` Ordner entfernt.

>[!IMPORTANT]
>
>Wiederherstellungsvorgänge sind nur für Patches verfügbar, die ursprünglich über [!DNL Patching Automation] angewendet wurden. Patches, die manuell oder über andere Methoden angewendet wurden, können mit diesem Service nicht rückgängig gemacht werden.

## Phasen

Der [!DNL Patching Automation]-Workflow verwendet drei *Phasen* die immer in dieser Reihenfolge ausgeführt werden, um sicherzustellen, dass Patches sicher und zuverlässig angewendet werden:

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

In der Patch-Phase wird der Patch in einer temporären Integrationsumgebung angewendet oder rückgängig gemacht. In dieser Phase erstellt der Service eine temporäre Integrationsumgebung, um den Patch sicher anzuwenden, die erfolgreiche Bereitstellung zu bestätigen und sicherzustellen, dass er eine Konsistenzprüfung besteht, bevor Änderungen an der tatsächlichen Umgebung vorgenommen werden.

Dieser Ansatz bietet:

* **Sicherheit** - Behält Ihre Zielumgebung unberührt, bis die Integrationsumgebung erfolgreich bereitgestellt wird und die Konsistenzprüfung besteht
* **Rollback-Funktion** - wenn Probleme erkannt werden
* **Isolierung** - für jeden Patch-Vorgang

#### Phase 2a: Erstellung der Integrationsumgebung

**Verzweigungserstellung** - [!DNL Patching Automation] erstellt einen temporären Integrationsumgebungszweig mit dem Namen `{target-environment}-CAPS-{patch-id}`

**Umgebung einrichten** - Die Integrationsumgebung wird als untergeordnetes Element Ihrer Zielumgebung erstellt

**Code-**: Die Integrationsumgebung übernimmt den genauen Code-Status Ihrer Zielumgebung (dieselbe Codebasis)

**Kein Daten-Cloning** - Die Integrationsumgebung erhält keine Kopie der Daten der Zielumgebung (Datenbank, Medien oder anderer gespeicherter Inhalt). Nur die Code-Basis wird zum Anwenden und Überprüfen des Patches verwendet

**Ressourcenanforderungen** - Die gesamte Speicherkapazität Ihres Cloud-Projekts ist in Ihrem Vertrag definiert. (Überprüfen Sie dies über Ihre Kontoseite oder `magento-cloud subscription:info`). Die Festplattenzuordnung jeder Umgebung wird separat über die `disk`-Eigenschaft in `.magento.app.yaml`/`.magento/services.yaml` konfiguriert. Weitere [&#x200B; finden Sie unter &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) von Festplattenspeicher . Wenn ein Patch-Vorgang aufgrund von Speicherbeschränkungen fehlschlägt, überprüfen Sie die Festplattenauslastung (`magento-cloud db:size`/`magento-cloud mount:size`) Ihrer Integrationsumgebung in Bezug auf die konfigurierte Zuordnung.

#### Schritt 2b: Patchen der Anwendung in der Integrationsumgebung

**Sichere Tests** - Der Patch wird auf die Integrationsumgebung angewendet, nicht direkt auf Ihre Zielumgebung

**Dateiverwaltung** - Patch-Dateien werden im `m2-hotfixes` Ordner abgelegt

**Git-Vorgänge** - Änderungen werden übertragen und in den Zweig der Integrationsumgebung übertragen

**Umgebungsaktivierung** - Die Integrationsumgebung wird aktiviert, um den gepatchten Code bereitzustellen

**Konsistenzprüfung** - Nach der Aktivierung bestätigt [!DNL Patching Automation] Folgendes, bevor mit der Zusammenführung fortgefahren wird: Die Integrationsumgebung wurde erfolgreich bereitgestellt, ist in Ordnung, die Anwendung wird gestartet und die Datenbank- und Cache-Verbindungen sind erreichbar.

>[!NOTE]
>
>Wenn Ihr Projekt ein externes GitHub-Repository verwendet, übernimmt der Service die Authentifizierung automatisch mithilfe der [[!DNL Patching Automation] GitHub-App](github-integration.md). Über die Installation der App hinaus sind keine zusätzlichen Anmeldeinformationen erforderlich.

#### Schritt 2c: Zurück zur Zielumgebung

**Synchronisierungsprüfung**: Vor dem Zusammenführen bestätigt der Service, dass die Integrationsumgebung weiterhin aktiv, mit der Zielumgebung synchronisiert und in Ordnung ist. Wenn das Ziel während des Patches geändert wurde, wird der Vorgang hier angehalten, anstatt zusammengeführt zu werden

**Umgebungs-Checkout** - Der Service überprüft Ihre Zielumgebung lokal

**Zusammenführungsvorgang** - Der Zweig der Integrationsumgebung wird mit der Zielumgebung zusammengeführt

**Konfliktbehandlung** - Wenn ein Zusammenführungskonflikt auftritt, schlägt der Vorgang fehl und wird als Fehler gemeldet. Er wird nicht automatisch aufgelöst.

**Bereitstellung** - Die zusammengeführten Änderungen werden in Ihrer Zielumgebung bereitgestellt

**Überprüfung** Der Service überprüft, ob die Zusammenführung erfolgreich war und die Umgebungen synchronisiert sind

### Lebenszyklus der Integrationsumgebung

Integrationsumgebungen haben während der Patching-Phase einen bestimmten Lebenszyklus:

* **Erstellung** - Wird zu Beginn der Patch-Phase erstellt
* **Aktiver Zeitraum** - Während der Patch-Anwendung und der Tests aktiv bleiben
* **Bereinigung** - Wird sofort gelöscht, wenn der Vorgang während der Patching-Phase vor der Zusammenführung fehlschlägt. Andernfalls wird während der Validierungsphase, nach der Zusammenführung, gelöscht, unabhängig davon, ob die Validierung erfolgreich war oder nicht

### Phase 3: Validierung

Die Validierungsphase bestätigt, dass die gepatchte Anwendung erfolgreich gestartet wurde und eine Konsistenzprüfung besteht.

**Was passiert:**

* **Konsistenzprüfung der Anwendung** - Überprüft, ob die Anwendung ordnungsgemäß gestartet und ausgeführt wird und ob die Datenbank- und Cache-Verbindungen erreichbar sind
* **Bereinigung** - entfernt die temporäre Integrationsumgebung und aktualisiert den Auftragsstatus entsprechend dem Abschluss. Die Aktivität der Umgebung bleibt im Aktivitäts-Feed Ihres Projekts sichtbar.

>[!IMPORTANT]
>
>Im Gegensatz zu den Phasen 1 und 2 wird diese Konsistenzprüfung ausgeführt *nachdem* Patch bereits in Ihrer Zielumgebung zusammengeführt wurde. Wenn die Zusammenführung fehlschlägt, wird sie nicht automatisch zurückgesetzt. Ihre Zielumgebung kann beschädigt bleiben und ein manuelles Eingreifen (z. B. Zurücksetzen des Patches) ist erforderlich, um sie wiederherzustellen. Unter [Fehlerbehebung](troubleshooting.md) finden Sie Informationen dazu, was in diesem Fall zu tun ist.

## Erfolgsindikatoren

**Vorgang anwenden:**

* „Auftrag erfolgreich abgeschlossen“ - Patch ohne Probleme angewendet
* „Patch wurde angewendet“ - Patch war bereits vorhanden (keine Aktion erforderlich)
* Patch-Datei erfolgreich in `m2-hotfixes` Ordner platziert
* Alle Validierungsprüfungen erfolgreich
* Konsistenzprüfungen der Anwendung erfolgreich

**Wiederherstellungsvorgang:**

* „Auftrag erfolgreich abgeschlossen“ - Patch ohne Probleme zurückgesetzt
* „Patch wurde zurückgesetzt“ - Patch wurde bereits zurückgesetzt (keine Aktion erforderlich)
* Patch-Datei wurde erfolgreich aus `m2-hotfixes` Ordner entfernt
* Alle Validierungsprüfungen erfolgreich
* Konsistenzprüfungen der Anwendung erfolgreich

## Sicherheitsmaßnahmen für die Produktionsumgebung

Das Anwenden oder Zurücksetzen von Patches in einer Produktionsumgebung ist mit höheren Risiken verbunden als in anderen Umgebungen. [!DNL Patching Automation] umfasst daher zwei produktionsspezifische Sicherheitsmaßnahmen.

### Bestätigung vor Beginn

Bevor ein Anwenden- oder Zurücksetzen-Vorgang in einer Produktionsumgebung gestartet wird, werden Sie aufgefordert, den Vorgang in einem Dialogfeld zu bestätigen. Dieser Bestätigungsschritt schützt vor dem versehentlichen Starten eines Auftrags in der Produktion.

### Empfohlene Voraussetzungen

Adobe empfiehlt, den Wartungsmodus zu aktivieren und Cron-Aufträge zu deaktivieren, bevor eine Produktionsumgebung gepatcht wird. Standardmäßig überprüft [!DNL Patching Automation], ob beide Bedingungen erfüllt sind, und blockiert den Vorgang mit einer Benachrichtigung, wenn eine der Bedingungen nicht erfüllt ist. Wenn Sie die Risiken verstehen, ohne den Wartungsmodus oder mit aktivierten Cron-Aufträgen fortzufahren, aktivieren Sie das Kontrollkästchen „Überschreiben“ in der Benutzeroberfläche, um diese Prüfung zu umgehen.

* **Wartungsmodus** - Wird zur Aktivierung empfohlen
* **Cron-Aufträge** - Empfohlen, deaktiviert zu werden

## Verwandte Themen

* [Einführung in die Patch-Automatisierung](intro.md)
* [Zugriff](access.md)
* [GitHub-Integration](github-integration.md)
* [Best Practices](best-practices.md)
* [Fehlerbehebung](troubleshooting.md)
