---
title: Registerkarte [!UICONTROL CDN]
description: Erfahren Sie mehr über die Registerkarte [!UICONTROL CDN] von  [!DNL Observation for Adobe Commerce].
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e753528a1d74eda0a1393e2cc455f33f529db739
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Registerkarte [!UICONTROL CDN]

Diese Registerkarte enthält Informationen, die sich auf den [!DNL content delivery network (CDN)] konzentrieren. Im Fall von Adobe Commerce Cloud ist dies der [!DNL Fastly] -Dienst.

## [!UICONTROL HIT rate]

![Trefferrate](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

Der Frame **[!UICONTROL HIT rate]** zeigt die Anzahl der zwischenspeicherbaren Anforderungen an, die in der letzten Minute zu [!UICONTROL HITS] führten. Dies weist auf eine erfolgreiche Zwischenspeicherung hin. Der Pfeil rechts zeigt den Prozentsatz über oder unter der gleichen Zeit vor einer Woche an.

## [!UICONTROL HIT Processing]

![Trefferverarbeitung](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

Dieses Feld &quot;**[!UICONTROL HIT processing]**&quot; zeigt die Anzahl der zwischenspeicherbaren Anforderungen, die während der Woche zu &quot;[!UICONTROL HITS]&quot; führten.

## [!UICONTROL MISS rate]

![MISS-Rate](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

Dieses Feld &quot;**[!UICONTROL MISS rate]**&quot; zeigt die Anzahl der Fehlschläge zwischenspeicherbarer Anforderungen in der letzten Minute an. Ein Fehler tritt auf, wenn die Anfrage nicht zwischengespeichert wird und die Anfrage an den Herkunftsserver übergeben werden muss, um den Inhalt bereitzustellen. Der Wert rechts ist der Vergleich der Steigerung/Verringerung mit der Anzahl der Minuten pro Minute, die eine Woche zuvor vergangen sind.

## [!UICONTROL MISS time]

![FALSCHE ZEIT](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![Trefferverhältnis](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![Fehlerprozentsatz](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

Das Feld &quot;**[!UICONTROL Error Percentage]**&quot; zeigt den Wert des ERROR-Prozentsatzes der Anforderungen an und zeigt den relativen Anstieg/Rückgang im Vergleich zur gleichen Zeit wie eine Woche zuvor an.

## [!UICONTROL Total Requests]

![Anforderungen insgesamt](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![Fehlerrate](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![Durchschnittliche durchschnittliche Antwort im Cache für den ausgewählten Zeitraum in Sekunden schnell zwischenspeichern](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

Dieser Frame zeigt die Dauer der zwischenspeicherbaren Anforderungen in Sekunden an. Wenn also `cache_response` den Wert [!UICONTROL MISS] aufweist, wird der Durchschnitt der ausgelassenen zwischengespeicherten Antworten für die ausgewählte Zeit angezeigt.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![Durchschnittliche durchschnittliche Antwort im Cache für den ausgewählten Zeitraum in Sekunden, der von POP gefackelt wurde](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

*POP* bezieht sich in diesem Zusammenhang auf einen Point of Presence (POP), der so konfiguriert ist, dass er als Pool für die Cache-Speicherung funktioniert. Siehe [Points of presence](https://developer.fastly.com/learning/concepts/pop/).

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![Gesamtbandbreite (alle POPs) im ausgewählten Zeitraum im Vergleich zu 1 Woche zuvor (Anstieg/Rückgang in %)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![Anforderungen - Seit dem ausgewählten Zeitraum im Vergleich zu einer Woche vor ](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

Dieser Rahmen ähnelt dem Zusammenfassungsfeld für [!UICONTROL Total Requests] oben, zeigt jedoch die Anforderungszahlen der vorherigen Wochen an. Dies sind alle Anforderungen, nicht nur zwischenspeicherbare Anforderungen (wobei `is_cacheable` wahr ist).

## [!UICONTROL Response Count]

![Antwortanzahl](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![Bandbreite nach POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![Die 5 wichtigsten URLs (Statuscodes 5xx oder 3xx)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

Die Ansicht &quot;**[!UICONTROL Top 5 URLs]**&quot;zeigt die fünf wichtigsten URLs an, bei denen Fehlerantworten mit 5xx- oder 3xx-Werten auftreten. Aufgrund der Platzbeschränkungen müssen Sie den Mauszeiger über die URL bewegen, um den spezifischen Fehlercode anzuzeigen, der mit dieser URL verknüpft ist. (Beispiel im roten Feld der obigen Abbildung).

## [!UICONTROL Top 25 URLs (200 status)]

![Top 25 URLs (200-Status)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

Der Frame &quot;**[!UICONTROL Top 25 URLs]**&quot;zeigt die URLs an, die während des ausgewählten Zeitraums einen 200-Status nach Anzahl zurückgegeben haben.

## [!UICONTROL Duration by Response Status]

![Dauer nach Antwortstatus](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

Das Diagramm **[!UICONTROL Duration by Response Status]** zeigt die Fehlerantworten nach Anzahl während des ausgewählten Zeitraums, facettiert nach dem Fehlerstatus-Code.

## [!UICONTROL Duration by Response Status, top 25 urls]

![Dauer nach Antwortstatus, die obersten 25 URLs](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

Das Diagramm **[!UICONTROL Duration by Response Status, top 25 URLs]** zeigt die 25 wichtigsten URLs nach der Dauer der Antwort in Sekunden. Möglicherweise müssen Sie den Mauszeiger über die URL bewegen, um den gesamten Pfad anzuzeigen. Um auch alle URLs außer einer zu entfernen, klicken Sie auf diese URL. Sie können dann weitere URLs hinzufügen, indem Sie diese einzeln anklicken. Wenn Sie einzelne URLs entfernen möchten, können Sie die Taste gedrückt halten und auf jede URL klicken, um sie aus dem Diagramm zu entfernen.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![Dauer nach Antwortstatus, Top-25-Status ungleich 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

Das Diagramm **[!UICONTROL Duration by Response Status, top 25 non-200 status]** ähnelt dem letzten mit dem Unterschied, dass der Fokus auf Statuscodes, die nicht 200 sind, oder Fehlerstatus-Codes liegt. Daraufhin werden der Fehlercode und dann die URL angezeigt. Möglicherweise müssen Sie den Mauszeiger über die URL bewegen, um den gesamten Pfad anzuzeigen. Um auch alle URLs außer einer zu entfernen, klicken Sie auf diese URL. Sie können dann weitere URLs hinzufügen, indem Sie diese einzeln anklicken. Wenn Sie einzelne URLs entfernen möchten, können Sie die Taste gedrückt halten und auf jede URL klicken, um sie aus dem Diagramm zu entfernen.

## [!UICONTROL Error Count by POP timeline]

![Fehleranzahl nach POP-Timeline](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

Das Diagramm **[!UICONTROL Error Count by POP timeline]** zeigt die Anzahl der Fehlerstatus entlang der ausgewählten Zeitleiste des Zeitrahmens, facettiert durch den Fehlercode.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![Dauer nach Status der Antwort, Top-25-Client-IP, Nicht-200-Status](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

Das Diagramm **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** zeigt die IP-Adressen nach der durchschnittlichen Dauer des ausgewählten Zeitraums an, in dem Status-Fehlercodes aufgetreten sind.

## [!UICONTROL IP Frequency]

![IP-Häufigkeit](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

Der Frame **[!UICONTROL IP Frequency]** zählt die Status (&#39;MISS&#39; und &#39;PASS&#39;) für jede IP-Adresse aus den [!DNL Fastly] -Protokollen. Webanfragen mit diesen Status erreichen den Herkunftsserver und fügen dem Server Ladevorgänge hinzu. Er zeigt die zwanzig häufigsten Adressen in der Häufigkeit. Dieser Frame kann verwendet werden, um IP-Angriffe oder Quellen hoher Belastung auf einer Website zu erkennen. Dieses Diagramm ist auch auf der Registerkarte &quot;Zusammenfassung&quot;vorhanden und wird hier platziert, um einen einfachen Vergleich mit weiteren Details zu den [!DNL Fastly]-Protokollinformationen zu ermöglichen, die auf dieser Registerkarte angezeigt werden.
