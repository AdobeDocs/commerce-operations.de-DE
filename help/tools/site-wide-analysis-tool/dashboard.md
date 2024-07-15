---
title: '[!DNL Dashboard]'
description: Erfahren Sie mehr über die Registerkarte [!DNL Dashboard] im  [!DNL Site-Wide Analysis Tool], die Elemente, den Verwendungszeitpunkt, die Vorteile und Best Practices.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

Die Seite &quot;[!UICONTROL Dashboard]&quot; zeigt einen Überblick über [!DNL widgets], die eine &quot;Einzelne Glasansicht&quot;des Gesundheitszustands und des aktuellen Status Ihrer Adobe Commerce-Website bieten. Jede [!DNL widget] enthält einen Link zum Zugriff auf die Seite jeder Funktion, zu jedem Tool selbst oder zu Berichten (je nach dem [!DNL widget]).
Es gibt auch eine Liste von [!UICONTROL External Resources] Links für Adobe Commerce, einschließlich der [Adobe Commerce Help Center Support Knowledge Base (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), der [Adobe Commerce Developer Documentation (DevDocs)](https://developer.adobe.com/commerce/docs/), der [[!DNL Quality Patches Tool]: Suche nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, des [Sicherheitszentrums](https://helpx.adobe.com/security.html) und der [Beobachtung für Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Elemente

* **[!UICONTROL Recommendations]**: Zeigt Best Practices für Ihre Site an. Recommendations (gefundene Probleme und zu behebende Empfehlungen) werden nach Priorität sortiert - P0 (Kritisch) nach P4 (Benachrichtigung).
Recommendations umfasst Beschreibungen, Empfehlungen, Site-Auswirkungen, Stammursache, Szenarien/Vorbedingungen und verwendete Tools.

* **[!UICONTROL Upgrade Compatibility Tool]**: Prüft eine benutzerdefinierte Adobe Commerce-Instanz auf eine bestimmte Version, indem alle darin installierten Module und der darin installierte Core-Code analysiert werden. Es wird eine Liste kritischer Probleme, Fehler und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird. Außerdem werden potenzielle Probleme identifiziert, die in Ihrem Code behoben werden müssen, bevor ein Upgrade auf eine neuere Version von Adobe Commerce durchgeführt werden kann.
Mit dem [!UICONTROL Upgrade Compatibility Tool] können Sie erkennen, wann Änderungen am Kerncode an benutzerdefinierten Funktionen vorgenommen wurden.

* **[!UICONTROL Security Center Widget]**: Zeigt Einblicke in die Sicherheit Ihrer Site an.
Zu den angezeigten Sicherheitsinformationen gehören die [Tech [!DNL Stack] Versionskonformität mit [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Best Practice Security Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
Der [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) überwacht Adobe Commerce-Sites auf Sicherheitsrisiken. Es kann proaktiv und effizient Malware in Händlern erkennen und Händler darüber informieren, ob Sicherheitsrisiken, Malware oder Bedrohungen bestehen, und fehlende Adobe Commerce-Patches und -Updates identifizieren.

* **[!UICONTROL Extensions]**: Zeigt die derzeit auf Ihrer Adobe Commerce-Instanz installierten Erweiterungen an. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) -Informationen werden, soweit verfügbar, für die dort aufgeführten Erweiterungen bereitgestellt.

* **[!UICONTROL Alerts]**: Zeigt die neueste [!DNL New Relic Managed Alerts] für die Adobe Commerce-Instanz an. Weitere Informationen zu [verwalteten Warnhinweisen für Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) und zum [Zugriff auf New Relic-Dienste](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) finden Sie in der Knowledge Base des Adobe Commerce-Supports.

* **[!UICONTROL Non-recommended software in use]**: Zeigt die nicht empfohlene Software an, die Ihre Adobe Commerce-Instanz derzeit verwendet, basierend auf Ihrer Adobe Commerce-Version. Die nicht empfohlene Software wird von [!UICONTROL Name], [!UICONTROL Installed Version] und [!UICONTROL Recommended Version] aufgelistet.

* **[!UICONTROL Recommended Patches]**: Zeigt eine kurze Liste aller empfohlenen Patches an, die sowohl auf bereits installierten Patches als auch auf Ihrer Adobe Commerce-Version basieren. Die vollständige Liste der empfohlenen Patches finden Sie auf der Registerkarte mit den **[!UICONTROL Patches]**-Funktionen, die sich ebenfalls innerhalb des [!DNL Site-Wide Analysis Tool] befindet. Die Patches werden von [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"} bereitgestellt. Alle aufgelisteten Patches sind mit Ihrer aktuellen Adobe Commerce-Instanz kompatibel.
Wenn es keine empfohlenen Patches für Ihre Adobe Commerce-Instanz gibt, wird dieser [!DNL widget] angezeigt, **[!UICONTROL No Recommended Patches]**.

## Verwendungsbereiche

Die Seite &quot;**[!UICONTROL Dashboard]**&quot; ist Ihr allgegenwärtiges Kommandozentrum in der &quot;[!DNL Site-Wide Analysis Tool]&quot;, um nicht nur einfach das &quot;große Bild&quot;des gesamten Zustands Ihrer Site anzuzeigen, sondern Sie können auch spezifische Tools, Empfehlungen und Berichte für Ihre Adobe Commerce-Website über jeden Abschnitt &quot;[!DNL widget]&quot;anzeigen und darauf zugreifen.

## Vorteile

* Die [!DNL widgets] für [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions] und [!UICONTROL Security Scan] verwenden alle einfach zu lesende, farbcodierte interaktive Kreisdiagramme mit Diagrammlegenden an der Seite und zählen die Summen in der Mitte, um anzugeben, wie viele [!UICONTROL Recommendations], [!UICONTROL Extensions] und [!UICONTROL Security Scan Tool] Elemente jede Funktion hat. Die Diagramme [!UICONTROL Recommendations] und [!UICONTROL Security Scan Tool] sind durch den Schweregrad getrennt. [!UICONTROL Extensions] sind in vier Klassifizierungen unterteilt: aktuelle Version, alte Version, deaktiviert und unbekannt.

* [!DNL New Relic Alerts] werden mit dem neuesten Warnhinweis oben aufgeführt, einschließlich einer kurzen Beschreibung und der Dauer des Vorgangs.

* Die [!UICONTROL Recommendations] und [!UICONTROL Extensions] [!DNL widgets] haben Zugriff auf die vollständige Seite der Daten für jede Funktion, indem sie auf **[!UICONTROL View All]** klicken.

* Die [!UICONTROL Security Scan Tool] hat einen **[!UICONTROL View Report]** -Link im Fenster [!DNL widget] , der Sie zur Seite [!UICONTROL Recommendations] führt.

* Die [!DNL Upgrade Compatibility Tool] hat eine **[!UICONTROL Run Upgrade Scan]** -Schaltfläche im [!DNL widget] -Fenster.

## Best Practices für die Verwendung von [!UICONTROL Dashboard]

* Klicken Sie auf die einzelnen [!DNL widget] , um auf die detaillierten Daten zuzugreifen, damit Sie Einblicke in die Sicherheit, den Gesundheitszustand, die Empfehlungen und die Best Practices Ihrer Website erhalten und diese verbessern können.

* Wechseln Sie zu [!UICONTROL Security Scan Tool] [!DNL widget] und klicken Sie auf [!UICONTROL View Report] , um einen [!UICONTROL Recommendations] -Bericht für Ihre Site anzuzeigen.

* Verwenden Sie die Links &quot;[!DNL External Resources]&quot;, um weitere Informationen zu erhalten, über Sicherheits-Patches, Aktualisierungen und Best Practices auf dem Laufenden zu bleiben oder die Einblicke der Support-Wissensdatenbank für das Adobe Commerce Help Center (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), der [Adobe Commerce Developer Documentation (DevDocs)](https://developer.adobe.com/commerce/docs/), der [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, des [Sicherheitszentrums](https://helpx.adobe.com/security.html) und 10}Beobachtung für Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).[[
