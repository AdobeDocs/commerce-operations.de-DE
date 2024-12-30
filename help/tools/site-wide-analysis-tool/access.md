---
title: Wie greife ich auf zu [!DNL Site-Wide Analysis Tool]
description: Erfahren Sie, wie Sie auf zugreifen [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Zugreifen auf die [!DNL Site-Wide Analysis Tool]

Es gibt zwei Möglichkeiten, auf die [!DNL Site-Wide Analysis Tool Dashboard] zuzugreifen.

Sie können auf die [!DNL dashboard] entweder über die [[!DNL Site-Wide Analysis Tool] Website](https://supportinsights.adobe.com/commerce) direkt **nur für Adobe Commerce auf Cloud-**) zugreifen und sich mit Ihrer Adobe ID anmelden oder über die [!DNL dashboard] in der [!DNL Admin Panel] Ihres Stores zugreifen.

Der [!DNL Site-Wide Analysis Tool]-Service ist im [Produktionsmodus](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#operation-modes) für [!DNL Admin] Benutzer mit der Berechtigung zum Zugriff auf [Rollenressourcen](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles) verfügbar.

>[!NOTE]
>
>Ab dem 23. April 2024 wurde die [!DNL Site-Wide Analysis Tool] eingestellt und ist nicht mehr für Kunden von Adobe Commerce On-Premise verfügbar.


![Site-Wide Analysis Dashboard](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Dashboard*

## Option 1: Direktes Anmelden bei Ihrem [!DNL Site-Wide Analysis Tool Dashboard] über die [!DNL Site-Wide Analysis Tool] Domain (nur für Adobe Commerce in der Cloud-Infrastruktur)

Ein **[!DNL Adobe ID]ist erforderlich** um auf ein [!DNL Commerce] Konto zuzugreifen.
Wenn Sie bereits über ein [!DNL Commerce]-Konto verfügen, aber noch kein [!DNL Adobe ID] haben, können Sie dieses während des Anmeldevorgangs erstellen.

1. Navigieren Sie zu [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. Klicken Sie auf die Schaltfläche **[!UICONTROL Sign in with Adobe ID]** und folgen Sie den Anweisungen.

   ![Site-Wide Analysis Dashboard](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]Anmeldebildschirm*

1. Akzeptieren Sie die Nutzungsbedingungen.

1. **<u>Hinweis</u>:** Ihr Konto sollte berechtigt sein, zu **[!DNL Support Permissions]**, um auf [!DNL Site-Wide Analysis Tool Dashboard] zugreifen zu können.
Weitere Informationen finden Sie unter [Freigeben eines  [!DNL Commerce] -Kontos](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) in unserem Benutzerhandbuch.

## Option 2: Anmelden bei Ihrem [!DNL Site-Wide Analysis Tool Dashboard] über die [!DNL Admin Panel] Ihres Stores

### Schritt 1: Berechtigungen überprüfen

Vergewissern Sie sich, dass das [!DNL Admin] Benutzerkonto über die Berechtigung verfügt, über die [zugewiesene Benutzerrolle](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/user-accounts/permissions-user-roles) auf die [!DNL Site-Wide Analysis Tool] zuzugreifen.

>[!IMPORTANT]
>
>Die Ressource mit der [!DNL Site-Wide Analysis Tool] Rolle (Berechtigung **wird** automatisch zugewiesen. Sie MUSS für die Benutzerrolle und die Rolle aktiviert werden, die jedem Benutzerkonto in der [!UICONTROL Admin] einzeln zugewiesen sind.

Gehen Sie für die benutzerdefinierte Rolle, die Zugriff [!DNL Site-Wide Analysis Tool] benötigt, wie folgt vor:

1. Wählen Sie die Ressource **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** aus.

   ![Site-Wide Analysis Dashboard](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]Berechtigung für die Rolle ausgewählt*

1. Klicken Sie auf **[!UICONTROL Save Role]**.

1. Benachrichtigen Sie alle Benutzer, denen diese Rolle zugewiesen wurde, sich von der [!DNL Admin] abzumelden und sich erneut anzumelden.

>[!NOTE]
>
>Wenn Sie sich vergewissert haben, dass das Benutzerkonto über die Berechtigung zum Zugriff auf die [!DNL Site-Wide Analysis Tool] verfügt und der/die Benutzende beim Versuch, über die [!DNL Admin] auf das Tool zuzugreifen, die Fehlermeldung 403 erhält, könnte für Ihre Instanz von Adobe Commerce in der Cloud-Infrastruktur die HTTP-Zugriffssteuerung aktiviert sein. Das [!DNL Site-Wide Analysis Tool]-Dashboard wird NICHT unterstützt, wenn die HTTP-Authentifizierung aktiviert ist. Weitere Informationen zur Lösung dieses Problems finden Sie in unserem [Support-Artikel](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### Schritt 2: [!DNL Site-Wide Analysis Tool]

1. Navigieren Sie in der *[!UICONTROL Admin]* Seitenleiste zu **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Site-Wide Analysis Dashboard](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]in der [!DNL Admin Panel] in Adobe Commerce*

1. Lesen Sie die *Nutzungsbedingungen* für die [!DNL Site-Wide Analysis Tool] und klicken Sie **[!UICONTROL Accept]**, um fortzufahren.

   Jeder Benutzer muss die Nutzungsbedingungen für die Sitzung akzeptieren. Dieser Schritt wird für jede angemeldete Sitzung wiederholt.


1. Klicken Sie oben im Dashboard auf die Registerkarte, die Sie sehen möchten.

   ![Site-Wide Analysis Dashboard](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]Informationen*

## Generieren von Berichten aus dem [!DNL Site-Wide Analysis Tool Dashboard]

1. Klicken Sie oben rechts im Dashboard auf **[!UICONTROL Generate Report]**.

1. Aktivieren Sie das Kontrollkästchen für jede **[!UICONTROL Type]** und jede **[!UICONTROL Priority]**, die Sie in den Bericht aufnehmen möchten.

1. Klicken Sie auf **[!UICONTROL Generate Report]**.

   ![Site-Wide Analysis Dashboard](../../assets/tools/swat-report-settings.png)
   *Berichteinstellungen*

| REGISTERKARTE | BESCHREIBUNG |
| --- | --- |
| Dashboard | Zeigt den Zustand Ihres Systems mit aktuellen Benachrichtigungen und Empfehlungen nach Priorität an. |
| Informationen | Enthält Kontaktinformationen für den Kunden und eine Zusammenfassung der aktuellen Tickets sowie detaillierte Informationen zu den einzelnen installierten Adobe Commerce-Produkten. |
| Recommendations | Listet Empfehlungen auf, die auf Best Practices zur Behebung von auf Ihrer Site festgestellten Problemen basieren. |
| Ausnahmen | Listet von der Anwendung ausgelöste Fehler auf, die durch abnormale Bedingungen ohne einen Fehler-Handler verursacht wurden. |
| Erweiterungen | Listet alle Erweiterungen und Bibliotheken von Drittanbietern auf. |

>[!NOTE]
>
>Nach der Anwendung einer Empfehlung kann es einige Tage dauern, bis sie im [!DNL Site-Wide Analysis Tool Dashboard] oder generierten Bericht aktualisiert wird.
