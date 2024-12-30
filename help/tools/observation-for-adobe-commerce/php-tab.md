---
title: Die Registerkarte [!UICONTROL PHP]
description: Erfahren Sie mehr über die Registerkarte "[!UICONTROL PHP]" von [!DNL Observation for Adobe Commerce].
exl-id: 0989a7f5-75b0-4fb5-ac5e-2618603bf548
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Die Registerkarte [!UICONTROL PHP]

Die **PHP** Registerkarte zeigt Probleme mit PHP-Prozessen an, um eine tiefere Analyse von PHP-Problemen zu ermöglichen.

## [!UICONTROL PHP active process details]

![PHP active process details](../../assets/tools/php-active-process-details.jpg)

Der **[!UICONTROL PHP active process details]** zeigt die PHP-Prozesse, einschließlich php-fpm, im ausgewählten Zeitrahmen an.

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![PHP-Prozess laden](../../assets/tools/php-process-load.jpg)

Der **[!UICONTROL PHP process load (# of PHP processes and % of CPU load)]** zeigt die CPU-Last von PHP-FPM-Prozessen im ausgewählten Zeitraum an.

## [!UICONTROL PHP Memory detail]

![PHP-Speicherdetail](../../assets/tools/php-memory-detail.jpg)

Der **[!UICONTROL PHP Memory detail]** zeigt die Speichernutzung von PHP-Prozessen im ausgewählten Zeitrahmen an.

## [!UICONTROL PHP CPU Utilization]

![PHP CPU Utilisation](../../assets/tools/php-cpu-utilization.jpg)

Der **[!UICONTROL PHP CPU Utilization]** zeigt die prozentuale Auslastung von PHP-Prozessen durch CPU über den ausgewählten Zeitraum an.

## [!UICONTROL PHP Process states]

![PHP Prozessstatus](../../assets/tools/php-process-states-image-1.jpg)

Der **[!UICONTROL PHP Process states]** zeigt den PHP-Prozessstatus über den ausgewählten Zeitraum an. Es wird angezeigt, wenn PHP-Prozesse beendet und neu gestartet werden. Vorsicht vor beendeten PHP-Prozessen, die keine Neustarts anzeigen.

* &#39;%NOTICE: Wird beendet …%&#39;) als &#39;php_term&#39;
* &#39;% HINWEIS: Beenden, Tschüss!%&#39;) als &#39;php_exit&#39; angegeben
* &#39;% NOTICE: fpm wird ausgeführt, PID%&#39;) als &#39;fpm_start&#39;
* &#39;%NOTICE: Bereit, Verbindungen als &#39;php_ready&#39; zu behandeln

## [!UICONTROL PHP Errors]

![PHP-Fehler](../../assets/tools/php-errors-image-1.jpg)

Der **[!UICONTROL PHP Errors]** zeigt die Anzahl der PHP-Worker-Fehler im ausgewählten Zeitraum an. Zu den Fehlermeldungen, die analysiert und angezeigt werden, gehören:

* &#39;%WORKER_CONNECTIONS&#39; sind nicht genug%&#39;) als &#39;Worker&#39;
* &#39;%PHP Schwerwiegender Fehler: Zulässige Speichergröße!%&#39;) als &#39;mem_size&#39; angegeben
* &#39;%bei Signal 11 (SIGSEGV)%&#39; als &#39;sig_11&#39; beendet
* &#39;%beendet am Signal 7 (SIGBUS)%&#39;) als &#39;sig_7&#39;
* &#39;%PM.START_SERVERS%&#39; erhöhen) als &#39;PMSTART_SERV&#39;
* &#39;%MAX_CHILDS%&#39;) als &#39;MAX_CHILDS_CNT&#39; angegeben
* &#39;%PHP Schwerwiegender Fehler: Zulässige Speichergröße von%&#39;) als &#39;mem_ext_count&#39;
* &#39;%Speicher für Pool%&#39; kann nicht als &#39;opc_mem_count&#39; zugewiesen werden
* &#39;%Warning Interned String Buffer Overflow%&#39;) als &#39;opc_str_buf&#39;
* &#39;%Illegal string offset%&#39;) als &#39;opc_sv_comments&#39;
* &#39;%PHP Schwerwiegender Fehler: Nicht erfasste RedisException: Lesefehler bei Verbindung%&#39;) als &#39;php_exc&#39;

## [!UICONTROL PHP processes count]

![PHP-Prozesse zählen](../../assets/tools/php-processes-count.jpg)

Der **[!UICONTROL PHP processes count]** zeigt die Anzahl der PHP-Prozesse im ausgewählten Zeitrahmen an.

## [!UICONTROL Database Errors]

![Datenbankfehler](../../assets/tools/php-tab-database-errors.jpg)

Der **[!UICONTROL Database Errors]** zeigt Datenbankfehler im ausgewählten Zeitraum an. Zu den analysierten Fehlern gehören:

* &#39;%Speichergröße zugewiesen für die temporäre Tabelle ist mehr als 20% von innodb_buffer_pool_size%&#39;) als &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) als &#39;rbr_write_fail&#39;
* &#39;%mysqld: Datenträger voll%&#39;) als &#39;disk_full&#39; angegeben
* &#39;%Error number 28%&#39;) als &#39;err_28&#39;
* &#39;%rollback%&#39;) als &#39;rollback&#39;
* &#39;%Foreign key constraint failed for table%&#39;) as &#39;Foreign_key_constraint&#39;
* &#39;%ERROR_CODE: 1114%&#39;) als &#39;sql_1114_full&#39;
* &#39;%CRITICAL: SQLSTATE[HY000][2006] MySQL Server wurde entfernt%&#39;) als &#39;sql_gone&#39;
* &#39;%SQLSTATE[HY000] [1040] Zu viele Verbindungen%&#39;) als &#39;sql_1040&#39;
* &#39;%CRITICAL: SQLSTATE[HY000] [2002]%&#39;) als &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;) als &#39;sql_1047&#39;
* &#39;%[Warnung] Verbindung abgebrochen%&#39;) als &#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000]: Verletzung der Integritätsbeschränkung:%&#39;) als &#39;sql_23000&#39;
* &#39;%1205 Sperrwartezeitlimit%&#39;) als &#39;SQL_1205&#39;
* &#39;%SQLSTATE[HY000] [1049] Unknown database%&#39;) als &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: Basistabelle oder Ansicht nicht gefunden:%&#39;) als &#39;sql_42S02&#39;
* &#39;%Allgemeiner Fehler: 1114%&#39;) als &#39;sql_1114&#39;
* %SQLSTATE[40001]%) als &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]: Spalte nicht gefunden: 1054 Unbekannte Spalte%&#39;) als &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]: Syntaxfehler oder Zugriffsverletzung:%&#39;) als &#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: Kardinalitätsverletzung:%&#39;) als &#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;) als &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] Client mit IP-Adresse%&#39;) als &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]: Allgemeiner Fehler: 2014%&#39;) als &#39;sql_2014&#39;
* &#39;%1927 Verbindung wurde abgebrochen%&#39;) als &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) als &#39;sql_1062_e&#39;
* &#39;%[Hinweis] WSREP: Speicherzuordnung wird auf Festplatte geleert …%&#39;) als &#39;mem_map_flush&#39;
* &#39;%Interner MariaDB-Fehler-Code: 1146%&#39;) als &#39;sql_1146&#39;
* &#39;%Interner MariaDB-Fehler-Code: 1062%&#39;) als &#39;sql_1062&#39; * &#39;%1062 [Warnung] InnoDB:%&#39;) als &#39;sql_1062_w&#39;
* &#39;%Interner MariaDB-Fehler-Code: 1064%&#39;) als &#39;sql_1064&#39;
* &#39;%InnoDB: Assertionsfehler in Datei &#39;%&#39;) als &#39;Assertion_err&#39;
* %mysqld_safe Anzahl der laufenden Prozesse: 0%) als &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld hat das Signal%&#39;) als &#39;mysql_sigterm&#39; erhalten
* &#39;%1452 Cannot add%&#39;) as &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) als &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]: Allgemeiner Fehler: 3%&#39;) als &#39;cnt_wrt_tmp&#39;
* &#39;%Allgemeiner Fehler: 1 %&#39;) als &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) als &#39;sql_42S22&#39;
* &#39;%InnoDB: Fehler (doppelter Schlüssel)%&#39; als &#39;InnoDB_dup_key&#39;

## [!UICONTROL Database traces]

![Datenbank-Traces](../../assets/tools/php-tab-database-traces.jpg)

Der **[!UICONTROL Database traces]** zeigt Informationen zur Datenbankablaufverfolgung an. Dieser Frame ist an die Ansicht APM-Transaktionsübersicht für die ausgewählte Zeitleiste angepasst.

## [!UICONTROL Database mysql-slow.log]

![Datenbank mysql-slow.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

Der **[!UICONTROL Database mysql-slow.log]** zeigt die Abfrageanweisungstypen an, die sich im ausgewählten Zeitraum in der `mysql-slow.log`-Datei befanden.
