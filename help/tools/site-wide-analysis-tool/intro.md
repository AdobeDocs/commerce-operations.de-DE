---
title: '[!DNL Site-Wide Analysis Tool]'
description: Erfahren Sie mehr über das [!DNL Site-Wide Analysis] Tool, dessen Verwendung, den Installationsprozess und wie Sie Zugriff erhalten
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 5f39a2d8440225b3a2e463894e2bd866196fbac2
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>Mit Wirkung vom 23. April 2024 wird der [!DNL Site-Wide Analysis Tool] für alle Adobe Commerce-Kunden vor Ort eingestellt.

Dieses Handbuch bietet einen ganzheitlichen Überblick über die [!DNL Site-Wide Analysis Tool]. Hier werden die Verwendungen, schrittweise Anweisungen für die Installation und der Zugriff auf das Tool beschrieben.

## Was ist [!DNL Site-Wide Analysis Tool]?

Der [!DNL Site-Wide Analysis Tool] ist ein proaktives Self-Service-Tool und zentrales Repository, das detaillierte Systemeinblicke und Empfehlungen enthält, um die Sicherheit und Bedienbarkeit Ihrer Adobe Commerce-Installation sicherzustellen. Es bietet rund um die Uhr eine Leistungsüberwachung, Berichte und Beratung in Echtzeit, um potenzielle Probleme zu identifizieren und bessere Sichtbarkeit in Bezug auf Gesundheit, Sicherheit und Anwendungskonfigurationen der Website zu erreichen. Dies trägt zur Verkürzung der Auflösungszeit und zur Verbesserung der Site-Stabilität und -Leistung bei.

![Dashboard des Site-weiten Analyse-Tools](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Weitere Informationen finden Sie in diesem [Einführungsvideo](https://www.youtube.com/watch?v=KW2R8ki_RG4) .

## Tool-Übersicht

- **Dashboard**
   - Zeigt den allgemeinen Zustand Ihres Systems mit Benachrichtigungen zu erkannten Problemen und spezifischen Empfehlungen nach Priorität an.<br>
Sie enthält auch ein historisches Diagramm, um zu verfolgen, wie sich die Gesundheit Ihrer Website im Laufe der Zeit ändert.
   - Zeigt den **[!UICONTROL Security Center Widget]** an, über den Sie auf Folgendes zugreifen können:
      - [Tech [!DNL Stack] Versionskonformität mit  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)
      - [Adobe-Sicherheitsbulletin](https://helpx.adobe.com/security/security-bulletin.html)
      - [Recommendations vom  [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html)
      - [[!DNL Site-Wide Analysis Tool] Best Practice Security Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html)

- **Informationen** - Bietet Kontaktinformationen für Kunden und eine Zusammenfassung der aktuellen Tickets mit detaillierten Informationen zu den installierten Adobe Commerce-Produkten.

- **Recommendations** - Führt Empfehlungen basierend auf Best Practices zur Behebung von auf Ihrer Site erkannten Problemen auf:
   - Senden Sie für Änderungen, die eine Aktualisierung der Infrastruktur erfordern, eine Support-Anfrage.
   - Nehmen Sie die Änderungen für Änderungen, die eine Aktualisierung der Anwendung erfordern, selbst vor.
   - Wenden Sie sich bei Änderungen, die manuelles Eingreifen erfordern, z. B. eine [Codebereitstellung](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow), an Ihren Systemadministrator oder -entwickler, um Hilfe zu erhalten.

- **Ausnahmen** - Führt Fehler auf, die von der Anwendung ausgegeben werden und durch ungewöhnliche Bedingungen ohne Fehler-Handler verursacht wurden.

- **Erweiterungen** - Führt alle Drittanbietererweiterungen und Drittanbieterbibliotheken auf.

- **Patches** - In den [!DNL Quality Patches Tool] integriert, bietet er eine Liste aller verfügbaren Patches, die für Ihre Adobe Commerce-Instanz spezifisch sind.

## Integrationen mit anderen Adobe Commerce-Support-Tools

Zeigen Sie alle wichtigen Einblicke in Ihre Site an einem Ort an. Mit [!DNL Site-Wide Analysis Tool] können Sie direkten Zugriff auf und Informationen aus den [!UICONTROL Security Center Widget], [!DNL Upgrade Compatability Tool] und [!DNL Managed Alerts] erhalten.

- [**[!UICONTROL Security Center Widget]**] - Zeigt Sicherheitseinblicke für Ihre Site an.<br>
Zu den angezeigten Sicherheitsinformationen gehören die [Tech [!DNL Stack] Versionskonformität mit [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Best Practice Security Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
Der [[!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) bietet Adobe Commerce- und Magento Open-Source-Kunden Echtzeiteinblicke in den Sicherheitsstatus ihres Stores, indem sie proaktiv Malware erkennen und sie darüber informieren, ob ihr Speicher gefährdet ist.

- [**[!DNL Upgrade Compatability Tool]**](../../upgrade/upgrade-compatibility-tool/overview.md) - Führt die angepasste Instanz von Adobe Commerce mit der Ziel-Upgrade-Version aus und gibt eine Zusammenfassung kritischer Probleme, Fehler und Warnungen zurück, die behoben werden müssen, wodurch der Prozess der Upgrade-Analyse einfacher, schneller und billiger wird.

- [**[!DNL Managed Alerts]**](https://support.magento.com/hc/en-us/sections/360010758472-Managed-alerts-for-Adobe-Commerce) - Überwachen Sie mehrere Metriken, um die Leistung der Plattform proaktiv zu verfolgen, und geben Sie spezifische Anweisungen zur Fehlerbehebung, damit Händler kritische Ausfallzeiten vermeiden und über CPU, Anwendungsleistung, Datenträger, Speicher und Datenbank auf dem Laufenden bleiben können.

## Für wen ist dieser Leitfaden?

Händler und Partner, die eine bessere Sichtbarkeit ihrer Adobe Commerce-Websites wünschen. Sie ermöglicht es Händlern, das Kundenerlebnis zu verbessern und eine bessere Abstimmung auf die Empfehlungen zu Best Practices und grundlegende Fragen zu erreichen.

## [!DNL Site-Wide Analysis Tool] Demo

Sehen Sie sich dieses Video an, um mehr über die [!DNL Site-Wide Analysis Tool] zu erfahren:

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
