---
title: Registerkarte [!UICONTROL bots]
description: Erfahren Sie mehr über die Registerkarte [!UICONTROL bots] von  [!DNL Observation for Adobe Commerce].
exl-id: 741310ca-28fb-4b08-95c7-e8d1fb952018
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1905'
ht-degree: 0%

---

# Registerkarte [!UICONTROL bots]

Diese Registerkarte enthält Informationen, die erklären, wie Sie erkennen können, ob und was [!DNL bots] Site-Probleme verursacht.

## Allgemeine Übersicht über [!DNL bots]:

* Ein [!DNL bot] ist eine Software, die sich wiederholende automatisierte Aufgaben ausführt. Mit künstlicher Intelligenz und Evolution des maschinellen Lernens ändern sich die Aufgaben, Methoden und Interaktionen von [!DNL bots]. Es gibt *gute* [!DNL bots], die Websites durch Crawling und Hinzufügen zu Internetsuchmaschinen nutzen. Dies führt dazu, dass Internetnutzer durch Suchmaschinenergebnisse zur Site geleitet werden. Eine *gute* [!DNL bot] berücksichtigt in der Regel die auf der [!DNL bot] platzierten Grenzen durch eine `robots.txt`-Datei oder Einstellungen in einer Suchmaschinenkonsole. Grenzen können den Zugriff auf die Site oder Teile davon einschränken.
* &#39;bösartig&#39; [!DNL bots] ignoriert die `robots.txt`-Datei, oder sie können eine gute [!DNL bot] über das Feld für den Anforderungs-Benutzeragenten der HTTP-Anfragedaten verdorben. Einige Dinge, die böswillig [!DNL bots] tun:
   * Fügen Sie einer Site Ladevorgänge hinzu, um legitimen Benutzern den Zugriff auf die Site zu verweigern.
   * Inhalte ohne Berechtigung erstellen und wiederverwenden.
   * Registrieren Sie gefälschte Konten, um E-Mail-Dienste oder -Adressen zu überschwemmen oder auf andere Sites umzuleiten ([!DNL SPAM bots]).
   * Erstellen Sie falsche Ansichten ([!DNL Viewbots]).
   * Produkte oder Tickets kaufen ([!DNL Focused bots]).
* Verwalten von [!DNL bots]
   * [!DNL Observation for Adobe Commerce] hat Ansichten von [!DNL bot] Traffic:
      * Er zeigt die gesamte nicht zwischengespeicherte [!DNL bot] -Aktivität an, die die Last anzeigt, die ein [!DNL bot] einer Site hinzufügt, und wenn dieses Laden stattfindet.
      * Er zeigt die [!DNL bots] an, die Fehler erzeugen. Wenn ein [!DNL bot] für gewöhnlich eine Last hinzufügt, die Site-Probleme verursacht, weist diese [!DNL bot] oder IP-Adresse die höchste Fehlerhäufigkeit auf.
      * Es werden [!DNL bot] Namen (Benutzeragenten-Feldwerte anfordern) und IP-Adressen angezeigt, die wie folgt verwaltet werden können:
         * [!DNL Fastly] (Ratenbegrenzung oder [!DNL VCLs], die IP-Adressen, Bereiche oder [!DNL bots] nach Namenswert blockieren).
         * Hinzufügen guter [!DNL bot] Informationen zum `robots.txt field`, um die Rate des Site-Zugriffs zu beschränken oder zu begrenzen.
         * Verwalten von [!DNL Bing] oder [!DNL Google bots] über die Suchmaschinenkonsole.

## [!UICONTROL Experimental Potential Malicious Bots frame]

![ Experimentelle potenzielle bösartige Bots frame](../../assets/tools/observation-for-adobe-commerce/experimental-potential-malicious-bots-frame-new.jpg)

Der Frame **[!UICONTROL Experimental Potential Malicious Bots frame]** umfasst 12 separate, komplexe Abfragen. Er erkennt böswillige IP-Anforderungssignaturen und aggregiert dann die Ergebnisse, fasst sie zusammen und sortiert sie nach Anzahl in absteigender Reihenfolge. Die Abfragen enthalten eine Vielzahl von Datensignaturen von CVE-Exploits und anderen böswilligen Anfragen. Selbst wenn die Exploits durch Sicherheitskorrekturen/Patches blockiert werden und keine Bedrohung für die Site darstellen, muss die Anfrage noch von der Website bearbeitet werden. Das Volumen der Anfragen kann in kurzer Zeit sehr bedeutend werden. In diesem Frame werden nicht die Gesamtanforderungen der IP-Adresse angezeigt, sondern Anforderungen, die Signale enthalten, die darauf hinweisen, dass die Anfrage eine verdächtige Absicht hatte.

Stellen Sie sicher, dass der Traffic verdächtig ist und nicht von einer [!DNL Content Distributed Network] -Adresse (CDN) stammt, die möglicherweise auch gültige Anfragen sendet. Wenn festgestellt wird, dass die Anfragen von einer CDN-IP-Adresse stammen, wenden Sie sich an diesen Dienstanbieter, um bei der Blockierung des verdächtigen Traffics über sein Netzwerk zu helfen. Informationen zum Blockieren der Adresse oder der Anforderungs-URL finden Sie unter [Blockieren von böswilligem Traffic für Adobe Commerce auf  [!DNL Fastly] Ebene](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level.html) in der Knowledge Base des Adobe Commerce-Supports.

## [!UICONTROL Rate of HTTP request per second (top 25) during requested time period]

![Rate der HTTP-Anforderung pro Sekunde (Top 25) während des angeforderten Zeitraums](../../assets/tools/observation-for-adobe-commerce/rate-of-http-request-per-second.jpg)

Der Frame **[!UICONTROL Rate of HTTP request per second (top 25) during requested time period]** zeigt die höchsten Anforderungen pro Sekunde für IP-Adressen im ausgewählten Zeitraum an. Wenn diese Adressen auch in der obigen Tabelle aufgeführt sind, stellen Sie sicher, dass sie keine CDN-Adressen und böswillig sind, und blockieren Sie sie über [!DNL Fastly].

## [!UICONTROL Total Bot traffic by bot name]:

![Bot-Traffic insgesamt nach Bot-Namen während des ausgewählten Zeitraums:](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

Die Tabelle **[!UICONTROL Total Bot traffic by bot name during selected time period]** enthält die aggregierte Anzahl nicht zwischengespeicherter Anforderungen, wobei das Feld [!UICONTROL request_user_agent] im Wert eine Zeichenfolge von [!DNL bots] enthält. Dies kann der Name [!DNL bot] sein oder auch nicht, da der Feldwert [!UICONTROL request_user_agent] gespoolt werden kann. Der Wert unter der Spalte [!UICONTROL Count] ist der wichtigste.

## [!UICONTROL Total Bot Traffic by Bot name/IP address]

![Bot-Traffic insgesamt nach Bot-Name/IP-Adresse während des ausgewählten Zeitraums Wie blockiert man Bot-Traffic auf schneller Ebene ODER verwaltet Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce-Roboter.txt](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

Die Tabelle &quot;**[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]**&quot; zeigt dieselben Daten wie die vorherige Tabelle, fügt jedoch IP-Adressen hinzu, die die Anfragen im Namen des [!DNL bot] senden. Als böswilliger [!DNL bots]-Spoof-Gut [!DNL bots] sollten die IP-Adressen über Websites überprüft werden, die missbräuchliche IP-Adressen identifizieren, oder über *whois*-Dienste oder [!DNL DNS lookups]. Beispielsweise veröffentlicht [!DNL Google] ihre [[!DNL googlebot] IP-Adressen](https://developers.google.com/search/apis/ipranges/googlebot.json) und [!DNL Microsoft] verfügt über ein Verifizierungstool für [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f).

## [!UICONTROL Graph - Bots with HTTP status errors]

![Diagramm - Bots mit HTTP-Statusfehlern während des ausgewählten Zeitraums Wie blockiert man Bot-Traffic auf der schnellsten Ebene ODER verwaltet Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce-Roboter.txt](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

Das Diagramm **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** zeigt Fehler in [!DNL bots] an, die sich im Feld &quot;Anfrage-Benutzeragent&quot;deklarieren. Dies bedeutet nicht unbedingt, dass der Fehler durch das Volumen des [!DNL bot] - oder anderen Traffics verursacht wird. Fehler können sein, dass der [!DNL bot] nicht vorhandene Informationen anfordert oder dass in der Anfrage ein anderes Problem vorliegt.

Wenn es zu einem Anstieg von Fehlern bei IP-Adressen während Instabilität oder Ausfall der Site kommt, kann es sich um Verdächtige im Site-Problem handeln.

## [!UICONTROL Table - IPs that do not identify as bots]

![Tabelle - IPs, die während des ausgewählten Zeitraums nicht als Bots mit HTTP-Statusfehlern identifizieren Wie blockiert man Bot-Traffic auf schneller Ebene ODER verwaltet Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce-Roboter.txt ](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png)

In der Tabelle &quot;**[!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]**&quot; werden IP-Anfragen mit HTTP-Status-Codes angezeigt, die nicht 200 sind und sich NICHT als [!DNL bots] im Feld &quot;Anfrage-Benutzeragent&quot;identifizieren. Diese IP-Adressen können böswillige IP-Adressen sein, insbesondere wenn die Zahlen für den ausgewählten Zeitraum hoch sind.

Wenn die Anzahl der HTTP-Status-Codes ungleich 200 ist und die IP-Adressbereiche nicht ähnlich sind, tragen die Adressen möglicherweise nicht zu den Site-Problemen bei.

## [!UICONTROL Table – Cache Status 'ERROR']

![Tabelle - Detailtabelle &quot;Cache Status &#39;ERROR&#39;&quot;(was machen diese IPs?) Blocken des Bot-Traffics auf der schnellsten Ebene ODER Verwalten von Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce-Roboter.txt](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

Wenn IP-Adressen eine hohe Fehlerrate erzeugen, fragen Sie, was sie tun. Die Tabelle **[!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** zeigt die angeforderte URL zusammen mit dem HTTP-Statuswert für Anfragen mit dem Cache-Status-Wert [!UICONTROL ERROR] an. Die Häufigkeit wird durch URL erfasst, sodass die Anzahl gering sein kann. Beachten Sie, dass die IP-Adresse im ausgewählten Zeitraum möglicherweise Tausende von Anfragen stellt. Dies ist eine Ansicht für bis zu 2000 Anfragen während des Zeitrahmens (Anzeigelimit für Datensätze).

## [!UICONTROL Show 5XX status distribution]

![Anzeigen der 5XX-Statusverteilung über IP-Adressen (die 200 wichtigsten Adressen) Anleitung zum Blockieren des Bot-Traffics auf schneller Ebene ODER zum Verwalten von Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce-Roboter.txt ](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

Der **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]**-Frame ist leistungsstark. Es werden die IP-Adressen angezeigt, die während des ausgewählten Zeitraums über 50 HTTP-Status-Codes verfügen. Wenn eine IP-Adresse eine hohe Anzahl von Anfragen sendet und die Site so stark beeinflusst wird, dass sie den Traffic nicht verarbeiten kann, haben die IP-Adressen, die die höchste Häufigkeit von Anfragen stellen, in der Regel das höchste Fehlervolumen. 5XX HTTP-Status-Codes zeigen normalerweise eine Site an, die Schwierigkeiten hat, auf Anfragen zu reagieren.

Je größer der Balken, desto größer ist der prozentuale Anteil der Fehler, die die IP-Adresse in der Gesamtzahl der 5xx-Fehler während dieses Zeitraums aufweist. Hinweis: Eine IP-Adresse kann mehrere Segmente im Diagramm enthalten, wenn sie mehrere HTTP-Status-Codes aufweist (z. B. HTTP-Status 502 und 503).

Die typische Verteilung wird rechts in der Leiste angezeigt, wo die IP-Adressen die gleiche Breite aufweisen, oder es gibt einige breite Balken mit sehr niedrigen Zahlen.

Wenn Sie den Mauszeiger über das Balkensegment bewegen, wird die Anzahl der angegebenen Fehler im ausgewählten Zeitraum angezeigt.

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status]

![IP-Cache-Status (MISS, PASS, ERROR) und HTTP-Status während des ausgewählten Zeitraums Wie blockiert man Bot-Traffic auf schneller Ebene ODER verwaltet Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce-Roboter.txt](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

Dieser **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** -Frame zeigt die Anzahl der HTTPS-Status-Codes und nicht zwischengespeicherten Anforderungen nach IP im ausgewählten Zeitraum. Dies zeigt die proportionale Belastung jeder IP-Adresse und das Gesamtvolumen an. Sie zeigt die IP-Adressen mit den meisten Anforderungen an.

## [!UICONTROL Fastly Cache Summary for selected time period]

![Schneller Cache-Überblick für den ausgewählten Zeitraum](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

Wenn Sie im unten stehenden Diagramm auf das Symbol [!UICONTROL Error] klicken, können Sie die letzten beiden Diagramme miteinander vergleichen. Dies kann dabei helfen anzugeben, wo die Belastung zu Site-Problemen beiträgt.

![Prüfung eines schnellen Fehlers](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots]

![IPs, die sich während des ausgewählten Zeitraums nicht als Bots ohne Fehler identifizieren wie Bot-Traffic auf schneller Ebene blockieren ODER Bots über Ihre robots.txt-Datei verwalten Best Practices für Adobe Commerce-Roboter.txt](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

Der Frame **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** zeigt das Feld für den Anforderungs-Benutzeragenten, die IP-Adresse und den Statuscode für Anfragen, bei denen das Feld für den Anforderungs-Benutzeragenten keine [!DNL bot] angibt. Dieser Frame kann Anforderungen mit hoher Häufigkeit von beliebigen IP-Adressen anzeigen, aber achten Sie auf Anforderungen mit hoher Häufigkeit, insbesondere in einem Zeitraum, in dem die Site Probleme haben kann.

## [!UICONTROL Graph - Suspicious Non-Bot traffic]

![Verdächtiger Nicht-Bot-Traffic während des ausgewählten Zeitraums](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

Das Diagramm **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** sucht nach einem Benutzeragenten-Wert für die Anfrage von Go-http-client, wird jedoch erweitert, um andere verdächtige Werte für den Anforderungs-Benutzeragenten zu untersuchen. Dieser Benutzeragenten-Anforderungswert wird von Sites zum Herstellen einer Verbindung von Diensten verwendet und kann gültig sein, wird aber auch von böswilligen [!DNL bots] verwendet.

## [!UICONTROL Graph - Bot traffic by Bot name]

![Diagramm - Bot-Traffic nach Bot-Name während des ausgewählten Zeitraums)](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

Der Frame **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** zeigt dieselben Daten wie der Traffic von &quot;Bot insgesamt&quot;nach [!DNL Bot] Name während des ausgewählten Zeitraums oben auf der Registerkarte an. Sie zeigt die Daten über die Timeline an, damit Sie sehen können, wann die Anfragen der [!DNL bots] gestellt werden und wie sie verteilt sind.

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses]

![Top 250 Bot-Namen und IP-Adressen während des ausgewählten Zeitraums Wie blockiert man Bot-Traffic auf schneller Ebene ODER verwaltet Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce-Roboter.txt](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

Der Frame &quot;**[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]**&quot;zeigt dieselben Daten wie der Traffic insgesamt [!DNL Bot] nach Bot-Name/IP-Adresse während des ausgewählten Zeitraums oben auf der Registerkarte an. Sie zeigt die Daten über die Timeline an und facettiert sie nach IP-Adresse. Dies zeigt an, wann die Anfragen von [!DNL bots] gestellt werden, welche IP Anfragen sendet und welche Verteilung der Anfragen erfolgt.

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly)]

![Blockierter Bot-Name/IP-Adressen (im Handumdrehen) während des ausgewählten Zeitraums. Dieses Diagramm zeigt Bot-Traffic und IPs an, die einen 403 Forbidden HTTP Status Code](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png) zurückgegeben haben

Der Frame **[!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** zeigt den Bot-Namen und die IP-Adressen an, die blockiert sind. In diesem Diagramm sehen Sie, wie alle Anforderungen in [!DNL Fastly] in Zukunft blockiert werden.

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly)]

![Blockierter Nicht-Bot-Name/IP-Adressen (im Handumdrehen) während des ausgewählten Zeitraums. Dieses Diagramm zeigt Nicht-Bot-Traffic und IPs an, die einen 403 Forbidden HTTP Status Code ](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png) zurückgegeben haben

Der Frame **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** zeigt IP-Adressen an, die sich nicht als [!DNL bot] identifizieren, die durch [!DNL Fastly] blockiert wurden.

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![Diese Tabelle zeigt die Anzahl der Benutzeragenten pro IP-Adresse, die Anzahl der erfolgreichen, fehlgeschlagenen und blockierten Anfragen:](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

Böswillige [!DNL bots] verspottete oft andere [!DNL bots] durch den Wert des [!UICONTROL Request User Agent] -Felds. Diese Tabelle zeigt, wie viele eindeutige Werte die IP-Adresse in diesem Feld hat. Je höher der Wert im Feld [!UICONTROL Request User Agent] ist, desto verdächtiger ist die IP-Adresse.

## [!UICONTROL IP with non-200 status errors]

![IP mit Nicht-200-Statusfehlern - ohne 403-Status](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

Der Frame **[!UICONTROL IP with non-200 status errors – without 403 status]** zeigt die Verteilung über den ausgewählten Zeitraum von IP-Adressen mit anderen HTTP-Status-Codes als 200 an. Wenn Sie höhere Werte für eine einzelne IP-Adresse oder IP-Adressengruppe sehen, müssen diese weiter untersucht werden.

## [!UICONTROL IP with 403 status codes:]

![IP mit 403 Status-Codes:](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

Der Frame &quot;**[!UICONTROL IP with 403 status codes]**&quot;zeigt nicht zwischengespeicherte Anfragen ohne &quot;[!UICONTROL cache_status=ERROR]&quot;, die einen HTTP-Status von 403 aufweisen. Dies kann zeigen, dass der Ursprungs-Server die Quelle des 403 (nicht autorisiert) und nicht der Block von [!DNL Fastly] ist.

## [!UICONTROL Top 5 with non-200 status codes]

![Top 5 mit Statuscodes, die nicht 200 sind und cache_status anzeigen:](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

Die Tabelle **[!UICONTROL Top 5 with non-200 status codes showing cache_status]** zeigt auf IP-/Statusebene die Zählungen jedes einzelnen Objekts mit dem Wert [!UICONTROL cache_status] an.

## [!UICONTROL Pageview Latency will show as spikes]

![SeitenansichtLatenz wird als Spitzen in diesem Diagramm angezeigt:](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

Der Frame **[!UICONTROL Pageview Latency will show as spikes on this graph:]** zeigt die Latenz der Seitenladevorgänge/API-Antworten, die mit dem Traffic von [!DNL bot] übereinstimmen kann.
