---
title: Zugriff [!DNL Site-Wide Analysis Tool]
description: Erfahren Sie, wie Sie auf die [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 5f9f81b930a3b23c0b334ccbea94d296338a0048
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Zugriff auf die [!DNL Site-Wide Analysis Tool]

Es gibt zwei Möglichkeiten, auf die [!DNL Site-Wide Analysis Tool Dashboard].

Sie können auf die [!DNL dashboard] von der [[!DNL Site-Wide Analysis Tool] Webseite](https://supportinsights.adobe.com/commerce) directly **(nur für Adobe Commerce auf Cloud-Infrastruktur)** und melden Sie sich mit Ihrer Adobe ID an oder greifen Sie über die [!DNL dashboard] aus dem Geschäft [!DNL Admin Panel].

Die [!DNL Site-Wide Analysis Tool] -Dienst verfügbar unter [Produktionsmodus](https://docs.magento.com/user-guide/magento/installation-modes.html) für [!DNL Admin] Benutzer mit Zugriffsberechtigung für Benutzer [Rollenressourcen](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Wenn Sie eine lokale Installation von Adobe Commerce haben, müssen Sie eine [Agent](../site-wide-analysis-tool/installation.md) in Ihrer Infrastruktur, um das Tool zu verwenden.

![Dashboard für Site-weite Analysen](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Dashboard*

## Option 1: Anmeldung bei Ihrer [!DNL Site-Wide Analysis Tool Dashboard] direkt aus dem [!DNL Site-Wide Analysis Tool] Domäne (nur für Adobe Commerce auf Cloud-Infrastruktur)

Ein **[!DNL Adobe ID]ist erforderlich** für den Zugriff auf [!DNL Commerce] -Konto.
Wenn Sie bereits über eine [!DNL Commerce] -Konto, Sie haben jedoch keine [!DNL Adobe ID], können Sie eine während des Anmeldeprozesses erstellen.

1. Navigieren Sie zu [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. Klicken Sie auf **[!UICONTROL Sign in with Adobe ID]** und folgen Sie den Anweisungen.

   ![Dashboard für Site-weite Analysen](../../assets/tools/adobe-id-login.jpg)
   *[!DNL Adobe ID]Anmeldebildschirm*

1. Akzeptieren Sie die Geschäftsbedingungen.

1. **<u>Hinweis</u>:** Ihr Konto sollte berechtigt sein, **[!DNL Support Permissions]** für den Zugriff [!DNL Site-Wide Analysis Tool Dashboard].
Weitere Informationen finden Sie unter [Freigeben von [!DNL Commerce] account](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) in unserem Benutzerhandbuch.

## Option 2: Anmeldung bei Ihrer [!DNL Site-Wide Analysis Tool Dashboard] aus dem Geschäft [!DNL Admin Panel]

### Schritt 1: Berechtigungen überprüfen

Stellen Sie sicher, dass [!DNL Admin] Das Benutzerkonto hat Zugriff auf die [!DNL Site-Wide Analysis Tool] durch [zugewiesene Benutzerrolle](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>Die [!DNL Site-Wide Analysis Tool] Benutzerressource (Berechtigung) ist **not** automatisch zugewiesen. Sie MUSS für die Benutzerrolle und die Rolle aktiviert werden, die jedem Benutzerkonto im [!UICONTROL Admin].

Für die benutzerdefinierte Rolle [!DNL Site-Wide Analysis Tool] -Zugriff verwenden, führen Sie folgende Schritte aus:

1. Wählen Sie die **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** Rolle.

   ![Dashboard für Site-weite Analysen](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]für die Rolle ausgewählte Berechtigung*

1. Klicken **[!UICONTROL Save Role]**.

1. Benachrichtigen Sie alle Benutzer, denen diese Rolle zugewiesen wurde, über die Abmeldung von der [!DNL Admin]und melden Sie sich erneut an.

>[!NOTE]
>
>Wenn Sie überprüft haben, ob das Benutzerkonto über die Berechtigung zum Zugriff auf die [!DNL Site-Wide Analysis Tool] und der Benutzer beim Versuch, auf das Tool zuzugreifen, einen 403-Fehler von der [!DNL Admin]festlegen, kann für Ihre Adobe Commerce-Instanz in der Cloud-Infrastruktur die HTTP-Zugriffssteuerung aktiviert sein. Die [!DNL Site-Wide Analysis Tool] Dashboard wird NICHT unterstützt, wenn HTTP Auth aktiviert ist. Weitere Informationen zur Behebung dieses Problems finden Sie in der [Support-Artikel](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### Schritt 2: Zugriff [!DNL Site-Wide Analysis Tool]

1. Im *[!UICONTROL Admin]* Seitenleiste, navigieren Sie zu **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Dashboard für Site-weite Analysen](../../assets/tools/ac-admin-panel-marked.jpg)
   *[!DNL Site-Wide Analysis Tool]-Position im [!DNL Admin Panel] in Adobe Commerce*

1. Lesen Sie die *Nutzungsbedingungen* für die [!DNL Site-Wide Analysis Tool] und klicken **[!UICONTROL Accept]** , um fortzufahren.

   Jeder Benutzer muss die Nutzungsbedingungen für die Sitzung akzeptieren. Dieser Schritt wird für jede angemeldete Sitzung wiederholt.


1. Klicken Sie oben im Dashboard auf die gewünschte Registerkarte.

   ![Dashboard für Site-weite Analysen](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]Informationen*

## Erstellen Sie Berichte aus dem [!DNL Site-Wide Analysis Tool Dashboard]

1. Klicken Sie oben rechts im Dashboard auf **[!UICONTROL Generate Report]**.

1. Aktivieren Sie das Kontrollkästchen für jede **[!UICONTROL Type]** und **[!UICONTROL Priority]** festlegen, die Sie in den Bericht aufnehmen möchten.

1. Klicken **[!UICONTROL Generate Report]**.

   ![Dashboard für Site-weite Analysen](../../assets/tools/swat-report-settings.png)
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
>Nach Anwendung einer Empfehlung kann es einige Tage dauern, bis sie im [!DNL Site-Wide Analysis Tool Dashboard] oder generierten Bericht.
