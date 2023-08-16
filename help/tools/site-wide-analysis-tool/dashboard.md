---
title: '[!DNL Dashboard]'
description: Informationen zum [!DNL Dashboard] im [!DNL Site-Wide Analysis Tool], -Elemente, Verwendungszeitpunkt, Vorteile und Best Practices.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

Die [!UICONTROL Dashboard] Seite zeigt einen Überblick [!DNL widgets] , die eine &quot;Einzelne Glasansicht&quot;des Gesundheitszustands und des aktuellen Status Ihrer Adobe Commerce-Website bieten. Jeder [!DNL widget] enthält einen Link zum Zugriff auf die Seite jeder Funktion, zu jedem Tool selbst oder zu Berichten (je nach [!DNL widget]).
Es gibt auch eine Liste von [!UICONTROL External Resources] Links für Adobe Commerce, einschließlich der [Support-Info-Center für Adobe Commerce (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce-Entwicklerdokumentation (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Sicherheitszentrum](https://helpx.adobe.com/security.html), und [Beobachtung für Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Elemente

* **[!UICONTROL Recommendations]**: Zeigt Best Practices für Ihre Site an. Recommendations (gefundene Probleme und zu behebende Empfehlungen) werden nach Priorität sortiert - P0 (Kritisch) nach P4 (Benachrichtigung).
Recommendations umfasst Beschreibungen, Empfehlungen, Site-Auswirkungen, Stammursache, Szenarien/Vorbedingungen und verwendete Tools.

* **[!UICONTROL Upgrade Compatibility Tool]**: Prüft eine benutzerdefinierte Adobe Commerce-Instanz auf eine bestimmte Version, indem alle darin installierten Module und der darin installierte Core-Code analysiert werden. Es wird eine Liste kritischer Probleme, Fehler und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird. Außerdem werden potenzielle Probleme identifiziert, die in Ihrem Code behoben werden müssen, bevor ein Upgrade auf eine neuere Version von Adobe Commerce durchgeführt werden kann.
Die [!UICONTROL Upgrade Compatibility Tool] können Sie erkennen, wann Änderungen am Kerncode an benutzerdefinierten Funktionen vorgenommen wurden.

* **[!UICONTROL Security Center Widget]**: Zeigt Einblicke in die Sicherheit Ihrer Site an.
Zu den angezeigten Sicherheitsinformationen gehören [Tech [!DNL Stack] Versionskonformität [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Best Practice Security Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
Die [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) überwacht Adobe Commerce-Sites auf Sicherheitsrisiken. Es kann proaktiv und effizient Malware in Händlern erkennen und Händler darüber informieren, ob Sicherheitsrisiken, Malware oder Bedrohungen bestehen, und fehlende Adobe Commerce-Patches und -Updates identifizieren.

* **[!UICONTROL Extensions]**: Zeigt die derzeit auf Ihrer Adobe Commerce-Instanz installierten Erweiterungen an. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) soweit verfügbar, werden Informationen für die dort aufgeführten Erweiterungen bereitgestellt.

* **[!UICONTROL Alerts]**: Zeigt die neueste Version an [!DNL New Relic Managed Alerts] für die Adobe Commerce-Instanz. Weitere Informationen [Verwaltete Warnhinweise für Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) und wie [Zugriff auf New Relic-Dienste](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) in der Wissensdatenbank der Adobe Commerce-Support.

* **[!UICONTROL Non-recommended software in use]**: Zeigt die nicht empfohlene Software an, die Ihre Adobe Commerce-Instanz derzeit verwendet. Diese basiert auf Ihrer Adobe Commerce-Version. Die nicht empfohlene Software wird von [!UICONTROL Name], [!UICONTROL Installed Version], und [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Zeigt eine kurze Liste aller empfohlenen Patches an, die auf beiden Patches basieren, die Sie möglicherweise bereits installiert haben, sowie auf Ihrer Adobe Commerce-Version. Die vollständige Liste der empfohlenen Patches finden Sie im **[!UICONTROL Patches]** Registerkarte &quot;Funktion&quot;, die sich ebenfalls im [!DNL Site-Wide Analysis Tool]. Die Patches werden von der [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Alle aufgelisteten Patches sind mit Ihrer aktuellen Adobe Commerce-Instanz kompatibel.
Wenn es keine empfohlenen Patches für Ihre Adobe Commerce-Instanz gibt, wird dies [!DNL widget] wird angezeigt, **[!UICONTROL No Recommended Patches]**.

## Verwendungsbereiche

Die **[!UICONTROL Dashboard]** Seite ist Ihr naheliegendes Befehlszentrum im [!DNL Site-Wide Analysis Tool] , um nicht nur einfach das &quot;Gesamtbild&quot;der Gesundheit Ihrer Site als Ganzes anzuzeigen, sondern Sie können auch spezifische Tools, Empfehlungen und Berichte für Ihre Adobe Commerce-Website durch jede [!DNL widget].

## Vorteile

* Die [!DNL widgets] für [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions], und [!UICONTROL Security Scan] Alle verwenden einfach zu lesende, farbcodierte interaktive Kreisdiagramme mit Diagrammlegenden an der Seite und zählen die Summen in der Mitte, um anzugeben, wie viele [!UICONTROL Recommendations], [!UICONTROL Extensions], und [!UICONTROL Security Scan Tool] Elemente, die jede Funktion enthält. [!UICONTROL Recommendations] und [!UICONTROL Security Scan Tool] -Diagramme sind durch Schweregrad getrennt. [!UICONTROL Extensions] sind in vier Klassifizierungen unterteilt: aktuelle Version, alte Version, deaktiviert und unbekannt.

* [!DNL New Relic Alerts] werden mit dem neuesten Warnhinweis oben aufgelistet, einschließlich einer kurzen Beschreibung und der Dauer des Warnhinweises.

* Die [!UICONTROL Recommendations] und [!UICONTROL Extensions] [!DNL widgets] Zugriff auf die vollständige Seite der Daten für jede Funktion erhalten, indem Sie auf **[!UICONTROL View All]**.

* Die [!UICONTROL Security Scan Tool] hat eine **[!UICONTROL View Report]** -Link in [!DNL widget] Fenster, das Sie zum [!UICONTROL Recommendations] Seite.

* Die [!DNL Upgrade Compatibility Tool] hat eine **[!UICONTROL Run Upgrade Scan]** im [!DNL widget] Fenster.

## Best Practices für die Verwendung der [!UICONTROL Dashboard]

* Klicken Sie auf jeden [!DNL widget] , um auf die detaillierten Daten zuzugreifen, die es bietet, um Einblicke in die Sicherheit, den Gesundheitszustand, Empfehlungen und Best Practices Ihrer Website zu erhalten und diese zu verbessern.

* Navigieren Sie zu [!UICONTROL Security Scan Tool] [!DNL widget] und klicken [!UICONTROL View Report] zum Anzeigen einer [!UICONTROL Recommendations] Berichte für Ihre Site erstellen.

* Verwenden Sie die [!DNL External Resources] Links, über die Sie entweder mehr Informationen erfahren, aktuelle Informationen zu Sicherheits-Patches, -Updates und -Best Practices erhalten oder die Vorteile der [Support-Info-Center für Adobe Commerce (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce-Entwicklerdokumentation (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Suchen Sie nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Sicherheitszentrum](https://helpx.adobe.com/security.html), und [Beobachtung für Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
