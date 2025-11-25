---
title: Best Practices zur Fehlerbehebung
description: Erfahren Sie, wie Sie Adobe Commerce-Implementierungsprobleme beheben.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Best Practices zur Fehlerbehebung

Befolgen Sie diese Best Practices für die effektive Fehlerbehebung bei Adobe Commerce bei Cloud-Infrastrukturproblemen.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur

## Best Practices

| Anfragetyp | Best Practices | Ressource |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Bereitstellungsprobleme | **Befolgen Sie die Best Practices für die Bereitstellung.** 13 % der Support-Tickets betreffen Bereitstellungsprobleme. Die Best Practices wurden aktualisiert und enthalten nun Möglichkeiten, viele dieser Ursachen zu verhindern. | [Best Practices für Builds und &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices)) in unserer Entwicklerdokumentation. |
| Probleme beim Herunterfahren der Site | **Verwenden der Fehlerbehebung für den Ausfall der Site.** Crons können lange laufen und sich gegenseitig überrennen. Sie sind die Ursache für viele Ausfälle und Leistungsprobleme. | [Site Down &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=de) und [Zurücksetzen von Cron-Aufträgen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=de) in unserer Support-Wissensdatenbank. |
| Leistungsprobleme | **Wenn Sie das Adobe Commerce-Banner nicht verwenden, deaktivieren Sie es.** Wenn das Banner aktiviert, aber nicht verwendet wird, werden Ressourcen verwendet, um Suchen in der Datenbank durchzuführen, wenn sie nicht erforderlich sind. Dies führt zu Leistungsproblemen. | [Deaktivieren Sie die Adobe Commerce-Bannerausgabe, um die Leistung zu &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html?lang=de). in unserer Support-Wissensdatenbank. |
| Probleme suchen | **Die MySQL-Katalogsuchmaschine wurde in Adobe Commerce 2.4.0.** entfernt. Vor der Installation von Version 2.4.0 muss der Elasticsearch-Host eingerichtet und konfiguriert sein. Siehe Installieren und Konfigurieren von Elasticsearch in unserer Entwicklerdokumentation. | [Einrichten des Elasticsearch-Service](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) in unserer Entwicklerdokumentation. |
| Benutzerdefinierte Fehler | **Keine Bereitstellung zu Spitzenzeiten.** Hinzufügen und Entfernen von Benutzenden führt zu Triggern bei einer -Bereitstellung. | [Keine Ausfallzeiten bei der Bereitstellung](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime) in unserer Entwicklerdokumentation. |
| Datenbankfehler und -probleme | **Datenbankprobleme verursachen Bereitstellungs- (Post-Hook-Probleme), Leistungs- und Standortausfälle.** Viele sind mit Fehlern oder unzureichender Zuweisung von Datenbankspeicherplatz verbunden. | [MariaDB Error Codes](https://mariadb.com/docs/server/reference/error-codes/mariadb-error-code-reference); [Manage Storage Space](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) (einschließlich Datenbank) in unserer Entwicklerdokumentation. |
| Konfigurationsprobleme | **Index nach Zeitplan anstatt Index beim Speichern.** Dies ist die effizienteste Indexkonfiguration. Index beim Speichern führt zur vollständigen Neuindizierung. | [Indexer konfigurieren](../../../configuration/cli/manage-indexers.md#configure-indexers) finden Sie in unserer Entwicklerdokumentation. |
| Probleme mit benutzerdefiniertem Code | **Überprüfen Sie Ihre langsamen Abfrageprotokolle auf Möglichkeiten, Prozesse zu identifizieren und möglicherweise abzubrechen, deren Abschluss zu viel Zeit in Anspruch nimmt.** Langsame Abfragen können zu Datenbankblockaden führen, was zu Site-Downs und Leistungsproblemen führt. | [Überprüfung langsamer Abfragen und Prozesse dauert in MySQL zu lange](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html?lang=de) |
| Probleme mit Erweiterungen | **Verwenden Sie nur verifizierte Erweiterungen, die sich derzeit auf der Commerce Marketplace befinden.** | [Erweiterungen für Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Probleme mit Ressourcen | **Überwachen Sie den verfügbaren Speicher und Speicherplatz und optimieren Sie den Speicher.** Möglicherweise steht Ihnen vor einer Aktion, die erhebliche Ressourcen verbraucht (z. B. Bereitstellung), Speicherplatz zur Verfügung. Auch eine unzureichende Optimierung des Dateispeichers (z. B. zu viele große, umfangreiche Bilder) kann zu unzureichendem Speicherplatz beitragen. Geringe Ressourcen verursachen Leistungsprobleme, Standortausfälle, blockierte Bereitstellungen und Bereitstellungsfehler. | [Verwalten des Festplattenspeichers](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) in unserer Entwicklerdokumentation; [Dateispeicher ist niedrig/erschöpft, bestimmte Seitenladevorgänge sind langsam](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=de) in unserer Support-Wissensdatenbank. |
