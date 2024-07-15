---
title: Zugriff auf [!DNL Site-Wide Analysis Tool]
description: Erfahren Sie, wie Sie auf den [!DNL Site-Wide Analysis Tool] zugreifen.
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 5f9f81b930a3b23c0b334ccbea94d296338a0048
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Zugriff auf die [!DNL Site-Wide Analysis Tool]

Es gibt zwei Möglichkeiten, auf den [!DNL Site-Wide Analysis Tool Dashboard] zuzugreifen.

Sie können entweder von der [[!DNL Site-Wide Analysis Tool] Website](https://supportinsights.adobe.com/commerce) direkt **(nur für Adobe Commerce in der Cloud-Infrastruktur) aus auf die [!DNL dashboard] zugreifen und sich bei Ihrer Adobe ID anmelden oder über die [!DNL dashboard] von der [!DNL Admin Panel] Ihres Stores aus auf die Datei zugreifen.**

Der Dienst [!DNL Site-Wide Analysis Tool] ist im [Produktionsmodus](https://docs.magento.com/user-guide/magento/installation-modes.html) für [!DNL Admin] -Benutzer mit Zugriffsberechtigung auf Benutzer [Benutzerrollenressourcen](https://docs.magento.com/user-guide/system/permissions-user-roles.html) verfügbar.

>[!NOTE]
>
>Wenn Sie eine lokale Installation von Adobe Commerce haben, müssen Sie einen [Agenten](../site-wide-analysis-tool/installation.md) in Ihrer Infrastruktur installieren, um das Tool zu verwenden.

![ Dashboard für eine Site-weite Analyse](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Dashboard*

## Option 1: Anmeldung bei Ihrem [!DNL Site-Wide Analysis Tool Dashboard] direkt über die Domäne [!DNL Site-Wide Analysis Tool] (nur für Adobe Commerce über die Cloud-Infrastruktur)

Für den Zugriff auf ein [!DNL Commerce] -Konto ist **[!DNL Adobe ID]erforderlich.**
Wenn Sie bereits über ein [!DNL Commerce] -Konto verfügen, aber nicht über ein [!DNL Adobe ID] verfügen, können Sie während des Anmeldevorgangs eines erstellen.

1. Wechseln Sie zu [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Sign in with Adobe ID]** und folgen Sie den Anweisungen.

   ![ Dashboard für eine Site-weite Analyse](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]Anmeldebildschirm*

1. Akzeptieren Sie die Geschäftsbedingungen.

1. **<u>Hinweis</u>:** Ihr Konto sollte auf **[!DNL Support Permissions]** berechtigt sein, um auf [!DNL Site-Wide Analysis Tool Dashboard] zuzugreifen.
Weitere Informationen finden Sie unter [Ein [!DNL Commerce] Konto teilen](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) in unserem Benutzerhandbuch.

## Option 2: Anmeldung bei Ihrem [!DNL Site-Wide Analysis Tool Dashboard] von Ihrem Store [!DNL Admin Panel]

### Schritt 1: Berechtigungen überprüfen

Vergewissern Sie sich, dass das [!DNL Admin]-Benutzerkonto über die Berechtigung zum Zugriff auf die [!DNL Site-Wide Analysis Tool] über ihre [zugewiesene Benutzerrolle](https://docs.magento.com/user-guide/system/permissions-user-roles.html) verfügt.

>[!IMPORTANT]
>
>Die Rolle &quot;[!DNL Site-Wide Analysis Tool]&quot;-Ressource (Berechtigung) ist &quot;**nicht**&quot;, die automatisch zugewiesen wird. Sie MUSS für die Benutzerrolle und die Rolle aktiviert werden, die jedem Benutzerkonto in der [!UICONTROL Admin] einzeln zugewiesen sind.

Gehen Sie wie folgt vor, um die benutzerdefinierte Rolle zu verwenden, auf die [!DNL Site-Wide Analysis Tool] zugreifen muss:

1. Wählen Sie die Rollenressource **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** aus.

   ![ Dashboard für eine Site-weite Analyse](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]Berechtigung für die Rolle ausgewählt*

1. Klicken Sie auf **[!UICONTROL Save Role]**.

1. Benachrichtigen Sie alle Benutzer, denen diese Rolle zugewiesen wurde, über die Abmeldung von der [!DNL Admin] und melden Sie sich erneut an.

>[!NOTE]
>
>Wenn Sie überprüft haben, ob das Benutzerkonto über die Berechtigung zum Zugriff auf &quot;[!DNL Site-Wide Analysis Tool]&quot;verfügt und der Benutzer beim Versuch, über &quot;[!DNL Admin]&quot;auf das Tool zuzugreifen, einen 403-Fehler erhält, kann für Ihre Instanz von Adobe Commerce in der Cloud-Infrastruktur die HTTP-Zugriffssteuerung aktiviert sein. Das Dashboard [!DNL Site-Wide Analysis Tool] wird NICHT unterstützt, wenn HTTP Auth aktiviert ist. Weitere Informationen zur Behebung dieses Problems finden Sie in unserem [Support-Artikel](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### Schritt 2: Zugriff auf [!DNL Site-Wide Analysis Tool]

1. Gehen Sie auf der *[!UICONTROL Admin]* Seitenleiste zu **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![ Dashboard für eine Site-weite Analyse](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]Position im [!DNL Admin Panel] in Adobe Commerce*

1. Lesen Sie die *Nutzungsbedingungen* für die [!DNL Site-Wide Analysis Tool] und klicken Sie auf **[!UICONTROL Accept]** , um fortzufahren.

   Jeder Benutzer muss die Nutzungsbedingungen für die Sitzung akzeptieren. Dieser Schritt wird für jede angemeldete Sitzung wiederholt.


1. Klicken Sie oben im Dashboard auf die gewünschte Registerkarte.

   ![ Dashboard für eine Site-weite Analyse](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]information*

## Generieren von Berichten aus dem [!DNL Site-Wide Analysis Tool Dashboard]

1. Klicken Sie in der rechten oberen Ecke des Dashboards auf **[!UICONTROL Generate Report]**.

1. Aktivieren Sie das Kontrollkästchen für jede Einstellung **[!UICONTROL Type]** und **[!UICONTROL Priority]**, die Sie in den Bericht aufnehmen möchten.

1. Klicken Sie auf **[!UICONTROL Generate Report]**.

   ![ Dashboard für eine Site-weite Analyse](../../assets/tools/swat-report-settings.png)
   *Berichtseinstellungen*

| TAB | BESCHREIBUNG |
| --- | --- |
| Dashboard | Zeigt den Systemzustand mit aktuellen Benachrichtigungen und Empfehlungen nach Priorität an. |
| Informationen | Bietet Kontaktinformationen für Kunden und eine Zusammenfassung der aktuellen Tickets mit detaillierten Informationen zu den einzelnen installierten Adobe Commerce-Produkten. |
| Recommendations | Listet Empfehlungen auf, die auf Best Practices basieren, um auf Ihrer Site erkannte Probleme zu beheben. |
| Ausnahmen | Listet von der Anwendung ausgelöste Fehler auf, die durch anormale Bedingungen ohne Fehler-Handler verursacht wurden. |
| Erweiterungen | Listet alle Drittanbietererweiterungen und Drittanbieterbibliotheken auf. |

>[!NOTE]
>
>Nach Anwendung einer Empfehlung kann es einige Tage dauern, bis sie im [!DNL Site-Wide Analysis Tool Dashboard] - oder generierten Bericht aktualisiert wird.
