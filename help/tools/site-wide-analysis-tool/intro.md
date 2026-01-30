---
title: '[!DNL Site-Wide Analysis Tool]'
description: Erfahren Sie mehr über  [!DNL Site-Wide Analysis] -Tool, seine Verwendungszwecke, den Installationsprozess und den Zugriff darauf
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 62ca9093228d4d928d6c61c4c5dcf26e142c9fdb
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>Ab dem 23. April 2024 wird die [!DNL Site-Wide Analysis Tool] für alle Adobe Commerce On-Premise-Kunden eingestellt.

Dieses Handbuch bietet einen ganzheitlichen Überblick über die [!DNL Site-Wide Analysis Tool]. Es beschreibt die Verwendungen, schrittweise Installationsanweisungen und den Zugriff auf das Tool.

## Was ist der [!DNL Site-Wide Analysis Tool]?

Das [!DNL Site-Wide Analysis Tool] ist ein proaktives Self-Service-Tool und ein zentrales Repository, das detaillierte Systemeinblicke und Empfehlungen bietet, um die Sicherheit und Bedienbarkeit Ihrer Adobe Commerce-Installation sicherzustellen. Sie bietet rund um die Uhr eine Echtzeit-Leistungsüberwachung, Berichte und Beratung, um potenzielle Probleme zu identifizieren und den Site-Status, die Sicherheit und Anwendungskonfigurationen besser einsehen zu können. Dies trägt dazu bei, die Auflösungszeit zu reduzieren und die Stabilität und Leistung der Site zu verbessern.

>[!NOTE]
>
>Nachdem eine Empfehlung angewendet wurde, kann es einige Tage dauern, bis sie im Dashboard des Site-Wide Analysis Tool aktualisiert oder der Bericht generiert wird.
>
>Der [!DNL Site-Wide Analysis Tool] berichtet über Daten auf Systemebene. Berichte zu Produkten, Vertrieb, Marketing und anderen Commerce-Anwendungsdaten von Adobe Commerce finden Sie unter [Adobe Commerce-Berichte](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu).

![Dashboard des Site-Wide Analysis Tool](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Weitere Informationen finden [ in ](https://www.youtube.com/watch?v=KW2R8ki_RG4) Einführungsvideo.

## Tool-Übersicht

- **Dashboard**
   - Zeigt den Gesamtzustand Ihres Systems mit Benachrichtigungen zu erkannten Problemen und spezifischen Empfehlungen nach Priorität.<br>
Sie enthält auch ein Verlaufsdiagramm, in dem die Veränderungen des Zustands Ihrer Website im Laufe der Zeit dargestellt werden.
   - Zeigt die **[!UICONTROL Security Center Widget]**, die Links zu den folgenden Ressourcen bereitstellt:
      - [Tech [!DNL Stack] Version Compliance mit [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements)
      - [Adobe-Sicherheitsbulletin](https://helpx.adobe.com/security/security-bulletin.html)
      - [Empfehlungen der [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan)
      - [[!DNL Site-Wide Analysis Tool] Best Practice-Sicherheitsempfehlungen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations)

- **Informationen**: Enthält Kontaktinformationen für den Kunden und eine Zusammenfassung aktueller Tickets sowie detaillierte Informationen zu jedem installierten Adobe Commerce-Produkt.

- **Recommendations** - Bietet einen [SWAT Health Index-Wert](#swat-health-index.md) zum Nachverfolgen der Site-Konsistenz und listet Empfehlungen auf, die auf Best Practices basieren, um auf Ihrer Site erkannte Probleme zu beheben:
   - Für Änderungen, die eine Aktualisierung der Infrastruktur erfordern, senden Sie eine Support-Anfrage.
   - Nehmen Sie die Änderungen, für die ein Programm-Update erforderlich ist, selbst vor.
   - Wenden Sie sich bei Änderungen, die ein manuelles Eingreifen erfordern, wie [Code-Bereitstellung](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow), an Ihren Systemadministrator oder Ihre Entwickler.

- **Ausnahmen** - Listet Fehler auf, die von der Anwendung ausgelöst wurden und durch abnormale Bedingungen ohne einen Fehler-Handler verursacht wurden.

- **Erweiterungen** - Listet alle Erweiterungen von Drittanbietern und Bibliotheken von Drittanbietern auf.

- **Patches** - In die [!DNL Quality Patches Tool] integriert, enthält sie eine Liste aller verfügbaren Patches, die für Ihre Adobe Commerce-Instanz spezifisch sind.

## Integrationen mit anderen Adobe Commerce-Support-Tools

Sehen Sie sich wichtige Erkenntnisse über Ihre Website an einem Ort an. [!DNL Site-Wide Analysis Tool] erhalten Sie direkten Zugriff auf und Informationen von den [!UICONTROL Security Center Widget], [!DNL Upgrade Compatibility Tool] und [!DNL Managed Alerts].

- **[!UICONTROL Security Center Widget]** : Zeigt Sicherheitserkenntnisse für Ihre Site an.<br>
Die Sicherheitsinformationen umfassen [Tech- [!DNL Stack] -Compliance mit  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirement), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan), and [[!DNL Site-Wide Analysis Tool]  Best Practice-Sicherheitsempfehlungen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations).

  Die [[!DNL Security Scan Tool]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) bietet Kunden von Adobe Commerce und Magento Open-Source Echtzeiteinblicke in den Sicherheitszustand ihres Stores, indem sie proaktiv Malware erkennen und sie benachrichtigen, wenn ihr Store gefährdet ist.

- **[[!DNL Upgrade Compatibility Tool]](../../upgrade/upgrade-compatibility-tool/overview.md)** - Überprüft Ihre Adobe Commerce-Instanz anhand der Upgrade-Version und kennzeichnet vor dem Upgrade kritische Probleme, Fehler und Warnungen, die behoben werden müssen. Die Behebung dieser Probleme optimiert den Upgrade-Prozess.“

- **[[!DNL Managed Alerts]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce)** - Überwachen Sie Schlüsselmetriken (CPU, Anwendungsleistung, Festplatte, Arbeitsspeicher und Datenbankzustand) und stellen Sie klare Schritte zur Fehlerbehebung bereit, damit Händler Probleme bewältigen und Ausfallzeiten vermeiden können.

## Für wen ist dieser Leitfaden geeignet?

Händler und Partner, die mehr Einblick in ihre Adobe Commerce-Websites erhalten möchten. Sie ermöglicht es Händlern, die Kundenerfahrung zu verbessern und Best-Practice-Empfehlungen und grundlegende Probleme besser aufeinander abzustimmen.

## [!DNL Site-Wide Analysis Tool] Demo

In diesem Video erfahren Sie mehr über die [!DNL Site-Wide Analysis Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
