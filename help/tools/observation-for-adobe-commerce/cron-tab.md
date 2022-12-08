---
title: "Die [!DNL Cron] tab"
description: Erfahren Sie mehr über die [!DNL Cron] Tab von [!DNL Observation for Adobe Commerce].
source-git-commit: 38467ebd2ec29f9e1679182fb1ee7076d738664b
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Die [!DNL Cron] tab

Auf dieser Registerkarte werden Probleme und Ursachen von [!DNL cron] Probleme.

## [!UICONTROL Cron transaction duration in seconds]

![Cron-Transaktionsdauer in Sekunden](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

Die **[!UICONTROL Cron transaction duration in seconds]** Frame Displays [!DNL crons] Transaktionsdauer in Sekunden. Dadurch werden Transaktionen angezeigt, die über lange Laufzeiten verfügen. Durch einen tieferen Einblick in APM werden weitere Details zur Abfrage angezeigt, die die Transaktion/der Vorgang ausführen kann.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL-Non-Sleeping Threads by Node](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

Die **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame zeigt die MySQL-Nicht-Sleeping-Threads nach Knoten über den ausgewählten Zeitrahmen an.

## [!UICONTROL SQL Trace count by path]

![SQL Trace-Anzahl nach Pfad](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

Die **[!UICONTROL SQL Trace count by path]** frame betrachtet die Anzahl der MySQL-Trace nach Pfad, was dazu beitragen kann, SQL-Anweisungen über einen ausgewählten Zeitraum hinweg zu verfolgen.

## [!UICONTROL Cron database call]

![Cron-Datenbankaufruf](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

Die **[!UICONTROL Cron database call]** frame betrachtet die Anzahl der [!DNL crons] über einen ausgewählten Zeitrahmen hinweg aufgerufen werden.

## [!UICONTROL Cron schedule table locks]

![Cron-Zeitplan-Tabellensperren](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

Die **[!UICONTROL Cron schedule table locks]** Frame-Look [!DNL cron] Die Zeitplantabelle wird über einen ausgewählten Zeitrahmen hinweg gesperrt.

## [!UICONTROL Cron schedule clean cron fired]

![Cron-Zeitplan-Tabellensperren](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

Die **[!UICONTROL Cron schedule clean cron fired]** frame betrachtet die Anzahl der [!DNL crons] über einen ausgewählten Zeitraum bereinigt. Wenn in diesem Frame keine Daten angezeigt werden, kann dies auf ein Problem mit [!DNL crons] korrekt ausgeführt werden. Wenn die Variable [!DNL cron] Der Auftragsplan wird nicht bereinigt. [!DNL crons] wird nicht optimal ausgeführt und kann länger dauern.

## [!UICONTROL Cron schedule clean records details table]

![Ausführungstabelle zu Cron-Zeitplan für saubere Datensätze](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

Die **[!UICONTROL Cron schedule clean records details table]** -Tabelle enthält Details zum Auftrag zum Bereinigen von Datensätzen aus der `cron_schedule` -Tabelle über einen ausgewählten Zeitraum hinweg.

## [!UICONTROL cron_schedule table updates]

![Aktualisierungen der Tabelle cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

Die **[!UICONTROL cron_schedule table updates]** frame betrachtet die Anzahl der [!DNL cron] Geplante Tabellen werden über einen ausgewählten Zeitraum hinweg aktualisiert. Eine hohe Aktivität beim Löschen oder Aktualisieren dieser Tabelle kann auf ein Problem mit [!DNL crons]. Außerdem [!DNL crons] Aktualisieren Sie diese Tabelle, wenn sie ausgeführt und abgeschlossen wird. Wenn diese Tabelle also keine Aktivität enthält und [!DNL crons] konfiguriert ist, kann es ein Problem mit [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tabellen mit Datenspeichervorgängen](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

Die **[!UICONTROL Datastore Operations Tables]** betrachtet Datenbanktabellenvorgänge, einschließlich `SELECT`, `DELETE`und `UPDATE` über einen ausgewählten Zeitraum hinweg. Dieser Rahmen zeigt die Datenbanktabellen mit der höchsten Betriebsfrequenz an.
