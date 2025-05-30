---
title: '[!DNL Site-Wide Analysis Tool]'
description: Erfahren Sie mehr über  [!DNL Site-Wide Analysis] -Tool, seine Verwendungszwecke, den Installationsprozess und den Zugriff darauf
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 5f39a2d8440225b3a2e463894e2bd866196fbac2
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>Ab dem 23. April 2024 wird die [!DNL Site-Wide Analysis Tool] für alle Adobe Commerce On-Premise-Kunden eingestellt.

Dieses Handbuch bietet einen ganzheitlichen Überblick über die [!DNL Site-Wide Analysis Tool]. Es beschreibt die Verwendungen, schrittweise Installationsanweisungen und den Zugriff auf das Tool.

## Was ist [!DNL Site-Wide Analysis Tool]?

Das [!DNL Site-Wide Analysis Tool] ist ein proaktives Self-Service-Tool und ein zentrales Repository, das detaillierte Systemeinblicke und Empfehlungen bietet, um die Sicherheit und Bedienbarkeit Ihrer Adobe Commerce-Installation sicherzustellen. Sie bietet rund um die Uhr eine Echtzeit-Leistungsüberwachung, Berichte und Beratung, um potenzielle Probleme zu identifizieren und den Site-Status, die Sicherheit und Anwendungskonfigurationen besser einsehen zu können. Dies trägt dazu bei, die Auflösungszeit zu reduzieren und die Stabilität und Leistung der Site zu verbessern.

![Dashboard des Site-Wide Analysis Tool](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Weitere Informationen finden [ in ](https://www.youtube.com/watch?v=KW2R8ki_RG4) Einführungsvideo.

## Tool-Übersicht

- **Dashboard**
   - Zeigt den Gesamtzustand Ihres Systems mit Benachrichtigungen zu erkannten Problemen und spezifischen Empfehlungen nach Priorität.<br>
Sie enthält auch ein Verlaufsdiagramm, in dem die Veränderungen des Zustands Ihrer Website im Laufe der Zeit dargestellt werden.
   - Zeigt die **[!UICONTROL Security Center Widget]** an, auf die Sie zugreifen können:
      - [Tech [!DNL Stack] Version Compliance mit [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=de)
      - [Adobe-Sicherheitsbulletin](https://helpx.adobe.com/de/security/security-bulletin.html)
      - [Recommendations aus dem [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=de)
      - [[!DNL Site-Wide Analysis Tool] Best Practice-Sicherheits-Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=de)

- **Informationen**: Enthält Kontaktinformationen für den Kunden und eine Zusammenfassung aktueller Tickets sowie detaillierte Informationen zu jedem installierten Adobe Commerce-Produkt.

- **Recommendations** - Listet Empfehlungen auf, die auf Best Practices basieren, um auf Ihrer Site festgestellte Probleme zu beheben:
   - Für Änderungen, die eine Aktualisierung der Infrastruktur erfordern, senden Sie eine Support-Anfrage.
   - Nehmen Sie die Änderungen, für die ein Programm-Update erforderlich ist, selbst vor.
   - Wenden Sie sich bei Änderungen, die ein manuelles Eingreifen erfordern, wie [Code-Bereitstellung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=de#deployment-workflow), an Ihren Systemadministrator oder Ihre Entwickler.

- **Ausnahmen** - Listet Fehler auf, die von der Anwendung ausgelöst wurden und durch abnormale Bedingungen ohne einen Fehler-Handler verursacht wurden.

- **Erweiterungen** - Listet alle Erweiterungen von Drittanbietern und Bibliotheken von Drittanbietern auf.

- **Patches** - In die [!DNL Quality Patches Tool] integriert, enthält sie eine Liste aller verfügbaren Patches, die für Ihre Adobe Commerce-Instanz spezifisch sind.

## Integrationen mit anderen Adobe Commerce-Support-Tools

Sehen Sie alle wichtigen Einblicke über Ihre Website an einem Ort. [!DNL Site-Wide Analysis Tool] erhalten Sie direkten Zugriff auf und Informationen von den [!UICONTROL Security Center Widget], [!DNL Upgrade Compatability Tool] und [!DNL Managed Alerts].

- [**[!UICONTROL Security Center Widget]**] - Zeigt Sicherheitserkenntnisse für Ihre Site an.<br>
Die angezeigten Sicherheitsinformationen umfassen die [Tech [!DNL Stack] Version Compliance with [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=de), [Adobe Security Bulletin](https://helpx.adobe.com/de/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=de), and [[!DNL Site-Wide Analysis Tool] Best Practice Security Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=de).<br>
Das [[!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=de) bietet Kunden von Adobe Commerce und Magento Open-Source Echtzeiteinblicke in den Sicherheitsstatus ihres Stores, indem es proaktiv Malware entdeckt und sie benachrichtigt, wenn ihr Store gefährdet ist.

- [**[!DNL Upgrade Compatability Tool]**](../../upgrade/upgrade-compatibility-tool/overview.md) - Führt die angepasste Adobe Commerce-Instanz für die Ziel-Upgrade-Version aus und gibt eine Zusammenfassung kritischer Probleme, Fehler und Warnungen zurück, die behoben werden müssen, was den Upgrade-Analyseprozess einfacher, schneller und kostengünstiger macht.

- [**[!DNL Managed Alerts]**](https://support.magento.com/hc/en-us/sections/360010758472-Managed-alerts-for-Adobe-Commerce) - Überwachen Sie mehrere Metriken, um die Leistung der Plattform proaktiv zu verfolgen, und stellen Sie spezifische Anweisungen zur Fehlerbehebung bereit, damit Händler kritische Ausfallzeiten vermeiden und über CPU, Anwendungs-Performance, Festplatte, Speicher und Datenbank auf dem Laufenden bleiben können.

## Für wen ist dieser Leitfaden geeignet?

Händler und Partner, die mehr Einblick in ihre Adobe Commerce-Websites erhalten möchten. Sie ermöglicht es Händlern, die Kundenerfahrung zu verbessern und Best Practices, Empfehlungen und grundlegende Probleme besser aufeinander abzustimmen.

## [!DNL Site-Wide Analysis Tool] Demo

In diesem Video erfahren Sie mehr über die [!DNL Site-Wide Analysis Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/3411355?quality=12&captions=ger)
