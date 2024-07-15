---
title: Best Practices zur Fehlerbehebung
description: Erfahren Sie, wie Sie Probleme bei der Implementierung von Adobe Commerce beheben können.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Best Practices zur Fehlerbehebung

Befolgen Sie diese Best Practices zur wirksamen Fehlerbehebung bei Problemen mit der Cloud-Infrastruktur von Adobe Commerce.

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur

## Best Practices

| Problemtyp | Best Practices | Ressource |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Bereitstellungsprobleme | **Befolgen Sie die Best Practices für die Bereitstellung.** 13 % der Support-Tickets betreffen Bereitstellungsprobleme. Die Best Practices wurden aktualisiert und enthalten jetzt auch Möglichkeiten, viele dieser Ursachen zu verhindern. | [Best Practices für Builds und Bereitstellung](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) in unserer Entwicklerdokumentation. |
| Site-Down-Probleme | **Verwenden Sie die Problembehebung für Site Down.** Crons können lange laufen und sich überlaufen lassen. Sie sind die Ursache für viele Ausfälle und Leistungsprobleme. | [Site Down-Fehlerbehebung](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) und [Zurücksetzen von Cron-Aufträgen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) in unserer Support-Wissensdatenbank. |
| Leistungsprobleme | **Wenn Sie kein Adobe Commerce-Banner verwenden, deaktivieren Sie es.** Wenn das Banner aktiviert, aber nicht verwendet wird, werden Ressourcen verwendet, um Suchen in der Datenbank durchzuführen, wenn sie nicht erforderlich sind. Dies führt zu Leistungsproblemen. | [Deaktivieren Sie die Adobe Commerce-Bannerausgabe, um die Leistung zu verbessern](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) in unserer Support-Wissensdatenbank. |
| Suchprobleme | **Die MySQL-Katalogsuchmaschine wurde in Adobe Commerce 2.4.0 entfernt.** Sie müssen den Elasticsearch-Host einrichten und konfigurieren, bevor Sie Version 2.4.0 installieren. Weitere Informationen finden Sie unter Installieren und Konfigurieren von Elasticsearch in unserer Entwicklerdokumentation. | [Richten Sie den Elasticsearch-Dienst](https://devdocs.magento.com/cloud/project/services-elastic.html) in unserer Entwicklerdokumentation ein. |
| Benutzerdefinierte Fehler | **Nicht während Spitzenzeiten bereitstellen.** Durch Hinzufügen und Entfernen von Benutzern wird eine Bereitstellung Trigger. | [Keine Ausfallzeitbereitstellung](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) in unserer Entwicklerdokumentation. |
| Datenbankfehler und -probleme | **Datenbankprobleme verursachen Bereitstellungs- (Post-Hook-Probleme), Leistungs- und Site-Down-Situationen.** Viele enthalten Fehler oder eine unzureichende Zuordnung von Datenbankspeicherplatz. | [MariaDB-Fehlercodes](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Speicherplatzverwaltung](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (einschließlich Datenbank) in unserer Entwicklerdokumentation. |
| Konfigurationsprobleme | **Indexieren nach Zeitplan anstelle von Index beim Speichern.** Dies ist die effizienteste Indizierungskonfiguration. Der Index bei Speichern führt zur vollständigen Neuindizierung. | [Konfigurieren Sie die Indexer](../../../configuration/cli/manage-indexers.md#configure-indexers) in unserer Entwicklerdokumentation. |
| Probleme mit benutzerspezifischem Code | **Überprüfen Sie Ihre langsamen Abfrageprotokolle auf Möglichkeiten, Prozesse zu identifizieren und möglicherweise abzubrechen, die zu viel Zeit in Anspruch nehmen.** Langsame Abfragen können zu Datenbankblockierungen führen, was zu Site-Downs und Leistungsproblemen führt. | [Überprüfen langsamer Abfragen und Prozesse, die in MySQL zu lange dauern](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Erweiterungsprobleme | **Verwenden Sie nur überprüfte Erweiterungen, die sich derzeit auf dem Commerce Marketplace befinden.** | [Erweiterungen für Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Ressourcenprobleme | **Überwachen Sie den verfügbaren Speicher und Speicherplatz und optimieren Sie den Speicher.** Sie haben möglicherweise Speicherplatz vor einer Aktion, die erhebliche Ressourcen verbraucht (z. B. Bereitstellung). Eine ungenügende Optimierung des Dateispeichers (z. B. zu viele große Rich-Bilder) kann auch zu ungenügendem Speicherplatz beitragen. Geringe Ressourcen verursachen Leistungsprobleme, Site-Downloads, blockierte Bereitstellungen und Bereitstellungsfehler. | [Verwalten Sie Speicherplatz](https://devdocs.magento.com/cloud/project/manage-disk-space.html) in unserer Entwicklerdokumentation. [Der Dateispeicher ist niedrig/erschöpft, bestimmte Seitenladevorgänge sind langsam](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) in unserer Support-Wissensdatenbank. |
