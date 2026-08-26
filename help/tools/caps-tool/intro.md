---
title: '[!DNL Adobe Commerce Patching Automation]'
description: Erfahren Sie mehr über [!DNL Adobe Commerce Patching Automation], seine Verwendung, den Zugriff darauf und über Best Practices für automatisiertes Patchen
hide: true
source-git-commit: f70924d6f0d1777104c59f3f9e776360308abceb
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation]

[!DNL Adobe Commerce Patching Automation] ist ein Tool, das das Anwenden und Zurücksetzen von Patches für Adobe Commerce in Cloud-Umgebungen automatisiert. Dadurch erhalten Commerce-Projektadministratoren einen optimierten Workflow zum Anwenden und Zurücksetzen von Patches. Integrierte Validierungs- und Konsistenzprüfungen stellen sicher, dass Cloud-Umgebungen stabil und sicher bleiben.

Dieses Handbuch richtet sich an Händler und Partner von Adobe Commerce Cloud, die ihren Patching-Prozess optimieren, das Risiko von Patch-bezogenen Problemen reduzieren, die Sicherheit und Stabilität ihrer Umgebung verbessern und routinemäßige Patch-Vorgänge automatisieren möchten.

## [!DNL Patching Automation] Themen

* **[Zugriff](access.md)**
* **[Workflow-Übersicht](workflow.md)**
* **[GitHub-Integration](github-integration.md)**
* **[Best Practices](best-practices.md)**
* **[Fehlerbehebung](troubleshooting.md)**

## Tool-Übersicht

* **Benutzeroberfläche**
  * Verfügbarkeit von Echtzeit-Patches und Statusanzeige für bestimmte Projekt- und Umgebungskombinationen
  * Umfassende Informationen zum Patch-Status, die den Fortschritt, Fehler und andere relevante Meldungen anzeigen
  * [!UICONTROL Patch Management Dashboard] für:
    * Anzeigen verfügbarer Patches
    * Anwenden von Patches mit einem Klick
    * Wiederherstellen zuvor angewendeter Patches
    * Überwachen des Status und der Ergebnisse des Patch-Vorgangs

* **Automatisierter Patch-Service mit strukturiertem Workflow**
  * **Vorprüfung** - Validiert die Patch-Kompatibilität und die Bereitschaft für die Umgebung
  * **Patchen** - Wendet Patches in Integrationsumgebungen automatisch an oder setzt sie zurück
  * **Validierung**: Führt eine Konsistenzprüfung durch, um zu bestätigen, dass die Anwendung gestartet wird und die Datenbank- und Cache-Verbindungen erreichbar sind

* **Sicherheitsfunktionen**
  * Validiert die Patch-Kompatibilität vor der Anwendung
  * Wendet den Patch zuerst in einer temporären Integrationsumgebung an und bestätigt, dass er erfolgreich bereitgestellt wurde und eine Konsistenzprüfung besteht, bevor er in die Zielumgebung zusammengeführt wird. Anschließend führt er unmittelbar nach der Bereitstellung eine abschließende Konsistenzprüfung durch
  * Wendet Patches auf den `m2-hotfixes` Ordner an und entfernt diese während der Wiederherstellung automatisch

## Integrationen mit Adobe Commerce Cloud

[!DNL Patching Automation] ist vollständig in die Adobe Commerce Cloud-Infrastruktur integriert und funktioniert nahtlos mit Ihren vorhandenen Cloud-Umgebungen. Sie nutzt Cloud-native Funktionen für eine optimale Leistung, bietet detaillierte Protokollierung und Überwachung und integriert sich mit Adobe Commerce Cloud-Support-Tools.

## Video-Tutorial

Erfahren Sie mehr über [!DNL Adobe Commerce Patching Automation] und wie dieses Tool Benutzern hilft, Sicherheits-Patches schnell zu finden und anzuwenden. Im folgenden Video wird beschrieben, wie Sie über das Dashboard des Site-Wide Analysis Tool (SWAT) darauf zugreifen, Ihr Projekt und Ihre Umgebung auswählen und Patches mit einem Klick anwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/3476247/?learn=on&enablevpops)

## Häufige Anwendungsfälle

* **Sicherheits-Patches** - Schnelle Anwendung wichtiger Sicherheits-Updates
* **Patch-Rollback**: Sicheres Zurücksetzen problematischer Patches, die über den Service angewendet wurden
* **Sicherheitskonformität** - Einhaltung von Sicherheitsstandards durch automatisiertes Patchen
* **Betriebsstabilität** - Bestätigt, dass die Anwendung nach jedem Patch-Vorgang gestartet wird und eine Konsistenzprüfung besteht
