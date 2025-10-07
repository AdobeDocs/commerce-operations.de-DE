---
title: Die Registerkarte [!UICONTROL Redis]
description: Erfahren Sie mehr über die Registerkarte "[!UICONTROL Redis]" von [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Die Registerkarte [!DNL Redis]

## [!UICONTROL Redis Node summary]

![Redis-Knoten-Zusammenfassung](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

Die **[!UICONTROL Redis Node summary]** umfasst alle Knoten in einer Umgebung. Das obige Beispiel enthält die Knoten für das gemeinsame Staging. Es gibt eine primäre und zwei sekundäre Instanz in der Produktion sowie eine primäre und zwei sekundäre Instanz in der Staging-Umgebung.

## [!UICONTROL Redis node detail]

![Redis-Serverleistungsmetriken und Details zur Knotenkonfiguration](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

Der **[!UICONTROL Redis node detail]** Frame gibt die Umgebung, die [!DNL Redis], die Softwareversion und die Knotengröße an.

## [!UICONTROL Redis node roles timeline]

![Zeitleiste für Redis-Knotenrollen](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

Der **[!UICONTROL Redis node roles timeline]** zeigt den Verlust [!DNL Redis] Dienstes in bestimmten Rollen an. Wenn eine Linie tiefer wird, zeigt dies an, dass die bestimmte Rolle, die die Linie darstellt, einen oder mehrere Knoten verloren hat.

## [!UICONTROL Connection to Redis]

![Verbindung zu Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

Der **[!UICONTROL Connection to Redis]** zeigt den Wert net.connecteclients aus den [!DNL New Relic Redis] Beispieldaten an. Es zeigt die Anzahl der Verbindungen nach Anwendung (Umgebung) und Knoten [!DNL New Relic].

## [!UICONTROL Commands per second by node]

![Befehle pro Sekunde nach Knoten](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

Im **[!UICONTROL Commands per second by node]** werden die [!DNL Redis] Befehle nach Knoten pro Sekunde im ausgewählten Zeitraum angezeigt.

## [!UICONTROL Redis % of memory used]

![Redis % des belegten Speichers](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

Der **[!UICONTROL Redis % of memory used]** zeigt den Prozentsatz des maximalen Speichers an, der von den [!DNL Redis]-Servern verwendet wird.

## [!UICONTROL Redis used memory]

![Verwendeter Speicher](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

Der **[!UICONTROL Redis used memory]** zeigt die Knotenauslastung des Speichers in GB/MB an.

## [!UICONTROL Redis changes since last db save]

![Redis-Änderungen seit dem letzten DB-Speichern](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] ist ein speicherresidenter Benutzer und speichert die Informationen im Speicher. Der **[!UICONTROL Redis changes since last db save]** zeigt die Anzahl der Speicheränderungen an, die seit dem letzten Speichern der Datenbank vorgenommen wurden. Unter [Redis-Persistenz](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/) finden Sie weitere Erläuterungen zur [!DNL Redis's].

## [!UICONTROL Redis synchronization from Log]

![Redis-Synchronisation aus Protokoll](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

Der **[!UICONTROL Redis synchronization from Log]**-Frame konzentriert sich auf die Fehler, die bei [!DNL Redis] Synchronisierung auftreten, oder auf Fehler, die aufgrund von Synchronisierungsproblemen auftreten. Weitere Informationen zu [!DNL Redis] finden Sie unter [[!DNL Redis] Dokumentation](https://redis.io/docs/).
