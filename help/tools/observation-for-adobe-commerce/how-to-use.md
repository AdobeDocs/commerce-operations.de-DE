---
title: Wie ist das Nerdlet  [!DNL Observation for Adobe Commerce] ?
description: Erfahren Sie, wie Sie das - [!DNL Observation for Adobe Commerce]  verwenden.
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Wie ist das [!DNL Observation for Adobe Commerce] Nerdlet anzuwenden?

## Allgemeiner Ansatz für die Behandlung von Problemen

Status der Umgebungsressourcen überprüfen:

* Untersuchen Sie den % der **[!UICONTROL Storage Free and MySQL % free storage by node]** Frames.

   * Folgen Sie den Links in der Kopfzeile des Frames, wenn Sie wenig Speicher sehen.

* Untersuchen Sie den % der **[!UICONTROL free system memory and Swap memory free in bytes]** Frames.

   * Wenn diese sehr geringe Speicherzustände aufweisen, können sie zu Problemen beitragen.

* Untersuchen Sie den **[!UICONTROL Alerts during the timeframe]**.

   * Adobe Commerce auf Cloud-Infrastruktur bietet [!DNL Managed alerts]. Sie können auf den Link in der Kopfzeile klicken, um [!DNL Support Knowledge Base] Artikel anzuzeigen, die Ihnen helfen, Aktionen für bestimmte Warnhinweise zu bestimmen.

* Untersuchen Sie den **[!UICONTROL CPU % by host]** Frame: Wenn er eine hohe CPU-Auslastung aufweist, überprüfen Sie den [!DNL Support Knowledge Base] in der Kopfzeile für den Frame. Stellen Sie außerdem sicher, dass während der Spitzenzeiten des Traffics keine Datenbank importiert/exportiert oder gesichert wird.

* Überprüfen Sie den **[!UICONTROL Web Traffic volume compared to one week ago]**: Wenn der Traffic im selben Zeitraum viel höher ist als in der Vorwoche, kann er erklärt werden (z. B. Verkaufskampagne oder neue Produkte, die vermarktet wurden)?
   * Wenn ein Anstieg des Traffics nicht erklärt werden kann, schauen Sie sich die durchschnittliche Antwortzeit (Millisekunden) für die Produktionsumgebung an. Trägt der höhere Traffic zu einer anderen Antwortzeit bei als normalerweise? Erweitern Sie den Zeitrahmen, um zu sehen, ob es sich um eine Anomalie handelt.
   * Wirkt sich der Anstieg des Traffics auf Web-Transaktionen aus? Prüfen Sie den **[!UICONTROL Response Code]** auf Fehler. Wenn die Site nicht verfügbar ist, können Sie auf den `Site Down?` Link in der Frame-Kopfzeile klicken. Der Frame identifiziert alle auftretenden Fehler und ihre Häufigkeit.
   * Hat jemand Änderungen an Ihrer Website bereitgestellt? Der **[!UICONTROL Deployment Log Entries]** gibt an, ob innerhalb des Problemzeitraums Bereitstellungen vorgenommen wurden. Wenn das Problem unmittelbar nach der Bereitstellung auftritt, kann es sein, dass Bereitstellungsaktivitäten der Site zusätzliche Last hinzufügen (Caches gelöscht, Services neu gestartet werden usw.).
   * Ist eine Vergrößerung oder Verkleinerung eingetreten? Wenn Ihre Site vorübergehend aktualisiert wurde, wurde sie möglicherweise auf ihre ursprüngliche Cluster-Größe zurückgesetzt. Wenn eine Anfrage zur Erhöhung der Site-Kapazität gestellt wurde, kann eine Vergrößerung auftreten. Überprüfen Sie den **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]**. Dieser Frame erkennt manchmal einen Ausfall auf einem bestimmten Knoten. Wenn die Größe abnimmt, kann dies auf ein Problem mit einem oder mehreren Knoten hinweisen.

* Auf der Registerkarte **[!UICONTROL IP Frequency]** wird die Anfragehäufigkeit anhand von IP-Adressen identifiziert, die an den Ursprungs-Servern gesendet werden (was bedeutet, dass die Anfrage nicht von [!DNL Fastly] 74 bedient werden konnte, da sie nicht zwischengespeichert wurde).

   * Überprüfen Sie für alle [!DNL Fastly] Probleme den **[!UICONTROL Fastly Cache]** Frame und wählen Sie die Fehlerfacette aus, um den Prozentsatz der fehlerhaften Anfragen anzuzeigen. Sie können auf ein Backend-Problem hinweisen, wenn sie mit Nicht-Webladevorgängen übereinstimmen.
   * Wenn die Last offenbar nicht auf Web-Traffic zurückzuführen ist, kann es zu Fehlern oder einer Anhäufung von Nicht-Web-Anfragen kommen, wie z. B. langsamen Abfragen oder [!DNL crons].

* Überprüfen Sie den **[!UICONTROL Database Errors]** auf Fehler, die mit der Problem-/Problem-Zeitleiste übereinstimmen können.
* Überprüfen Sie den **[!UICONTROL Database mysql-slow.log]**, um SQL-Anweisungen zu identifizieren, die auftreten. `INSERT`-, `UPDATE`- und `DELETE`-Befehle können eine Weile dauern, wenn die Abfrage nicht optimiert ist. Selbst `SELECT` Anweisungen können sehr ineffizient sein, wenn sie mit großen Tabellen verwendet werden.
* **[!UICONTROL PHP States]**- und **[!UICONTROL PHP Errors]**-Frames zeigen mögliche Probleme mit PHP. Der **[!UICONTROL PHP States]** zeigt die Beendigung, den Start und den Zustand des PHP-Prozesses nach Knoten an. Der **[!UICONTROL PHP Errors]** Frame kann dabei helfen, herauszufinden, wo das Problem mit PHP auftritt, z. B. Speichergröße, Worker oder Anzahl der Server.
* Um die Latenz in Transaktionen anzuzeigen, kann die Tabelle Transaktionen - Durchschnitt, Maximum, Min nach Spalten sortiert werden, um die am längsten laufende Transaktionsdauer anzuzeigen. Ein überladenes Cluster weist latente Dauern bei Transaktionen auf, aber es zeigt auch Anomalien an, die ein Problem mit einer Methode oder einem [!DNL cron] identifizieren können.
* Der **[!UICONTROL Cron error]** zeigt [!DNL cron], SQL-Fehler, die mit [!DNL cron]-Protokollen verbunden sein können, und freigegebene Staging-[!DNL crons] an, die in Produktionsumgebungen ausgeführt werden können, wenn eine dedizierte Staging-Umgebung vorhanden ist.
* Der [!UICONTROL ElasticSearch Errors] zeigt Fehler an, die auf große Probleme mit [!DNL Elasticsearch] Abfragen, Daten oder Indizes hinweisen können.
