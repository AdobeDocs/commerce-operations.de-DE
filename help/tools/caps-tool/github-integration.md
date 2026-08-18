---
title: Einrichten der GitHub-Integration für [!DNL CAPS]
description: Erfahren Sie, wie Sie die GitHub [!DNL Cloud Automation Patching Service (CAPS)] App installieren, um Patch-Vorgänge für mit GitHub verbundene Adobe Commerce Cloud-Projekte zu aktivieren.
hide: true
source-git-commit: 2887956e8644ffbcaadde36b90a0fc984369008a
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---


# Einrichten der GitHub-Integration für [!DNL CAPS]

Wenn Ihr Adobe Commerce Cloud-Projekt mit einem GitHub-Repository verbunden ist, müssen Sie die [!DNL CAPS] GitHub-App installieren, bevor Sie die [!DNL Cloud Automation Patching Service] ([!DNL CAPS]) zum Anwenden oder Zurücksetzen von Patches verwenden können. Die App gewährt [!DNL CAPS] den Zugriff, den sie benötigt, um in Ihrem Namen Änderungen an Ihrem Repository vorzunehmen.

## Voraussetzungen

* Aktives Adobe Commerce Cloud-Abonnement
* Eine [GitHub](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github)Integration, die bereits für Ihr Adobe Commerce Cloud-Projekt konfiguriert ist und bei der die [`fetch-branches` aktiviert ist](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration). [!DNL CAPS] erstellt und pusht temporäre Verzweigungen der Integrationsumgebung, sodass Patch-Vorgänge die Umgebung nicht erstellen, wenn diese Option deaktiviert ist.
* Ein auf [!DNL github.com] gehostetes Repository. GitHub-Integrationen, die mit einer benutzerdefinierten Domain konfiguriert sind, werden nicht unterstützt.
* Inhaber- oder Administratorzugriff auf die GitHub-Organisation oder das GitHub-Repository

## Installieren der [!DNL CAPS] GitHub-App

1. Öffnen Sie die [CAPS GitHub-App-Installationsseite](https://github.com/apps/adobe-commerce-patching-automation).
1. Klicken Sie auf **[!UICONTROL Install]**.
1. Wählen Sie die GitHub-Organisation aus, der Ihr Adobe Commerce-Repository gehört.
1. Wählen Sie unter **[!UICONTROL Repository access]** die Option **[!UICONTROL Only select repositories]** und wählen Sie das Repository für Ihr Adobe Commerce-Projekt aus.
1. Klicken Sie zur Bestätigung auf **[!UICONTROL Install]** .

Nach der Installation erkennt [!DNL CAPS] automatisch Ihre GitHub-Verbindung und verwendet die App für alle Patch-Vorgänge. Es ist keine weitere Einrichtung erforderlich.

## Deinstallieren der [!DNL CAPS] GitHub-App

Wenn [!DNL CAPS] nicht mehr auf Ihr Repository zugreifen möchten:

1. Öffnen Sie in GitHub die Einstellungen für das Konto, dem die Installation gehört:
   * Für ein **organisationseigenes** Repository: **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * Für ein **persönliches** Repository: **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. Suchen Sie nach `adobe-commerce-patching-automation` und klicken Sie auf **[!UICONTROL Configure]**.
1. Klicken Sie auf **[!UICONTROL Uninstall]** und bestätigen Sie.

>[!WARNING]
>
>Wenn beim Deinstallieren der GitHub-App noch CAPS angewendet oder Rücksetzungsvorgänge ausgeführt werden, können diese Vorgänge fehlschlagen. Nach der Deinstallation der App können Benutzende auch keine neuen Vorgänge starten, da die Aktionsschaltflächen inaktiv werden.

## Verwandte Themen

* [Einführung von CAPS](intro.md)
* [Zugriff](access.md)
* [Workflow-Übersicht](workflow.md)
* [Best Practices](best-practices.md)
* [Fehlerbehebung](troubleshooting.md)
