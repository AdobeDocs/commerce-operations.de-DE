---
title: So greifen Sie auf [!DNL Adobe Commerce Patching Automation] zu
description: Erfahren Sie, wie Sie auf [!DNL Adobe Commerce Patching Automation] zugreifen und sie verwenden können
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%
---
# So greifen Sie auf [!DNL Adobe Commerce Patching Automation] zu

## Voraussetzungen

[!DNL Patching Automation] verwendet die rollenbasierte Zugriffssteuerung von Adobe Commerce Cloud. Ihre Zugriffsebene in der Cloud-Konsole bestimmt, was Sie mit dem Service tun können.

### Wer [!DNL Patching Automation] verwenden kann

* **Projektadministrator** - Kann Patches auf alle Umgebungen anwenden oder zurücksetzen
* **Mitwirkender** - Kann Patches auf zugewiesene Umgebungen anwenden oder zurücksetzen
* **Viewer** - Kann nur das Projekt und die Umgebungen anzeigen, keine Aktionen zulässig

### Anfordern des Zugriffs auf ein Projekt

Wenn in der [!DNL Patching Automation] Benutzeroberfläche keine Projekte angezeigt werden, fordern Sie den Zugriff von der entsprechenden Person an:

* Kontaktieren Sie den Kontoinhaber oder Projektadministrator des Projekts.
* Sie können Ihnen über die Cloud-Konsole die entsprechende Rolle zuweisen
* Sobald Sie Zugriff erhalten haben, können Sie sich bei der Cloud-Konsole anmelden, um den Service zu verwenden

>[!NOTE]
>
>[!DNL Patching Automation] folgt demselben Berechtigungsmodell wie Adobe Commerce Cloud, sodass Ihre Zugriffsebene in der Cloud-Konsole bestimmt, was Sie mit dem Service tun können.

## Zugriff auf [!DNL Patching Automation]

[!DNL Patching Automation] ist als Registerkarte im [!DNL Site-Wide Analysis Tool]-Dashboard verfügbar. Sie können darauf über Ihr Admin-Bedienfeld zugreifen, indem Sie in der Admin **Seitenleiste zu** > **Systemeinblicke** > **Site-Wide Analysis Tool** wechseln. Unter [Zugriff auf das Site-Wide Analysis Tool](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/site-wide-analysis-tool/access) finden Sie Informationen zu Voraussetzungen und Berechtigungseinstellungen.

Sobald Sie sich im Dashboard befinden:

1. Klicken Sie in der Benutzeroberfläche auf die Registerkarte [!UICONTROL Patching Automation] .
1. Wählen Sie das Projekt und die Umgebung aus, in der Sie Patches anwenden möchten.
1. Überprüfen Sie die verfügbaren Patches und ihren Kompatibilitätsstatus.
1. Wählen Sie Patches aus, die angewendet oder zurückgesetzt werden sollen.

## Zugriff auf die Produktionsumgebung

Für Produktionsumgebungen gelten standardmäßig zusätzliche Sicherheitsmaßnahmen:

* **Wartungsmodus** - Muss aktiviert sein
* **Cron-Aufträge** - Muss deaktiviert werden
* **Bestätigungsdialogfeld** - Muss abgeschlossen sein, bevor Sie fortfahren

>[!IMPORTANT]
>
>Für das Patchen von Produktionsumgebungen sind eine ordnungsgemäße Vorbereitung und Sicherheitsmaßnahmen erforderlich, um unbeabsichtigte Unterbrechungen zu verhindern.

>[!NOTE]
>
>Sie können die Prüfungen des Wartungsmodus und des Cron-Auftrags überspringen, indem Sie das Kontrollkästchen „Überschreiben“ in der Benutzeroberfläche auswählen (*[!UICONTROL I want to skip maintenance mode and cron checks before applying patches to production environment]*). Verwenden Sie dies nur, wenn Sie das Risiko eines Patches der Produktion ohne diese Sicherheitsmaßnahmen verstehen.

## Verwandte Themen

* [Einführung in die Patch-Automatisierung](intro.md)
* [Workflow-Übersicht](workflow.md)
* [GitHub-Integration](github-integration.md)
* [Best Practices](best-practices.md)
* [Fehlerbehebung](troubleshooting.md)
