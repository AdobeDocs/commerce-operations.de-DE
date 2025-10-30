---
title: '[!DNL Cloud Automation Patching Service (CAPS)]'
description: Erfahren Sie mehr über [!DNL Cloud Automation Patching Service (CAPS)], seine Verwendung, den Zugriff darauf und über Best Practices für automatisiertes Patchen
hide: true
hidefromtoc: true
source-git-commit: 4bb2d597e93379dbe81bae100ccc0b94b39acf26
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# [!DNL Cloud Automation Patching Service (CAPS)]

Die [!DNL Cloud Automation Patching Service] ([!DNL CAPS]) ist ein Tool, das das Anwenden und Zurücksetzen von Patches für Adobe Commerce in Cloud-Umgebungen automatisiert. Dies bietet Commerce-Projektadministratoren einen optimierten Workflow zum Anwenden und Zurücksetzen von Patches, einschließlich integrierter Validierungs- und Konsistenzprüfungen, um sicherzustellen, dass Cloud-Umgebungen stabil und sicher bleiben.

Dieses Handbuch richtet sich an Händler und Partner von Adobe Commerce Cloud, die ihren Patching-Prozess optimieren, das Risiko von Patch-bezogenen Problemen reduzieren, die Sicherheit und Stabilität ihrer Umgebung verbessern und routinemäßige Patch-Vorgänge automatisieren möchten.

## [!DNL CAPS] Themen

* **[Zugriff](access.md)**
* **[Workflow](workflow.md)**
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
   * **Validierung**: Führt Konsistenzprüfungen durch und stellt sicher, dass kritische Funktionen nicht betroffen sind

* **Sicherheitsfunktionen**
   * Erstellt temporäre Integrationsumgebungen für Tests
   * Validiert die Patch-Kompatibilität vor der Anwendung
   * Bietet automatisches Rollback bei Validierungsfehlern
   * Wendet Patches auf den `m2-hotfixes` Ordner an und entfernt diese während der Wiederherstellung automatisch

## Integrationen mit Adobe Commerce Cloud

[!DNL CAPS] ist vollständig in die Adobe Commerce Cloud-Infrastruktur integriert und funktioniert nahtlos mit Ihren vorhandenen Cloud-Umgebungen. Sie nutzt Cloud-native Funktionen für eine optimale Leistung, bietet detaillierte Protokollierung und Überwachung und integriert sich mit Adobe Commerce Cloud-Support-Tools.

## Video-Tutorial

Erfahren Sie mehr über den Adobe Cloud Automated Patching Service und wie dieses Tool Benutzenden hilft, Sicherheits-Patches schnell zu finden und anzuwenden. Im folgenden Video wird beschrieben, wie Sie über das SWAT-Dashboard darauf zugreifen, Ihr Projekt und Ihre Umgebung auswählen und Patches mit einem Klick anwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/3476247/?learn=on&enablevpops)

## Häufige Anwendungsfälle

* **Sicherheits-Patches** - Schnelle Anwendung wichtiger Sicherheits-Updates
* **Patch-Rollback**: Sicheres Zurücksetzen problematischer Patches, die über [!DNL CAPS] angewendet wurden
* **Sicherheitskonformität** - Einhaltung von Sicherheitsstandards durch automatisiertes Patchen
* **Betriebsstabilität** - Gewährleistung der Umgebungsstabilität durch automatisierte Validierung
