---
title: Einrichten der GitHub-Integration für [!DNL Adobe Commerce Patching Automation]
description: Erfahren Sie, wie Sie die GitHub [!DNL Adobe Commerce Patching Automation] App installieren, um Patch-Vorgänge für mit GitHub verbundene Adobe Commerce Cloud-Projekte zu aktivieren.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# Einrichten der GitHub-Integration für [!DNL Patching Automation]

Wenn Ihr Adobe Commerce Cloud-Projekt mit einem GitHub-Repository verbunden ist, müssen Sie die [!DNL Patching Automation] GitHub-App installieren, bevor Sie den Service zum Anwenden oder Zurücksetzen von Patches verwenden können. Die App gewährt dem Service den Zugriff, den er benötigt, um Änderungen an Ihrem Repository in Ihrem Namen vorzunehmen.

## Voraussetzungen

* Aktives Adobe Commerce Cloud-Abonnement
* Eine [GitHub](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github)Integration, die bereits für Ihr Adobe Commerce Cloud-Projekt konfiguriert ist und bei der die [`fetch-branches` aktiviert ist](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration). [!DNL Patching Automation] erstellt und pusht temporäre Verzweigungen der Integrationsumgebung, sodass Patch-Vorgänge die Umgebung nicht erstellen, wenn diese Option deaktiviert ist.
* Ein auf [!DNL github.com] gehostetes Repository. GitHub-Integrationen, die mit einer benutzerdefinierten Domain konfiguriert sind, werden nicht unterstützt.
* Inhaber- oder Administratorzugriff auf die GitHub-Organisation oder das GitHub-Repository

## Installieren der [!DNL Patching Automation] GitHub-App

Sie können die Installation von [!DNL Patching Automation] starten, indem Sie in der Benutzeroberfläche auf **[!UICONTROL Install GitHub App]** klicken, wodurch Sie zur Installationsseite weitergeleitet werden, oder indem Sie direkt zur Installationsseite navigieren.

1. Öffnen Sie die [GitHub-App-Installationsseite zur Patch-Automatisierung](https://github.com/apps/adobe-commerce-patching-automation).
1. Klicken Sie auf **[!UICONTROL Install]**.
1. Wählen Sie die GitHub-Organisation aus, der Ihr Adobe Commerce-Repository gehört.
1. Wählen Sie unter **[!UICONTROL Repository access]** die Option **[!UICONTROL Only select repositories]** und wählen Sie das Repository für Ihr Adobe Commerce-Projekt aus.
1. Klicken Sie zur Bestätigung auf **[!UICONTROL Install]** .

Nach der Installation erkennt der Service automatisch Ihre GitHub-Verbindung und verwendet die App für alle Patch-Vorgänge. Es ist keine weitere Einrichtung erforderlich.

## Überprüfen und Verwalten des Verbindungsstatus

Die [!DNL Patching Automation] Benutzeroberfläche zeigt den aktuellen Status Ihrer GitHub-Verbindung an, wobei die Aktionen abhängig von diesem Status verfügbar sind:

* **[!UICONTROL Refresh]**/**[!UICONTROL Refresh status]** - Überprüft den Verbindungsstatus erneut, ohne Änderungen vorzunehmen.
* **[!UICONTROL Reinstall]** - Wird angezeigt, wenn die Installation nicht mehr gültig ist (z. B. wenn sie ausgesetzt wurde oder das mit Ihrem Cloud-Projekt verbundene Repository geändert wurde). Startet denselben Installationsablauf wie oben beschrieben.
* **[!UICONTROL Unlink GitHub App]** - Entfernt die gespeicherte Verbindung von [!DNL Patching Automation] mit der GitHub-App. Dadurch wird **App** aus Ihrem GitHub-Repository deinstalliert - siehe den Abschnitt „Deinstallieren“ unten, um den Zugriff vollständig zu entfernen.

## Deinstallieren der [!DNL Patching Automation] GitHub-App

Wenn der Dienst nicht mehr auf Ihr Repository zugreifen soll:

1. Öffnen Sie in GitHub die Einstellungen für das Konto, dem die Installation gehört:
   * Für ein **organisationseigenes** Repository: **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * Für ein **persönliches** Repository: **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. Suchen Sie nach `adobe-commerce-patching-automation` und klicken Sie auf **[!UICONTROL Configure]**.
1. Klicken Sie auf **[!UICONTROL Uninstall]** und bestätigen Sie.

>[!WARNING]
>
>Wenn beim Deinstallieren der GitHub-App noch Anwenden- oder Zurücksetzen-Vorgänge ausgeführt werden, können diese Vorgänge fehlschlagen. Nach der Deinstallation der App können Benutzende auch keine neuen Vorgänge starten, da die Aktionsschaltflächen inaktiv werden.

## Verwandte Themen

* [Einführung in die Patch-Automatisierung](intro.md)
* [Zugriff](access.md)
* [Workflow-Übersicht](workflow.md)
* [Best Practices](best-practices.md)
* [Fehlerbehebung](troubleshooting.md)
