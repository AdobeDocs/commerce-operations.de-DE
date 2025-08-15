---
title: '[!DNL Dashboard]'
description: Erfahren Sie mehr über die  [!DNL Dashboard] -Registerkarte in den  [!DNL Site-Wide Analysis Tool], den Verwendungszeitpunkt, die Vorteile und die Best Practices.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

Auf der Seite [!UICONTROL Dashboard] werden [!DNL widgets] auf einen Blick angezeigt, die eine „einheitliche Übersicht“ über den Zustand und den aktuellen Status Ihrer Adobe Commerce-Website bieten. Jede [!DNL widget] enthält einen Zugriffs-Link zur Seite jeder Funktion, zu jedem Tool selbst oder zu Berichten (je nach [!DNL widget]).
Es gibt auch eine Liste von [!UICONTROL External Resources] Links für Adobe Commerce, einschließlich der [Adobe Commerce Help Center Support Knowledge Base (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=de), der [Adobe Commerce Developer Documentation (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de){target="_blank"}, [Security Center](https://helpx.adobe.com/de/security.html) und [Observation for Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=de).

## Elemente

* **[!UICONTROL Recommendations]**: Zeigt Best Practice-Empfehlungen für Ihre Site an. Empfehlungen (gefundene Probleme und zu behebende Empfehlungen) werden nach Priorität sortiert: P0 (kritisch) bis P4 (Benachrichtigung).
Zu den Empfehlungen gehören Beschreibung, Empfehlung, Site-Auswirkungen, Grundursache, Szenarien/Voraussetzungen und verwendete Tools.

* **[!UICONTROL Upgrade Compatibility Tool]**: Überprüft eine angepasste Adobe Commerce-Instanz anhand einer bestimmten Version, indem alle darin installierten Module und der Kern-Code analysiert werden. Sie gibt eine Liste mit kritischen Problemen, Fehlern und Warnungen zurück, die vor dem Upgrade auf die neueste Version von Adobe Commerce behoben werden müssen. Außerdem werden potenzielle Probleme identifiziert, die in Ihrem Code behoben werden müssen, bevor Sie versuchen, auf eine neuere Version von Adobe Commerce zu aktualisieren.
Mit dem [!UICONTROL Upgrade Compatibility Tool] können Sie erkennen, wann Änderungen am Kern-Code an benutzerdefinierten Funktionen vorgenommen wurden.

* **[!UICONTROL Security Center Widget]**: Zeigt Sicherheits-Insights für Ihre Site an.
Die angezeigten Sicherheitsinformationen umfassen [Tech- [!DNL Stack] -Compliance mit  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=de), [Adobe Security Bulletin](https://helpx.adobe.com/de/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=de), and [[!DNL Site-Wide Analysis Tool]  Best Practice-Sicherheitsempfehlungen](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=de).<br>
Die [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=de) überwacht Adobe Commerce Sites auf Sicherheitsrisiken. Sie kann proaktiv und effizient Malware in Händlern erkennen und Händler über Sicherheitsrisiken, Malware oder Bedrohungen informieren sowie fehlende Adobe Commerce-Patches und -Updates identifizieren.

* **[!UICONTROL Extensions]**: Zeigt die derzeit auf Ihrer Adobe Commerce-Instanz installierten Erweiterungen an. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) Informationen werden, sofern verfügbar, für die dort aufgeführten Erweiterungen bereitgestellt.

* **[!UICONTROL Alerts]**: Zeigt die neuesten [!DNL New Relic Managed Alerts] für die Adobe Commerce-Instanz an. Weitere Informationen zu [verwalteten Warnhinweisen für Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html?lang=de) und zum [Zugriff auf New Relic-Services](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html?lang=de) finden Sie in der Wissensdatenbank für den Adobe Commerce-Support.

* **[!UICONTROL Non-recommended software in use]**: Zeigt basierend auf Ihrer Adobe Commerce-Version die nicht empfohlene Software an, die Ihre Adobe Commerce-Instanz derzeit verwendet. Die nicht empfohlene Software wird nach [!UICONTROL Name], [!UICONTROL Installed Version] und [!UICONTROL Recommended Version] aufgelistet.

* **[!UICONTROL Recommended Patches]**: Zeigt eine kurze Liste aller empfohlenen Patches an, die sowohl auf bereits installierten Patches als auch auf Ihrer Adobe Commerce-Version basieren. Die vollständige Liste der empfohlenen Patches finden Sie auf der Registerkarte **[!UICONTROL Patches]**-Funktion , die sich auch im [!DNL Site-Wide Analysis Tool] befindet. Die Patches werden bereitgestellt von [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de){target="_blank"}. Alle aufgelisteten Patches sind mit Ihrer aktuellen Adobe Commerce-Instanz kompatibel.
Wenn für Ihre Adobe Commerce-Instanz keine empfohlenen Patches zum Anzeigen vorhanden sind, wird dieser [!DNL widget] **[!UICONTROL No Recommended Patches]** angezeigt.

## Verwendungszeitpunkt

Die **[!UICONTROL Dashboard]** Seite ist Ihr übersichtliches Befehlszentrum in der [!DNL Site-Wide Analysis Tool], das nicht nur einfach das „Gesamtbild“ des Zustands Ihrer Site als Ganzes anzeigt, sondern Sie können auch über jede [!DNL widget] spezifische Tools, Empfehlungen und Berichte für Ihre Adobe Commerce-Website anzeigen und darauf zugreifen.

## Vorteile

* Die [!DNL widgets] für [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions] und [!UICONTROL Security Scan] verwenden leicht lesbare, farbcodierte interaktive Kreisdiagramme mit Diagrammlegenden auf der Seite und Zählersummen in der Mitte, um anzugeben, wie viele [!UICONTROL Recommendations], [!UICONTROL Extensions] und [!UICONTROL Security Scan Tool] Elemente jede Funktion hat. [!UICONTROL Recommendations] und [!UICONTROL Security Scan Tool] Diagramme werden nach Schweregrad getrennt. [!UICONTROL Extensions] sind in vier Klassifizierungen unterteilt: aktuelle Version, alte Version, deaktiviert und unbekannt.

* [!DNL New Relic Alerts] werden mit dem neuesten Warnhinweis oben aufgeführt, einschließlich einer kurzen Beschreibung und der Frage, wie lange der Warnhinweis zurückliegt.

* Die [!UICONTROL Recommendations]- und [!UICONTROL Extensions]-[!DNL widgets] haben durch Klicken auf &quot;**[!UICONTROL View All]**&quot; Zugriff auf die vollständige Datenseite für jede Funktion.

* Die [!UICONTROL Security Scan Tool] enthält im **[!UICONTROL View Report]** einen [!DNL widget] Link, über den Sie zur [!UICONTROL Recommendations] gelangen.

* Der [!DNL Upgrade Compatibility Tool] verfügt über eine Schaltfläche **[!UICONTROL Run Upgrade Scan]** im [!DNL widget].

## Best Practices für die Verwendung des [!UICONTROL Dashboard]

* Klicken Sie auf die einzelnen [!DNL widget], um auf die darin enthaltenen detaillierten Daten zuzugreifen, um sowohl insight als auch das Verständnis der Sicherheit, des Zustands, der Empfehlungen und der Best Practices Ihrer Website zur Verbesserung der Website zu erlangen.

* Gehen Sie zum [!UICONTROL Security Scan Tool] [!DNL widget] und klicken Sie auf [!UICONTROL View Report] , um einen [!UICONTROL Recommendations] für Ihre Site anzuzeigen.

* Verwenden Sie die [!DNL External Resources] Links, um entweder weitere Informationen zu erhalten, sich über Sicherheits-Patches, Updates und Best Practices auf dem Laufenden zu halten oder die insight der [Adobe Commerce Help Center Support Knowledge Base (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=de), der [Adobe Commerce Developer Documentation (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de){target="_blank"}, [Security Center](https://helpx.adobe.com/de/security.html) und [Observation for Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=de) zu nutzen.
