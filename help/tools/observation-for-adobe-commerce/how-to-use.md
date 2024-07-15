---
title: Verwendung des [!DNL Observation for Adobe Commerce] nerdlets
description: Erfahren Sie, wie Sie das [!DNL Observation for Adobe Commerce] Nerdlet verwenden.
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Verwendung des [!DNL Observation for Adobe Commerce]-Nerdlets

## Allgemeiner Ansatz zur Untersuchung von Problemen

Überprüfen Sie den Status der Umgebungsressourcen:

* Untersuchen Sie den prozentualen Anteil an **[!UICONTROL Storage Free and MySQL % free storage by node]** Frames.

   * Befolgen Sie die Links in der Kopfzeile des Frames, wenn Sie wenig Speicher sehen.

* Untersuchen Sie den prozentualen Anteil an **[!UICONTROL free system memory and Swap memory free in bytes]** Frames.

   * Wenn diese sehr geringe Speicherzustände aufweisen, können sie zu Problemen beitragen.

* Überprüfen Sie den Frame &quot;**[!UICONTROL Alerts during the timeframe]**&quot;.

   * Adobe Commerce in der Cloud-Infrastruktur bietet [!DNL Managed alerts]. Sie können auf den Link in der Kopfzeile klicken, um [!DNL Support Knowledge Base] -Artikel anzuzeigen, die Ihnen bei der Festlegung von Aktionen auf Ihrer Seite für spezifische Warnungen helfen.

* Überprüfen Sie den Frame **[!UICONTROL CPU % by host]**: Wenn er eine hohe CPU-Auslastung aufweist, überprüfen Sie den Artikel [!DNL Support Knowledge Base] in der Kopfzeile auf den Frame. Stellen Sie außerdem sicher, dass Datenbankimporte/-exporte oder -sicherungen nicht während der Traffic-Spitzenzeiten durchgeführt werden.

* Überprüfen Sie den Frame **[!UICONTROL Web Traffic volume compared to one week ago]**: Wenn der Traffic im selben Zeitraum viel höher ist als in der Vorwoche, kann er erklärt werden (z. B. eine Verkaufskampagne oder neue Produkte, die vermarktet wurden).
   * Wenn eine Traffic-Zunahme nicht erklärt werden kann, sehen Sie sich die durchschnittliche Antwortzeit (Millisekunden) für die Produktionsumgebung an. Unterscheidet sich der höhere Traffic zu einer Antwortzeit von dem normalen? Erweitern Sie den Zeitraum, um festzustellen, ob es sich um eine Anomalie handelt.
   * Hat der Anstieg des Traffics Auswirkungen auf Webtransaktionen? Überprüfen Sie den Frame **[!UICONTROL Response Code]** auf Fehler. Wenn die Site nicht erreichbar ist, können Sie auf den Link `Site Down?` im Frame-Header klicken. Der Frame identifiziert alle aufgetretenen Fehler und deren Häufigkeit.
   * Hat jemand Änderungen an Ihrer Website bereitgestellt? Der Frame **[!UICONTROL Deployment Log Entries]** gibt an, ob während des Zeitrahmens der Ausgabe Bereitstellungen durchgeführt wurden. Wenn das Problem unmittelbar nach der Bereitstellung auftritt, kann es sein, dass Bereitstellungsaktivitäten die Site zusätzlich belasten (Cache löschen, Dienste neu starten usw.).
   * Ist es zu einer Vergrößerung oder Verkleinerung gekommen? Wenn Ihre Site vorübergehend aktualisiert wurde, wurde sie möglicherweise auf die ursprüngliche Clustergröße zurückgesetzt. Wenn eine Anfrage zur Erhöhung der Site-Kapazität gestellt wurde, kann es zu einer Vergrößerung kommen. Überprüfen Sie den Frame **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** . Dieser Frame erkennt manchmal einen Ausfall an einem bestimmten Knoten. Wenn die Größe abnimmt, kann dies auf ein Problem mit einem oder mehreren Knoten hinweisen.

* Der Tab **[!UICONTROL IP Frequency]** gibt die Anforderungshäufigkeit von IP-Adressen an, die gegen die Herkunftsserver gesendet werden (d. h. die Anfrage konnte nicht von [!DNL Fastly] bearbeitet werden, da 74 sie nicht zwischengespeichert wurde).

   * Markieren Sie für alle mit [!DNL Fastly] zusammenhängenden Probleme den Frame **[!UICONTROL Fastly Cache]** und wählen Sie die Fehlerfacette aus, um den Prozentsatz der fehlerhaften Anforderungen anzuzeigen. Sie können auf ein Backend-Problem hinweisen, wenn sie mit Nicht-Web-Load zusammenfallen.
   * Wenn die Last anscheinend nicht auf den Web-Traffic zurückzuführen ist, kann es zu Fehlern oder einer Einrichtung von Nicht-Web-Anforderungen wie langsamen Abfragen oder [!DNL crons] kommen.

* Überprüfen Sie den Frame **[!UICONTROL Database Errors]** auf Fehler, die mit der Timeline für Probleme/Probleme übereinstimmen können.
* Überprüfen Sie den Frame **[!UICONTROL Database mysql-slow.log]** , um die auftretenden SQL-Anweisungen zu identifizieren. Die Befehle `INSERT`, `UPDATE` und `DELETE` können eine Weile dauern, wenn die Abfrage nicht optimiert ist. Selbst `SELECT` -Anweisungen können bei großen Tabellen sehr ineffizient sein.
* Die Frames **[!UICONTROL PHP States]** und **[!UICONTROL PHP Errors]** zeigen potenzielle Probleme mit PHP. Der Frame &quot;**[!UICONTROL PHP States]**&quot; zeigt PHP-Prozessbeendigungen, -Starts und wenn der Dienst den Status &quot;ready&quot;nach Knoten erreicht. Der Frame **[!UICONTROL PHP Errors]** kann dabei helfen, herauszufinden, wo das Problem bei PHP liegt, wie Speichergröße, Arbeitskräfte oder die Anzahl der Server.
* Um die Latenz bei Transaktionen anzuzeigen, kann die Tabelle Transaktionen - Durchschnittlich, Max., Minimum nach Spalten sortiert werden, um die längste Transaktionsdauer anzuzeigen. Ein überlasteter Cluster weist latente Zeitspannen in Transaktionen auf, zeigt aber auch Anomalien, die ein Problem mit einer Methode oder [!DNL cron] identifizieren könnten.
* Der Frame &quot;**[!UICONTROL Cron error]**&quot;zeigt [!DNL cron] Sperren, SQL-Fehler, die mit [!DNL cron] Protokollen verknüpft sein können, und freigegebene Staging- [!DNL crons], die in Produktionsumgebungen ausgeführt werden können, wenn eine dedizierte Staging-Umgebung vorhanden ist.
* Der Frame [!UICONTROL ElasticSearch Errors] zeigt Fehler an, die auf größere Probleme mit [!DNL Elasticsearch] Abfragen, Daten oder Indizes hinweisen können.
