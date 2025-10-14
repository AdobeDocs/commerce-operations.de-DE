---
title: Wie greife ich auf zu [!DNL Cloud Automation Patching Service (CAPS)]
description: Erfahren Sie, wie Sie auf zugreifen und verwenden können [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# So greifen Sie auf [!DNL Cloud Automation Patching Service (CAPS)] zu

## Voraussetzungen

[!DNL CAPS] verwendet die rollenbasierte Zugriffssteuerung von Adobe Commerce Cloud. Ihre Zugriffsebene in der Cloud-Konsole bestimmt, was Sie mit [!DNL CAPS] tun können.

### Wer [!DNL CAPS] verwenden kann

* **Projektadministrator** - Kann Patches auf alle Umgebungen anwenden oder zurücksetzen
* **Mitwirkender** - Kann Patches auf zugewiesene Umgebungen anwenden oder zurücksetzen
* **Viewer** - Kann nur das Projekt und die Umgebungen anzeigen, keine Aktionen zulässig

### Anfordern des Zugriffs auf ein Projekt

Wenn in der [!DNL CAPS] Benutzeroberfläche keine Projekte angezeigt werden, müssen Sie den Zugriff von der entsprechenden Person anfordern:

* Kontaktieren Sie den Kontoinhaber oder Projektadministrator des Projekts.
* Sie erhalten über die Cloud-Konsole die entsprechende Rolle.
* Sobald Sie Zugriff erhalten haben, können Sie sich bei der Cloud-Konsole anmelden, um [!DNL CAPS] zu verwenden

>[!NOTE]
>
>[!DNL CAPS] folgt demselben Berechtigungsmodell wie Adobe Commerce Cloud, sodass Ihre Zugriffsebene in der Cloud-Konsole bestimmt, was Sie mit [!DNL CAPS] tun können.

## Zugriff auf [!DNL CAPS]

Das CAPS-Tool ist im Dashboard des Site-Wide Analysis Tool unter [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/) verfügbar. Auf der Registerkarte Patching-Automatisierung können Sie Ihr Projekt und Ihre Umgebung auswählen.

1. Navigieren Sie zum Site-Wide Analysis Tool unter [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/).
1. Klicken Sie in der Benutzeroberfläche auf die Registerkarte [!UICONTROL Patching Automation] .
1. Wählen Sie das Projekt und die Umgebung aus, in der Sie Patches anwenden möchten.
1. Überprüfen Sie die verfügbaren Patches und ihren Kompatibilitätsstatus.
1. Wählen Sie Patches aus, die angewendet oder zurückgesetzt werden sollen.

## Zugriff auf die Produktionsumgebung

Für Produktionsumgebungen gelten zusätzliche Sicherheitsmaßnahmen:

* **Wartungsmodus** - Muss aktiviert sein
* **Cron-Aufträge** - Muss deaktiviert werden
* **Bestätigungsdialogfeld** - Muss abgeschlossen sein, bevor Sie fortfahren

>[!IMPORTANT]
>
>Für das Patchen von Produktionsumgebungen sind eine ordnungsgemäße Vorbereitung und Sicherheitsmaßnahmen erforderlich, um unbeabsichtigte Unterbrechungen zu verhindern.

## Verwandte Themen

* [Einführung von CAPS](intro.md)
* [Workflow](workflow.md)
* [Best Practices](best-practices.md)
* [Fehlerbehebung](troubleshooting.md)
