---
title: '"Die [!UICONTROL Redis] tab"'
description: Erfahren Sie mehr über die [!UICONTROL Redis] Tab von [!DNL Observation for Adobe Commerce].
source-git-commit: 3f2a401bb916fc04405f21ba2acfc42f7defdccb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# Die [!DNL Redis] tab

## [!UICONTROL Redis Node summary]

![Zusammenfassung des Redis-Knotens](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

Die **[!UICONTROL Redis Node summary]** umfasst alle Knoten in einer Umgebung. In diesem Beispiel werden die Knoten für freigegebene Staging eingeschlossen. Es gibt eine primäre und zwei sekundäre Produktions- sowie eine primäre und zwei sekundäre Staging-Aktivitäten.

## [!UICONTROL Redis node detail]

![Redis node detail](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

Die **[!UICONTROL Redis node detail]** frame die Umgebung angibt, [!DNL Redis] Rolle, Softwareversion und Knotengröße.

## [!UICONTROL Redis node roles timeline]

![Überarbeitet die Timeline der Knotenrollen](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

Die **[!UICONTROL Redis node roles timeline]** Frame zeigt den Verlust von [!DNL Redis] -Dienst in bestimmten Rollen. Wenn eine Zeile sinkt, zeigt dies an, dass die bestimmte Rolle, die die Zeile darstellt, einen oder mehrere Knoten verloren hat.

## [!UICONTROL Connection to Redis]

![Verbindung zu Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

Die **[!UICONTROL Connection to Redis]** frame zeigt den Wert net.linkedClients aus der [!DNL New Relic Redis] Beispieldaten. Er zeigt die Anzahl der Verbindungen nach [!DNL New Relic] application (environment) und node.

## [!UICONTROL Commands per second by node]

![Befehle pro Sekunde nach Knoten](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

Die **[!UICONTROL Commands per second by node]** -Frame zeigt die [!DNL Redis] -Befehle nach Knoten pro Sekunde über den ausgewählten Zeitraum hinweg.

## [!UICONTROL Redis % of memory used]

![Redis % des verwendeten Speichers](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

Die **[!UICONTROL Redis % of memory used]** Frame zeigt den Prozentsatz des maximalen Speichers an, der vom [!DNL Redis] Server.

## [!UICONTROL Redis used memory]

![Verwendeter Speicher zurücksetzen](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

Die **[!UICONTROL Redis used memory]** frame zeigt die Knotennutzung des Speichers in GB/MB an.

## [!UICONTROL Redis changes since last db save]

![Ändert Änderungen seit dem letzten db-Speichern](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] ist speicherspeicherresidenz und speichert die Informationen für die Speicherung. Die **[!UICONTROL Redis changes since last db save]** frame gibt die Anzahl der Speicheränderungen an, die seit dem Speichern der letzten Datenbank vorgenommen wurden. [Diese Informationen](https://redis.io/docs/manual/persistence/) erklärt [!DNL Redis's] Persistenz.

## [!UICONTROL Redis synchronization from Log]

![Redivensynchronisation aus Protokoll](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

Die **[!UICONTROL Redis synchronization from Log]** frame konzentriert sich auf Fehler, die während [!DNL Redis] Synchronisation oder Fehler, die aufgrund von Synchronisierungsproblemen auftreten. Siehe [Redis-Dokumentation](https://redis.io/docs/).
