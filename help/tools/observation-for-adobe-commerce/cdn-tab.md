---
title: Die [!UICONTROL CDN] tab
description: Informationen zum [!UICONTROL CDN] Tab von [!DNL Observation for Adobe Commerce].
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e753528a1d74eda0a1393e2cc455f33f529db739
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Die [!UICONTROL CDN] tab

Diese Registerkarte enthält Informationen, die sich auf die [!DNL content delivery network (CDN)]. Im Fall von Adobe Commerce Cloud ist dies die [!DNL Fastly] -Dienst.

## [!UICONTROL HIT rate]

![Trefferrate](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

Die **[!UICONTROL HIT rate]** frame zeigt die Anzahl zwischenspeicherbarer Anforderungen an, die zu [!UICONTROL HITS] im letzten Moment. Dies weist auf eine erfolgreiche Zwischenspeicherung hin. Der Pfeil rechts zeigt den Prozentsatz über oder unter der gleichen Zeit vor einer Woche an.

## [!UICONTROL HIT Processing]

![Trefferverarbeitung](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

Diese **[!UICONTROL HIT processing]** zeigt die Anzahl zwischenspeicherbarer Anforderungen an, die zu [!UICONTROL HITS] in der Woche.

## [!UICONTROL MISS rate]

![MISS-Rate](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

Diese **[!UICONTROL MISS rate]** zeigt die Anzahl an Fehlern zwischenspeicherbarer Anforderungen in der letzten Minute an. Ein Fehler tritt auf, wenn die Anfrage nicht zwischengespeichert wird und die Anfrage an den Herkunftsserver übergeben werden muss, um den Inhalt bereitzustellen. Der Wert rechts ist der Vergleich der Steigerung/Verringerung mit der Anzahl der Minuten pro Minute, die eine Woche zuvor vergangen sind.

## [!UICONTROL MISS time]

![MISS-Zeit](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![HIT-Verhältnis](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![Fehlerprozentsatz](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

Die **[!UICONTROL Error Percentage]** zeigt den Wert des ERROR-Prozentsatzes der Anforderungen an und zeigt den relativen Anstieg/Rückgang im Vergleich zur gleichen Zeit wie eine Woche zuvor an.

## [!UICONTROL Total Requests]

![Gesamte Anforderungen](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![Fehlerrate](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![Schneller Cache-Durchschnittliche Antwort für den ausgewählten Zeitraum in Sekunden](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

Dieser Frame zeigt die Dauer der zwischenspeicherbaren Anforderungen in Sekunden, d. h. wenn ein `cache_response` ist [!UICONTROL MISS], zeigt sie den Durchschnitt für ausgelassene zwischengespeicherte Antworten während der ausgewählten Zeit an.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![Schneller Cache-Durchschnittliche Antwort für den ausgewählten Zeitraum in Sekunden, die von POP facettiert wurden](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

*POP* in diesem Kontext bezieht sich auf einen POP (Point of Presence), der so konfiguriert ist, dass er als Pool für die Cache-Speicherung fungiert. Siehe [Anlaufstellen](https://developer.fastly.com/learning/concepts/pop/).

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![Gesamtbandbreite (Alle POPs) im ausgewählten Zeitraum im Vergleich zu vor einer Woche (% Anstieg/Rückgang)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![Anforderungen - Seit dem ausgewählten Zeitraum im Vergleich zu einer Woche](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

Dieser Frame ähnelt dem Zusammenfassungsfeld für [!UICONTROL Total Requests] oben, zeigt jedoch die Anzahl der Anfragen der letzten Wochen an. Dies sind alle Anforderungen, nicht nur zwischenspeicherbare Anforderungen (wobei `is_cacheable` ist wahr).

## [!UICONTROL Response Count]

![Anzahl der Antworten](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![Bandbreite nach POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![Top 5 URLs (Statuscodes 5xx oder 3xx)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

Die **[!UICONTROL Top 5 URLs]** -Ansicht zeigt die fünf wichtigsten URLs an, bei denen Fehlerantworten mit 5xx- oder 3xx-Fehler auftreten. Aufgrund der Platzbeschränkungen müssen Sie den Mauszeiger über die URL bewegen, um den spezifischen Fehlercode anzuzeigen, der mit dieser URL verknüpft ist. (Beispiel im roten Feld der obigen Abbildung).

## [!UICONTROL Top 25 URLs (200 status)]

![Top 25 URLs (Status 200)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

Die **[!UICONTROL Top 25 URLs]** frame zeigt die URLs an, die während des ausgewählten Zeitrahmens den Status 200 nach Anzahl zurückgegeben haben.

## [!UICONTROL Duration by Response Status]

![Dauer nach Antwortstatus](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

Die **[!UICONTROL Duration by Response Status]** -Diagramm zeigt die Fehlerantworten nach Anzahl während des ausgewählten Zeitrahmens, facettiert nach Fehlerstatus-Code.

## [!UICONTROL Duration by Response Status, top 25 urls]

![Dauer nach Status der Antwort, Top-25 URLs](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

Die **[!UICONTROL Duration by Response Status, top 25 URLs]** -Diagramm zeigt die 25 wichtigsten URLs nach der Dauer der Antwort in Sekunden an. Möglicherweise müssen Sie den Mauszeiger über die URL bewegen, um den gesamten Pfad anzuzeigen. Um auch alle URLs außer einer zu entfernen, klicken Sie auf diese URL. Sie können dann weitere URLs hinzufügen, indem Sie diese einzeln anklicken. Wenn Sie einzelne URLs entfernen möchten, können Sie die Taste gedrückt halten und auf jede URL klicken, um sie aus dem Diagramm zu entfernen.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![Dauer nach Antwortstatus, Top-25-Status ungleich 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

Die **[!UICONTROL Duration by Response Status, top 25 non-200 status]** -Diagramm ähnelt dem letzten mit dem Unterschied, dass der Fokus auf Statuscodes, die nicht unter 200 fallen, oder Fehlerstatus-Codes liegt. Daraufhin werden der Fehlercode und dann die URL angezeigt. Möglicherweise müssen Sie den Mauszeiger über die URL bewegen, um den gesamten Pfad anzuzeigen. Um auch alle URLs außer einer zu entfernen, klicken Sie auf diese URL. Sie können dann weitere URLs hinzufügen, indem Sie diese einzeln anklicken. Wenn Sie einzelne URLs entfernen möchten, können Sie die Taste gedrückt halten und auf jede URL klicken, um sie aus dem Diagramm zu entfernen.

## [!UICONTROL Error Count by POP timeline]

![Fehleranzahl nach POP-Timeline](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

Die **[!UICONTROL Error Count by POP timeline]** -Diagramm zeigt die Anzahl der Fehlerstatus entlang der ausgewählten Zeitleiste des Zeitrahmens, facettiert durch den Fehlercode.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![Dauer nach Status der Antwort, Top-25-Client-IP, Nicht-200-Status](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

Die **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** -Diagramm zeigt die IP-Adressen nach der durchschnittlichen Dauer des ausgewählten Zeitraums an, in dem Status-Fehlercodes aufgetreten sind.

## [!UICONTROL IP Frequency]

![IP-Häufigkeit](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

Die **[!UICONTROL IP Frequency]** frame zählt die Status (&#39;MISS&#39; und &#39;PASS&#39;) für jede IP aus der [!DNL Fastly] Protokolle. Webanfragen mit diesen Status erreichen den Herkunftsserver und fügen dem Server Ladevorgänge hinzu. Er zeigt die zwanzig häufigsten Adressen in der Häufigkeit. Dieser Frame kann verwendet werden, um IP-Angriffe oder Quellen hoher Belastung auf einer Website zu erkennen. Dieses Diagramm ist auch auf der Registerkarte &quot;Zusammenfassung&quot;vorhanden und wird hier platziert, um einen einfachen Vergleich mit weiteren Details zum [!DNL Fastly] auf dieser Registerkarte angezeigte Protokollinformationen.
