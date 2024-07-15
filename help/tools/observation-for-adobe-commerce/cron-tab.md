---
title: Registerkarte [!DNL Cron]
description: Erfahren Sie mehr über die Registerkarte [!DNL Cron] von  [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Registerkarte [!DNL Cron]

Auf dieser Registerkarte wird versucht, Probleme und Ursachen von [!DNL cron] -Problemen schnell zu isolieren.

## [!UICONTROL Cron transaction duration in seconds]

![Dauer der Cron-Transaktion in Sekunden](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

Der Frame **[!UICONTROL Cron transaction duration in seconds]** zeigt die [!DNL crons] Transaktionsdauer in Sekunden an. Dadurch werden Transaktionen angezeigt, die über lange Laufzeiten verfügen. Durch einen tieferen Einblick in APM werden weitere Details zur Abfrage angezeigt, die die Transaktion/der Vorgang ausführen kann.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL - Threads nicht beibehalten von Knoten](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

Der Frame &quot;**[!UICONTROL MySQL Non-Sleeping Threads by Node]**&quot;zeigt die MySQL-Nicht-Sleep-Threads nach Knoten über den ausgewählten Zeitraum hinweg an.

## [!UICONTROL SQL Trace count by path]

![SQL-Ablaufverfolgungsanzahl nach Pfad](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

Der Frame &quot;**[!UICONTROL SQL Trace count by path]**&quot; betrachtet die Anzahl der MySQL-Trace nach Pfad, was dazu beitragen kann, SQL-Anweisungen über einen ausgewählten Zeitraum hinweg zu verfolgen.

## [!UICONTROL Cron database call]

![Cron-Datenbankaufruf](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

Der Frame **[!UICONTROL Cron database call]** zeigt die Anzahl der Aufrufe von [!DNL crons] an die Datenbank über einen ausgewählten Zeitraum an.

## [!UICONTROL Cron schedule table locks]

![Sperren der Cron-Zeitplan-Tabelle](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

Der Frame **[!UICONTROL Cron schedule table locks]** betrachtet die Tabellensperrung für den [!DNL cron]-Zeitplan über einen ausgewählten Zeitraum hinweg.

## [!UICONTROL Cron schedule clean cron fired]

![Sperren der Cron-Zeitplan-Tabelle](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

Der Frame &quot;**[!UICONTROL Cron schedule clean cron fired]**&quot;zeigt die Anzahl der [!DNL crons] an, die während eines ausgewählten Zeitraums bereinigt wurden. Wenn in diesem Frame keine Daten angezeigt werden, kann dies auf ein Problem bei der ordnungsgemäßen Ausführung von [!DNL crons] hinweisen. Wenn der [!DNL cron] Auftragsplan nicht bereinigt wird, wird [!DNL crons] nicht optimal ausgeführt und kann länger dauern.

## [!UICONTROL Cron schedule clean records details table]

![Ausführungstabelle für Cron-Zeitplan für saubere Datensätze ](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

Die Tabelle **[!UICONTROL Cron schedule clean records details table]** enthält Details zum Auftrag, um Datensätze aus der Tabelle `cron_schedule` über einen ausgewählten Zeitraum zu bereinigen.

## [!UICONTROL cron_schedule table updates]

![cron_schedule table updates](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

Der Frame **[!UICONTROL cron_schedule table updates]** betrachtet die Anzahl der geplanten [!DNL cron] Tabellenaktualisierungen über einen ausgewählten Zeitraum. Eine hohe Aktivität beim Löschen oder Aktualisieren dieser Tabelle kann auf ein Problem mit [!DNL crons] hinweisen. Außerdem aktualisiert [!DNL crons] diese Tabelle, wenn sie ausgeführt und abgeschlossen wird. Wenn also keine Aktivität auf dieser Tabelle vorhanden ist und [!DNL crons] konfiguriert ist, kann es ein Problem mit [!DNL crons] geben.

## [!UICONTROL Datastore Operations Tables]

![Datastore-Betriebstabellen](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

Der **[!UICONTROL Datastore Operations Tables]** betrachtet Datenbanktabellenvorgänge, einschließlich `SELECT`, `DELETE` und `UPDATE` innerhalb eines ausgewählten Zeitraums. Dieser Rahmen zeigt die Datenbanktabellen mit der höchsten Betriebsfrequenz an.
