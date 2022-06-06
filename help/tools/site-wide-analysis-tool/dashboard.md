---
title: '"[!DNL Dashboard]"'
description: Erfahren Sie mehr über die [!DNL Dashboard] im [!DNL Site-Wide Analysis Tool], -Elemente, Verwendungszeitpunkt, Vorteile und Best Practices.
source-git-commit: 87a8d411de32f051037ade5ecc90aaa709a54e82
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

Die [!UICONTROL Dashboard] Seite zeigt einen Überblick [!DNL widgets] , die eine &quot;Einzelne Glasansicht&quot;des Gesundheitszustands und des aktuellen Status Ihrer Adobe Commerce-Website bieten. Diese [!DNL widgets] enthalten jeweils einen Link zum Zugriff auf die Seite der einzelnen Funktionen, zu jedem Tool selbst oder zu Berichten (je nach [!DNL widget]).
Es gibt auch eine Liste von [!UICONTROL External Resources] Links für Adobe Commerce, einschließlich der [Support-Info-Center für Adobe Commerce (Help Center)](https://support.magento.com/), [Adobe Commerce-Entwicklerdokumentation (DevDocs)](https://devdocs.magento.com/), [Werkzeug für Qualitätsmuster](https://devdocs.magento.com/quality-patches/tool.html#patch-grid), [Sicherheitszentrum](https://magento.com/security)und [Beobachtung für Adobe Commerce (OAC)](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).

## Elemente

* **[!UICONTROL Recommendations]**: Zeigt Best Practices für Ihre Site an. Recommendations (gefundene Probleme und zu behebende Empfehlungen) werden nach Priorität sortiert - P0 (Kritisch) nach P4 (Benachrichtigung).
Recommendations umfasst Beschreibungen, Empfehlungen, Site-Auswirkungen, Stammursache, Szenarien/Vorbedingungen und verwendete Tools.

* **[!UICONTROL Upgrade Compatibility Tool]**: Überprüft eine benutzerdefinierte Adobe Commerce-Instanz auf eine bestimmte Version, indem alle darin installierten Module und der darin installierte Core-Code analysiert werden. Es wird eine Liste kritischer Probleme, Fehler und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird. Außerdem werden potenzielle Probleme identifiziert, die in Ihrem Code behoben werden müssen, bevor ein Upgrade auf eine neuere Version von Adobe Commerce durchgeführt werden kann.
Die [!UICONTROL Upgrade Compatibility Tool] können Sie erkennen, wann Änderungen am Kerncode an benutzerdefinierten Funktionen vorgenommen wurden.

* **[!UICONTROL Security Scan Tool]**: Überwachen von Adobe Commerce-Sites auf Sicherheitsrisiken. Es kann proaktiv und effizient Malware in Händlern erkennen und Händler darüber informieren, ob Sicherheitsrisiken, Malware oder Bedrohungen bestehen, und fehlende Adobe Commerce-Patches und -Updates identifizieren.

* **[!UICONTROL Extensions]**: Zeigt die derzeit auf Ihrer Adobe Commerce-Instanz installierten Erweiterungen an. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) soweit verfügbar, werden Informationen für die dort aufgeführten Erweiterungen bereitgestellt.

* **[!UICONTROL Alerts]**: Zeigt die neueste [!DNL New Relic Managed Alerts] für die Adobe Commerce-Instanz. Weitere Informationen [Verwaltete Warnhinweise für Adobe Commerce](https://support.magento.com/hc/en-us/articles/360045806832) und wie [Zugriff auf neue relationale Dienste](https://support.magento.com/hc/en-us/articles/360039127712) in der Wissensdatenbank der Adobe Commerce-Support.

* **[!UICONTROL Non-recommended software in use]**: Zeigt die nicht empfohlene Software an, die Ihre Adobe Commerce-Instanz derzeit verwendet. Diese basiert auf Ihrer Adobe Commerce-Version. Die nicht empfohlene Software wird von [!UICONTROL Name], [!UICONTROL Installed Version]und [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Zeigt eine kurze Liste aller empfohlenen Patches auf der Basis von Patches an, die Sie bereits installiert haben, und der Adobe Commerce-Version. Die vollständige Liste der empfohlenen Patches finden Sie im **[!UICONTROL Patches]** Registerkarte &quot;Funktion&quot;, die sich ebenfalls im [!DNL Site-Wide Analysis Tool]. Die Patches werden von der [Werkzeug für Qualitätsmuster](https://devdocs.magento.com/quality-patches/tool.html). Alle aufgelisteten Patches sind mit Ihrer aktuellen Adobe Commerce-Instanz kompatibel.
Wenn es keine empfohlenen Patches für Ihre Adobe Commerce-Instanz gibt, wird dies [!DNL widget] wird angezeigt, **[!UICONTROL No Recommended Patches]**.

## Verwendungsbereiche

Die **[!UICONTROL Dashboard]** Seite ist Ihr naheliegendes Befehlszentrum im [!DNL Site-Wide Analysis Tool] , um nicht nur einfach das &quot;große Bild&quot;der Gesundheit Ihrer Site als Ganzes anzuzeigen, sondern auch spezifische Tools, Empfehlungen und Berichte für Ihre Adobe Commerce-Website zu sehen und darauf zuzugreifen. [!DNL widget].

## Vorteile

* Die [!DNL widgets] für [!UICONTROL Recommendations], [!UICONTROL Extensions]und [!UICONTROL Security Scan] Alle verwenden einfach zu lesende, farbcodierte interaktive Kreisdiagramme mit Diagrammlegenden an der Seite und zählen die Summen in der Mitte, um anzugeben, wie viele [!UICONTROL Recommendations], [!UICONTROL Extensions]und [!UICONTROL Security Scan Tool] Elemente, die jede Funktion enthält. [!UICONTROL Recommendations] und [!UICONTROL Security Scan Tool] -Diagramme sind durch Schweregrad getrennt. [!UICONTROL Extensions] werden in vier Klassifizierungen unterteilt: aktuelle Version, alte Version, deaktiviert und unbekannt.

* [!DNL New Relic Alerts] werden mit dem neuesten Warnhinweis oben aufgelistet, einschließlich einer kurzen Beschreibung und der Dauer des Warnhinweises.

* Die [!UICONTROL Recommendations] und [!UICONTROL Extensions] [!DNL widgets] Zugriff auf die vollständige Seite der Daten für jede Funktion erhalten, indem Sie auf **[!UICONTROL View All]**.

* Die [!UICONTROL Security Scan Tool] hat eine **[!UICONTROL View Report]** im [!DNL widget] Fenster, das Sie zum [!UICONTROL Recommendations] Seite.

* Die [!DNL Upgrade Compatibility Tool] hat eine **[!UICONTROL Run Upgrade Scan]** im [!DNL widget] Fenster.

## Best Practices für die Verwendung der [!UICONTROL Dashboard]

* Klicken Sie auf jeden [!DNL widget] , um auf die detaillierten Daten zuzugreifen, die es bietet, um Einblicke in die Gesundheit, Empfehlungen und Best Practices Ihrer Website zu erhalten und diese zu verbessern.

* Navigieren Sie zu [!UICONTROL Security Scan Tool] [!DNL widget] und klicken Sie auf [!UICONTROL View Report] zum Anzeigen einer [!UICONTROL Recommendations] Berichte für Ihre Site erstellen.

* Verwenden Sie die [!DNL External Resources] Links, über die Sie entweder mehr Informationen erfahren, aktuelle Informationen zu Sicherheits-Patches, -Updates und -Best Practices erhalten oder die Vorteile der [Support-Info-Center für Adobe Commerce (Help Center)](https://support.magento.com/), [Adobe Commerce-Entwicklerdokumentation (DevDocs)](https://devdocs.magento.com/), [Werkzeug für Qualitätsmuster](https://devdocs.magento.com/quality-patches/tool.html#patch-grid), [Sicherheitszentrum](https://helpx.adobe.com/security.html)und [Beobachtung für Adobe Commerce (OAC)](https://support.magento.com/hc/en-us/articles/4402379845901-Use-Observation-for-Adobe-Commerce).