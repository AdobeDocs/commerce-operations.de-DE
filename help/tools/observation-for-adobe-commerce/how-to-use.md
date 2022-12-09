---
title: "Verwendung der [!DNL Observation for Adobe Commerce] nerdlet"
description: Erfahren Sie, wie Sie die [!DNL Observation for Adobe Commerce] Nerdlet.
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Verwendung der [!DNL Observation for Adobe Commerce] Nerdlet

## Allgemeiner Ansatz zur Untersuchung von Problemen

Überprüfen Sie den Status der Umgebungsressourcen:

* Untersuchen Sie den Prozentsatz von **[!UICONTROL Storage Free and MySQL % free storage by node]** Frames.

   * Befolgen Sie die Links in der Kopfzeile des Frames, wenn Sie wenig Speicher sehen.

* Untersuchen Sie den Prozentsatz von **[!UICONTROL free system memory and Swap memory free in bytes]** Frames.

   * Wenn diese sehr geringe Speicherzustände aufweisen, können sie zu Problemen beitragen.

* Untersuchen Sie die **[!UICONTROL Alerts during the timeframe]** Rahmen.

   * Adobe Commerce auf Cloud-Infrastruktur bietet [!DNL Managed alerts]. Sie können auf den Link in der Kopfzeile klicken, um ihn anzuzeigen [!DNL Support Knowledge Base] -Artikel, die Ihnen bei der Festlegung von Aktionen für spezifische Warnungen helfen.

* Untersuchen Sie die **[!UICONTROL CPU % by host]** frame: Wenn eine hohe CPU-Auslastung vorliegt, überprüfen Sie die [!DNL Support Knowledge Base] -Artikel in der Kopfzeile für den Frame. Stellen Sie außerdem sicher, dass Datenbankimporte/-exporte oder -sicherungen nicht während der Traffic-Spitzenzeiten durchgeführt werden.

* Überprüfen Sie die **[!UICONTROL Web Traffic volume compared to one week ago]** frame: Wenn der Traffic im selben Zeitraum viel höher ist als in der Vorwoche, kann er erklärt werden (z. B. eine Verkaufskampagne oder neue Produkte, die vermarktet wurden).
   * Wenn eine Traffic-Zunahme nicht erklärt werden kann, sehen Sie sich die durchschnittliche Antwortzeit (Millisekunden) für die Produktionsumgebung an. Unterscheidet sich der höhere Traffic zu einer Antwortzeit von dem normalen? Erweitern Sie den Zeitraum, um festzustellen, ob es sich um eine Anomalie handelt.
   * Hat der Anstieg des Traffics Auswirkungen auf Webtransaktionen? Überprüfen Sie die **[!UICONTROL Response Code]** Frame auf Fehler. Wenn die Site ausfällt, können Sie auf die `Site Down?` in der Kopfzeile des Frames. Der Frame identifiziert alle aufgetretenen Fehler und deren Häufigkeit.
   * Hat jemand Änderungen an Ihrer Website bereitgestellt? Die **[!UICONTROL Deployment Log Entries]** gibt an, ob während des Zeitrahmens der Ausgabe Bereitstellungen vorgenommen wurden. Wenn das Problem unmittelbar nach der Bereitstellung auftritt, kann es sein, dass Bereitstellungsaktivitäten die Site zusätzlich belasten (Cache löschen, Dienste neu starten usw.).
   * Ist es zu einer Vergrößerung oder Verkleinerung gekommen? Wenn Ihre Site vorübergehend aktualisiert wurde, wurde sie möglicherweise auf die ursprüngliche Clustergröße zurückgesetzt. Wenn eine Anfrage zur Erhöhung der Site-Kapazität gestellt wurde, kann es zu einer Vergrößerung kommen. Überprüfen Sie die **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** Rahmen. Dieser Frame erkennt manchmal einen Ausfall an einem bestimmten Knoten. Wenn die Größe abnimmt, kann dies auf ein Problem mit einem oder mehreren Knoten hinweisen.

* Die **[!UICONTROL IP Frequency]** gibt die Anfragehäufigkeit von IP-Adressen an, die gegen die Herkunftsserver gesendet werden (d. h. die Anfrage konnte nicht von [!DNL Fastly] 74 wurde sie nicht zwischengespeichert).

   * Für alle [!DNL Fastly] verwandte Probleme, überprüfen Sie die **[!UICONTROL Fastly Cache]** und wählen Sie die Fehlerfacette aus, um den Prozentsatz der fehlerhaften Anforderungen anzuzeigen. Sie können auf ein Backend-Problem hinweisen, wenn sie mit Nicht-Web-Load zusammenfallen.
   * Wenn die Last nicht auf den Web-Traffic zurückzuführen ist, kann es zu Fehlern oder einer Einrichtung von Nicht-Web-Anforderungen wie langsamen Abfragen oder [!DNL crons].

* Überprüfen Sie die **[!UICONTROL Database Errors]** -Frame für Fehler, die mit der Zeitleiste für Probleme/Probleme übereinstimmen können.
* Überprüfen Sie die **[!UICONTROL Database mysql-slow.log]** Frame zum Identifizieren von SQL-Anweisungen, die auftreten. `INSERT`, `UPDATE`und `DELETE` -Befehle können eine Weile dauern, wenn die Abfrage nicht optimiert ist. Sogar `SELECT` -Anweisungen können bei großen Tabellen sehr ineffizient sein.
* **[!UICONTROL PHP States]** und **[!UICONTROL PHP Errors]** -Frames zeigen potenzielle Probleme mit PHP. Die **[!UICONTROL PHP States]** frame zeigt PHP-Prozessbeendigungen, -starts und wenn der Dienst den Status &quot;ready&quot;nach Knoten erreicht. Die **[!UICONTROL PHP Errors]** frame kann dabei helfen, zu isolieren, wo das Problem bei PHP liegt, z. B. Speichergröße, Arbeitskräfte oder die Anzahl der Server.
* Um die Latenz bei Transaktionen anzuzeigen, kann die Tabelle Transaktionen - Durchschnittlich, Max., Minimum nach Spalten sortiert werden, um die längste Transaktionsdauer anzuzeigen. Ein überlasteter Cluster weist eine latente Dauer in Transaktionen auf, zeigt aber auch Anomalien, die ein Problem mit einer Methode oder [!DNL cron].
* Die **[!UICONTROL Cron error]** Frame wird angezeigt [!DNL cron] Sperren, SQL-Fehler, die mit [!DNL cron] Protokolle und freigegebenes Staging [!DNL crons] , die in Produktionsumgebungen ausgeführt werden können, wenn eine dedizierte Staging-Umgebung vorhanden ist.
* Die [!UICONTROL ElasticSearch Errors] Frame zeigt Fehler an, die auf größere Probleme mit [!DNL Elasticsearch] Abfragen, Daten oder Indizes.
