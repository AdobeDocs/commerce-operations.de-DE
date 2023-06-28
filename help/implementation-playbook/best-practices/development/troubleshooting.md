---
title: Best Practices zur Fehlerbehebung
description: Erfahren Sie, wie Sie Probleme bei der Implementierung von Adobe Commerce beheben können.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Best Practices zur Fehlerbehebung

Befolgen Sie diese Best Practices zur wirksamen Fehlerbehebung bei Problemen mit der Cloud-Infrastruktur von Adobe Commerce.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur

## Best Practices

| Problemtyp | Best Practices | Ressource |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Bereitstellungsprobleme | **Befolgen Sie die Best Practices für die Bereitstellung.** 13 % der Support-Tickets betreffen Bereitstellungsprobleme. Die Best Practices wurden aktualisiert und enthalten jetzt auch Möglichkeiten, viele dieser Ursachen zu verhindern. | [Best Practices für Builds und Implementierungen](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) in unserer Entwicklerdokumentation. |
| Site-Down-Probleme | **Verwenden Sie die Fehlerbehebung für Site Down.** Crons können lange laufen und sich überlaufen lassen. Sie sind die Ursache für viele Ausfälle und Leistungsprobleme. | [Site-Down-Fehlerbehebung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) und [Zurücksetzen von Cron-Aufträgen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) in unserer Wissensdatenbank. |
| Leistungsprobleme | **Wenn Sie kein Adobe Commerce-Banner verwenden, deaktivieren Sie es.** Wenn das Banner aktiviert, aber nicht verwendet wird, werden Ressourcen verwendet, um Suchen in der Datenbank durchzuführen, wenn sie nicht erforderlich sind. Dies führt zu Leistungsproblemen. | [Adobe Commerce-Bannerausgabe deaktivieren, um die Leistung zu verbessern](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) in unserer Wissensdatenbank. |
| Suchprobleme | **Die MySQL-Katalogsuchmaschine wurde in Adobe Commerce 2.4.0 entfernt.** Sie müssen den Elasticsearch-Host vor der Installation von Version 2.4.0 eingerichtet und konfiguriert haben. Weitere Informationen finden Sie unter Installieren und Konfigurieren von Elasticsearch in unserer Entwicklerdokumentation. | [Elasticsearch-Dienst einrichten](https://devdocs.magento.com/cloud/project/services-elastic.html) in unserer Entwicklerdokumentation. |
| Benutzerdefinierte Fehler | **Nicht während Spitzenzeiten bereitstellen.** Durch Hinzufügen und Entfernen von Benutzern wird eine Bereitstellung Trigger. | [Keine Ausfallzeit-Bereitstellung](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) in unserer Entwicklerdokumentation. |
| Datenbankfehler und -probleme | **Datenbankprobleme verursachen Bereitstellungs- (Post-Hook-Probleme), Leistungs- und Site-Down-Situationen.** Viele sind mit Fehlern oder unzureichender Zuordnung von Datenbankspeicherplatz verbunden. | [MariaDB-Fehlercodes](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Verwalten des Speicherplatzes](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (einschließlich Datenbank) in unserer Entwicklerdokumentation. |
| Konfigurationsprobleme | **Indexieren Sie bei &quot;Speichern&quot;nach Zeitplan anstatt nach Index.** Dies ist die effizienteste Indizierungskonfiguration. Der Index bei Speichern führt zur vollständigen Neuindizierung. | [Indexer konfigurieren](../../../configuration/cli/manage-indexers.md#configure-indexers) in unserer Entwicklerdokumentation. |
| Probleme mit benutzerspezifischem Code | **Überprüfen Sie Ihre langsamen Abfrageprotokolle auf Möglichkeiten, Prozesse zu identifizieren und möglicherweise abzubrechen, die zu viel Zeit in Anspruch nehmen.** Langsame Abfragen können zu Datenbankblockierungen führen, was zu Site-Downs und Leistungsproblemen führt. | [Überprüfen langsamer Abfragen und Prozesse, die in MySQL zu lange dauern](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Erweiterungsprobleme | **Verwenden Sie nur überprüfte Erweiterungen, die sich derzeit im Commerce Marketplace befinden.** | [Erweiterungen für Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Ressourcenprobleme | **Überwachen Sie den verfügbaren Speicher und Speicherplatz und optimieren Sie den Speicher.** Möglicherweise verfügen Sie vor einer Aktion, die erhebliche Ressourcen verbraucht (z. B. Bereitstellung), über ausreichend Speicherplatz. Eine ungenügende Optimierung des Dateispeichers (z. B. zu viele große Rich-Bilder) kann auch zu ungenügendem Speicherplatz beitragen. Geringe Ressourcen verursachen Leistungsprobleme, Site-Downloads, blockierte Bereitstellungen und Bereitstellungsfehler. | [Verwalten des Festplattenspeichers](https://devdocs.magento.com/cloud/project/manage-disk-space.html) in unserer Entwicklerdokumentation; [Dateispeicher niedrig/erschöpft, bestimmte Seitenladevorgänge sind langsam](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) in unserer Wissensdatenbank. |
