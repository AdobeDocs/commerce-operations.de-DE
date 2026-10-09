---
title: Die Registerkarte [!DNL Cron]
description: Erfahren Sie mehr über die Registerkarte [!DNL Cron] von [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%
---
# Die Registerkarte [!DNL Cron]

Diese Registerkarte dient dazu, Probleme und Ursachen [!DNL cron] Probleme schnell zu isolieren.

## [!UICONTROL Cron transaction duration in seconds]

![Cron-Transaktionsdauer in Sekunden](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

Der **[!UICONTROL Cron transaction duration in seconds]** zeigt [!DNL crons] Transaktionsdauer in Sekunden an. Dadurch werden Transaktionen mit langen Laufzeiten angezeigt. Ein tieferer Einblick in APM zeigt weitere Details dazu, welche Abfrage die Transaktion/der Vorgang möglicherweise ausführt.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL Threads ohne Ruhezustand nach Knoten](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

Der **[!UICONTROL MySQL Non-Sleeping Threads by Node]** zeigt die MySQL Nicht-Sleeping-Threads nach Knoten für den ausgewählten Zeitraum an.

## [!UICONTROL SQL Trace count by path]

![SQL-Ablaufverfolgungsanzahl nach Pfad](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

Der **[!UICONTROL SQL Trace count by path]** betrachtet die Anzahl der MySQL-Traces nach Pfad, was dazu beitragen kann, SQL-Anweisungen über einen ausgewählten Zeitraum hinweg zu verfolgen.

## [!UICONTROL Cron database call]

![Cron-Datenbankaufruf](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

Der **[!UICONTROL Cron database call]** zeigt die Anzahl der [!DNL crons] an, die über einen ausgewählten Zeitraum in die Datenbank aufgenommen wurden.

## [!UICONTROL Cron schedule table locks]

![Cron-Plantabellen-Sperren](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

Der **[!UICONTROL Cron schedule table locks]** zeigt [!DNL cron] Zeitplantabellen-Sperren für einen ausgewählten Zeitraum an.

## [!UICONTROL Cron schedule clean cron fired]

![Cron-Plantabellen-Sperren](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

Der **[!UICONTROL Cron schedule clean cron fired]** zeigt die Anzahl der [!DNL crons] an, die in einem ausgewählten Zeitraum bereinigt wurden. Wenn in diesem Frame keine Daten angezeigt werden, kann dies auf ein Problem mit [!DNL crons] ordnungsgemäßen Ausführung hinweisen. Wenn der [!DNL cron] Auftragsplan nicht bereinigt wurde, wird [!DNL crons] nicht optimal ausgeführt und kann länger dauern.

## [!UICONTROL Cron schedule clean records details table]

![Tabelle mit Details zur Bereinigung der Datensätze des Cron-Zeitplans](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

Die **[!UICONTROL Cron schedule clean records details table]** Tabelle enthält Details zum Vorgang zum Löschen von Datensätzen aus der `cron_schedule` Tabelle über einen ausgewählten Zeitraum.

## [!UICONTROL cron_schedule table updates]

![cron_schedule-Tabellenaktualisierungen](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

Der **[!UICONTROL cron_schedule table updates]** zeigt die Anzahl [!DNL cron] geplanten Tabellenaktualisierungen über einen ausgewählten Zeitraum an. Eine hohe Aktivität beim Löschen oder Aktualisieren dieser Tabelle kann auf ein Problem mit [!DNL crons] hinweisen. Aktualisieren [!DNL crons] diese Tabelle außerdem bei ihrer Ausführung und Fertigstellung. Wenn es also keine Aktivität in dieser Tabelle gibt und [!DNL crons] konfiguriert sind, könnte es ein Problem mit [!DNL crons] geben.

## [!UICONTROL Datastore Operations Tables]

![Datenspeicher-Vorgangstabellen](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

Der **[!UICONTROL Datastore Operations Tables]** untersucht Datenbanktabellenvorgänge, einschließlich `SELECT`, `DELETE` und `UPDATE` für einen ausgewählten Zeitraum. Dieser Rahmen zeigt die Datenbanktabellen mit der höchsten Vorgangsfrequenz an.
