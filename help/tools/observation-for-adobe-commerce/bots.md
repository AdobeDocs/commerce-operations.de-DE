---
title: Die [!UICONTROL bots] tab
description: Erfahren Sie mehr über die [!UICONTROL bots] Tab von [!DNL Observation for Adobe Commerce].
exl-id: 741310ca-28fb-4b08-95c7-e8d1fb952018
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1903'
ht-degree: 0%

---

# Die [!UICONTROL bots] tab

Diese Registerkarte enthält Informationen, die erklären, wie Sie feststellen können, ob und was [!DNL bots] verursacht Site-Probleme.

## Allgemeine Übersicht [!DNL bots]:

* A [!DNL bot] ist eine Software, die sich wiederholende automatisierte Aufgaben ausführt. Mit künstlicher Intelligenz und Evolution des maschinellen Lernens, den Aufgaben, Methoden und Interaktionen von [!DNL bots] sich ändern. Es gibt *good* [!DNL bots] , die Websites durch Crawling und das Hinzufügen zu Internet-Suchmaschinen begünstigen. Dies führt dazu, dass Internetnutzer durch Suchmaschinenergebnisse zur Site geleitet werden. A *good* [!DNL bot] berücksichtigt normalerweise die Begrenzungen, die auf der [!DNL bot] durch `robots.txt` -Datei oder -Einstellungen in einer Suchmaschinenkonsole. Grenzen können den Zugriff auf die Site oder Teile davon einschränken.
* bösartig [!DNL bots] ignorieren Sie die `robots.txt` Datei oder sie können eine gute [!DNL bot] über das Feld &quot;Request user agent&quot;der HTTP-Anfragedaten. Manche schädliche Dinge [!DNL bots] do:
   * Fügen Sie einer Site Ladevorgänge hinzu, um legitimen Benutzern den Zugriff auf die Site zu verweigern.
   * Inhalte ohne Berechtigung erstellen und wiederverwenden.
   * Registrieren Sie gefälschte Konten, um E-Mail-Dienste oder -Adressen zu überschwemmen oder auf andere Sites umzuleiten ([!DNL SPAM bots]).
   * Erstellen Sie falsche Ansichten ([!DNL Viewbots]).
   * Produkte oder Tickets kaufen ([!DNL Focused bots]).
* Verwalten [!DNL bots]
   * [!DNL Observation for Adobe Commerce] hat Ansichten zu [!DNL bot] Traffic:
      * Er zeigt die Gesamtzahl an, die nicht zwischengespeichert wurde [!DNL bot] -Aktivität, die die Last anzeigt, die ein [!DNL bot] fügt zu einer Site hinzu und wenn dieses Laden stattfindet.
      * Sie zeigt die [!DNL bots] die Fehler erzeugen. Wenn eine [!DNL bot] das Hinzufügen von Last, die Site-Probleme verursacht, dass [!DNL bot] oder die IP-Adresse die höchste Fehlerhäufigkeit hat.
      * Er zeigt [!DNL bot] Namen (Benutzeragenten-Feldwerte anfordern) und IP-Adressen, die wie folgt verwaltet werden sollen:
         * [!DNL Fastly] (Ratenbegrenzung oder [!DNL VCLs] IP-Adressen, -Bereiche oder [!DNL bots] nach Namenswert).
         * Gut hinzufügen [!DNL bot] Informationen `robots.txt field` die Geschwindigkeit des Site-Zugriffs zu beschränken oder zu begrenzen.
         * Verwalten [!DNL Bing] oder [!DNL Google bots] über die Suchmaschinenkonsole.

## [!UICONTROL Experimental Potential Malicious Bots frame]

![Experimentelles potenzielles bösartiges Bots-Frame](../../assets/tools/observation-for-adobe-commerce/experimental-potential-malicious-bots-frame-new.jpg)

Die **[!UICONTROL Experimental Potential Malicious Bots frame]** Der Frame umfasst 12 separate, komplexe Abfragen. Er erkennt böswillige IP-Anforderungssignaturen und aggregiert dann die Ergebnisse, fasst sie zusammen und sortiert sie nach Anzahl in absteigender Reihenfolge. Die Abfragen enthalten eine Vielzahl von Datensignaturen von CVE-Exploits und anderen böswilligen Anfragen. Selbst wenn die Exploits durch Sicherheitskorrekturen/Patches blockiert werden und keine Bedrohung für die Site darstellen, muss die Anfrage noch von der Website bearbeitet werden. Das Volumen der Anfragen kann in kurzer Zeit sehr bedeutend werden. In diesem Frame werden nicht die Gesamtanforderungen der IP-Adresse angezeigt, sondern Anforderungen, die Signale enthalten, die darauf hinweisen, dass die Anfrage eine verdächtige Absicht hatte.

Vergewissern Sie sich, dass der Traffic verdächtig ist und nicht von einem [!DNL Content Distributed Network] (CDN)-Adresse, die auch gültige Anfragen liefern kann. Wenn festgestellt wird, dass die Anfragen von einer CDN-IP-Adresse stammen, wenden Sie sich an diesen Dienstanbieter, um bei der Blockierung des verdächtigen Traffics über sein Netzwerk zu helfen. Informationen zum Blockieren der Adresse oder der Anforderungs-URL finden Sie unter [Blockieren von schädlichem Traffic für Adobe Commerce in [!DNL Fastly] level](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level.html) in der Knowledge Base zur Adobe Commerce-Unterstützung.

## [!UICONTROL Rate of HTTP request per second (top 25) during requested time period]

![Rate der HTTP-Anforderung pro Sekunde (Top 25) im angeforderten Zeitraum](../../assets/tools/observation-for-adobe-commerce/rate-of-http-request-per-second.jpg)

Die **[!UICONTROL Rate of HTTP request per second (top 25) during requested time period]** frame zeigt die höchsten Anforderungen pro Sekunde IP-Adressen während des ausgewählten Zeitraums an. Wenn sich diese Adressen auch in der obigen Tabelle befinden, stellen Sie sicher, dass sie keine CDN-Adressen und böswillig sind, und blockieren Sie sie über [!DNL Fastly].

## [!UICONTROL Total Bot traffic by bot name]:

![Bot-Traffic insgesamt nach Bot-Name im ausgewählten Zeitraum:](../../assets/tools/observation-for-adobe-commerce/total-bot-traffic-bot-name.png)

Die **[!UICONTROL Total Bot traffic by bot name during selected time period]** -Tabelle enthält die aggregierte Anzahl nicht zwischengespeicherter Anforderungen, wobei die [!UICONTROL request_user_agent] -Feld hat eine Zeichenfolge von [!DNL bots] im Wert. Dies kann der Name [!DNL bot] als [!UICONTROL request_user_agent] -Feldwert kann gespoolt werden. Der Wert unter dem [!UICONTROL Count] ist die wichtigste Spalte.

## [!UICONTROL Total Bot Traffic by Bot name/IP address]

![Bot-Traffic insgesamt nach Bot-Name/IP-Adresse während des ausgewählten Zeitraums Wie blockiert man Bot-Traffic auf schneller Ebene ODER verwaltet Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/best-practices-adobecommerce-robots.png)

Die **[!UICONTROL Total Bot Traffic by Bot name/IP address during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** zeigt dieselben Daten wie die vorherige Tabelle an, fügt jedoch IP-Adressen hinzu, die die Anfragen im Namen der [!DNL bot]. Als bösartig [!DNL bots] Gaumen [!DNL bots], sollten die IP-Adressen über Websites überprüft werden, die missbräuchliche IP-Adressen identifizieren, oder über *whois* Dienstleistungen oder [!DNL DNS lookups]. Beispiel: [!DNL Google] veröffentlicht die [[!DNL googlebot] IP-Adressen](https://developers.google.com/search/apis/ipranges/googlebot.json) und [!DNL Microsoft] verfügt über ein Überprüfungstool für [[!DNL Bingbots]](https://www.bing.com/webmasters/help/Verify-Bingbot-2195837f).

## [!UICONTROL Graph - Bots with HTTP status errors]

![Diagramm - Bots mit HTTP-Status-Fehlern während des ausgewählten Zeitraums Wie blockiert man den Bot-Traffic auf schneller Ebene ODER verwaltet Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/bots-with-http-status-errors.png)

Die **[!UICONTROL Graph - Bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** Diagramm zeigt Fehler an [!DNL bots] , die sich im Feld &quot;Request user agent&quot;deklarieren. Dies bedeutet nicht unbedingt, dass der Fehler durch das Volumen der [!DNL bot] oder anderen Traffic. Die Fehler könnten darin bestehen, dass die [!DNL bot] fordert Informationen an, die nicht vorhanden sind oder ein anderes Problem in der Anfrage besteht.

Wenn es zu einem Anstieg von Fehlern bei IP-Adressen während Instabilität oder Ausfall der Site kommt, kann es sich um Verdächtige im Site-Problem handeln.

## [!UICONTROL Table - IPs that do not identify as bots]

![Tabelle - IP-Adressen, die während des ausgewählten Zeitraums nicht als Bots mit HTTP-Statusfehlern identifizieren Anleitung zum Blockieren des Bot-Traffics auf der schnellsten Ebene ODER zum Verwalten von Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce robots.txt ](../../assets/tools/observation-for-adobe-commerce/ips-http-errors.png)

Die **[!UICONTROL Table - IPs that do not identify as bots with HTTP status errors during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** -Tabelle zeigt IP-Anfragen mit HTTP-Status-Codes, die nicht 200 sind und NICHT selbstidentifizieren, als [!DNL bots] im Feld &quot;Anfrage-Benutzeragent&quot;ein. Diese IP-Adressen können böswillige IP-Adressen sein, insbesondere wenn die Zahlen für den ausgewählten Zeitraum hoch sind.

Wenn die Anzahl der HTTP-Status-Codes ungleich 200 ist und die IP-Adressbereiche nicht ähnlich sind, tragen die Adressen möglicherweise nicht zu den Site-Problemen bei.

## [!UICONTROL Table – Cache Status 'ERROR']

![Tabelle - Detailtabelle &quot;Cache Status &#39;ERROR&#39;&quot;(was machen diese IPs?) Blocken des Bot-Traffics auf der schnellsten Ebene ODER Verwalten von Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce-Roboter.txt](../../assets/tools/observation-for-adobe-commerce/cache-status-errors.png)

Wenn IP-Adressen eine hohe Fehlerrate erzeugen, fragen Sie, was sie tun. Die **[!UICONTROL Table – Cache Status 'ERROR' detail table (what are these IPs doing?) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** zeigt die angeforderte URL zusammen mit dem HTTP-Statuswert für Anfragen mit einem Cache-Status an. [!UICONTROL ERROR] -Wert. Die Häufigkeit wird durch URL erfasst, sodass die Anzahl gering sein kann. Beachten Sie, dass die IP-Adresse im ausgewählten Zeitraum möglicherweise Tausende von Anfragen stellt. Dies ist eine Ansicht für bis zu 2000 Anfragen während des Zeitrahmens (Anzeigelimit für Datensätze).

## [!UICONTROL Show 5XX status distribution]

![5XX-Statusverteilung über IP-Adressen (die 200 wichtigsten Adressen) Blockieren des Bot-Traffics auf der schnellsten Ebene ODER Verwalten von Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce robots.txt ](../../assets/tools/observation-for-adobe-commerce/5xx-status.png)

Die **[!UICONTROL Show 5XX status distribution across IP addresses (top 200 addresses) How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** frame ist leistungsstark. Es werden die IP-Adressen angezeigt, die während des ausgewählten Zeitraums über 50 HTTP-Status-Codes verfügen. Wenn eine IP-Adresse eine hohe Anzahl von Anfragen sendet und die Site so stark beeinflusst wird, dass sie den Traffic nicht verarbeiten kann, haben die IP-Adressen, die die höchste Häufigkeit von Anfragen stellen, in der Regel das höchste Fehlervolumen. 5XX HTTP-Status-Codes zeigen normalerweise eine Site an, die Schwierigkeiten hat, auf Anfragen zu reagieren.

Je größer der Balken, desto größer ist der prozentuale Anteil der Fehler, die die IP-Adresse in der Gesamtzahl der 5xx-Fehler während dieses Zeitraums aufweist. Hinweis: Eine IP-Adresse kann mehrere Segmente im Diagramm enthalten, wenn sie mehrere HTTP-Status-Codes (z. B. 502- und 503-HTTP-Status) aufweist.

Die typische Verteilung wird rechts in der Leiste angezeigt, wo die IP-Adressen die gleiche Breite aufweisen, oder es gibt einige breite Balken mit sehr niedrigen Zahlen.

Wenn Sie den Mauszeiger über das Balkensegment bewegen, wird die Anzahl der angegebenen Fehler im ausgewählten Zeitraum angezeigt.

## [!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status]

![IP-Cache-Status (MISS, PASS, ERROR) und HTTP-Status während des ausgewählten Zeitraums Wie blockiert man Bot-Traffic auf der schnellsten Ebene ODER verwaltet Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce-Roboter.txt](../../assets/tools/observation-for-adobe-commerce/ip-cache-status-miss-pass-error.png)

Diese **[!UICONTROL IP cache status (MISS, PASS, ERROR) and HTTP status during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** frame zeigt die Anzahl der HTTPS-Status-Codes und nicht zwischengespeicherten Anforderungen nach IP im ausgewählten Zeitraum an. Dies zeigt die proportionale Belastung jeder IP-Adresse und das Gesamtvolumen an. Sie zeigt die IP-Adressen mit den meisten Anforderungen an.

## [!UICONTROL Fastly Cache Summary for selected time period]

![Fastly Cache-Zusammenfassung für den ausgewählten Zeitraum](../../assets/tools/observation-for-adobe-commerce/fastly-cache-summary.png)

Wenn Sie auf die [!UICONTROL Error] im unten stehenden Diagramm können Sie die letzten beiden Diagramme miteinander vergleichen. Dies kann dabei helfen anzugeben, wo die Belastung zu Site-Problemen beiträgt.

![Schnellfehlerprüfung](../../assets/tools/observation-for-adobe-commerce/compare-fastly.png)

## [!UICONTROL Graph - IPs that do not identify as bots]

![IPs, die sich während des ausgewählten Zeitraums nicht als Bots ohne Fehler identifizieren wie Bot-Traffic auf der schnellsten Ebene blockiert ODER Bots über Ihre robots.txt-Datei verwaltet Best Practices für Adobe Commerce robots.txt](../../assets/tools/observation-for-adobe-commerce/ips-that-do-not-identify-as-bots.png)

Die **[!UICONTROL Graph - IPs that do not identify as bots without error during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** frame zeigt das Feld für den Anforderungs-Benutzeragenten, die IP-Adresse und den Statuscode für Anfragen an, bei denen das Feld für den Anforderungs-Benutzeragenten nicht auf eine [!DNL bot]. Dieser Frame kann Anforderungen mit hoher Häufigkeit von beliebigen IP-Adressen anzeigen, aber achten Sie auf Anforderungen mit hoher Häufigkeit, insbesondere in einem Zeitraum, in dem die Site Probleme haben kann.

## [!UICONTROL Graph - Suspicious Non-Bot traffic]

![Verdächtiger Nicht-Bot-Traffic während des ausgewählten Zeitraums](../../assets/tools/observation-for-adobe-commerce/suspicious-non-bot-traffic.png)

Die **[!UICONTROL Graph - Suspicious Non-Bot traffic during selected time period]** -Diagramm sucht nach einem Benutzeragenten-Anforderungswert von Go-http-client, wird jedoch erweitert, um andere verdächtige Werte für den Benutzeragenten einer Anfrage zu untersuchen. Dieser Benutzeragentenwert für die Anfrage wird von Sites zum Herstellen einer Verbindung von Diensten verwendet und kann gültig sein, wird aber auch von böswilligen Benutzern verwendet [!DNL bots].

## [!UICONTROL Graph - Bot traffic by Bot name]

![Diagramm - Bot-Traffic nach Bot-Name im ausgewählten Zeitraum)](../../assets/tools/observation-for-adobe-commerce/bot-traffic-bot-name.png)

Die **[!UICONTROL Graph - Bot traffic by Bot name during selected time period]** -Frame zeigt dieselben Daten wie der Gesamt-Bot-Traffic nach [!DNL Bot] Name während der ausgewählten Zeitraumtabelle oben auf der Registerkarte. Sie zeigt die Daten über die Timeline an, damit Sie sehen können, wann die Anforderungen von der [!DNL bots] und deren Verteilung.

## [!UICONTROL Graph - Top 250 Bot Names and IP addresses]

![Die 250 beliebtesten Bot-Namen und IP-Adressen im ausgewählten Zeitraum Anleitung zum Blockieren des Bot-Traffics auf schneller Ebene ODER zum Verwalten von Bots über Ihre robots.txt-Datei Best Practices für Adobe Commerce-Roboter.txt](../../assets/tools/observation-for-adobe-commerce/top-250-bot-names-ip-addresses.png)

Die **[!UICONTROL Graph - Top 250 Bot Names and IP addresses during selected time period How to block bot traffic on Fastly level OR manage bots through your robots.txt file Best practices for Adobe Commerce robots.txt]** Frame zeigt dieselben Daten wie die Gesamtsumme an [!DNL Bot] Traffic nach Bot-Name/IP-Adresse während der ausgewählten Zeitraumtabelle oben auf der Registerkarte. Sie zeigt die Daten über die Timeline an und facettiert sie nach IP-Adresse. Dies zeigt an, wann die Anforderungen von [!DNL bots] erstellt werden, welche IP Anfragen stellt und die Verteilung der Anfragen.

## [!UICONTROL Blocked Bot name / IP addresses (in Fastly)]

![Blockierter Bot-Name/IP-Adressen (schnell) im ausgewählten Zeitraum. Dieses Diagramm zeigt sowohl Traffic als auch IPs an, die einen 403 Forbidden HTTP Status-Code zurückgegeben haben](../../assets/tools/observation-for-adobe-commerce/blocked-bot-name-ip-addresses-403-code2.png)

Die **[!UICONTROL Blocked Bot name / IP addresses (in Fastly) during selected time period. This graph displays bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** frame zeigt den Bot-Namen und die IP-Adressen an, die blockiert sind. In diesem Diagramm sehen Sie, wie alle Anfragen in blockiert sind. [!DNL Fastly] in Zukunft.

## [!UICONTROL Blocked non-Bot name / IP addresses (in Fastly)]

![Blockierter Nicht-Bot-Name/IP-Adressen (in Fastly) während des ausgewählten Zeitraums. Dieses Diagramm zeigt Nicht-Bot-Traffic und IPs an, die einen 403 Forbidden HTTP Status-Code zurückgegeben wurden ](../../assets/tools/observation-for-adobe-commerce/blocked-non-bot-name-ip-addresses.png)

Die **[!UICONTROL Blocked non-Bot name / IP addresses (in Fastly) during selected time period graph displays non-bot traffic and IPs that were returned a 403 Forbidden HTTP Status code]** Frame zeigt IP-Adressen an, die sich nicht als [!DNL bot] die blockiert wurden [!DNL Fastly].

## [!UICONTROL This table shows the number of user agents per IP address, number of successful, unsuccessful and blocked requests:]

![Die folgende Tabelle zeigt die Anzahl der Benutzeragenten pro IP-Adresse, die Anzahl der erfolgreichen, fehlgeschlagenen und blockierten Anfragen:](../../assets/tools/observation-for-adobe-commerce/unsuccessful-attempts.png)

bösartig [!DNL bots] häufig andere [!DNL bots] durch den Wert der [!UICONTROL Request User Agent] -Feld. Diese Tabelle zeigt, wie viele eindeutige Werte die IP-Adresse in diesem Feld hat. Je höher der Wert im [!UICONTROL Request User Agent] -Feld, umso verdächtiger ist die IP-Adresse.

## [!UICONTROL IP with non-200 status errors]

![IP mit Nicht-200-Statusfehlern - ohne 403-Status](../../assets/tools/observation-for-adobe-commerce/ip-non-200-status-errors.png)

Die **[!UICONTROL IP with non-200 status errors – without 403 status]** frame zeigt die Verteilung über den ausgewählten Zeitraum von IP-Adressen mit anderen HTTP-Status-Codes als 200 an. Wenn Sie höhere Werte für eine einzelne IP-Adresse oder IP-Adressengruppe sehen, müssen diese weiter untersucht werden.

## [!UICONTROL IP with 403 status codes:]

![IP mit 403 Status-Codes:](../../assets/tools/observation-for-adobe-commerce/ip-403-status-code2.png)

Die **[!UICONTROL IP with 403 status codes]** frame zeigt nicht zwischengespeicherte Anforderungen ohne [!UICONTROL cache_status=ERROR] die einen HTTP-Status von 403 haben. Dies kann zeigen, dass der Herkunftsserver die Quelle des 403 (nicht autorisiert) und nicht ein Block von ist [!DNL Fastly].

## [!UICONTROL Top 5 with non-200 status codes]

![Top 5 mit Statuscodes, die nicht 200 sind und cache_status anzeigen:](../../assets/tools/observation-for-adobe-commerce/top-5-non-200-status-code-status.png)

Die **[!UICONTROL Top 5 with non-200 status codes showing cache_status]** -Tabelle zeigt auf IP-/Statusebene die Zählungen jeder einzelnen Tabelle mit der [!UICONTROL cache_status] -Wert.

## [!UICONTROL Pageview Latency will show as spikes]

![Die Seitenansichtslatenz wird in diesem Diagramm als Spitzen angezeigt:](../../assets/tools/observation-for-adobe-commerce/pageview-latency.png)

Die **[!UICONTROL Pageview Latency will show as spikes on this graph:]** frame zeigt die Latenz der Seitenladevorgänge/API-Antworten an, die mit der [!DNL bot] Traffic.
