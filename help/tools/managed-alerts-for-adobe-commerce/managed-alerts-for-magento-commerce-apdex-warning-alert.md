---
title: 'Verwaltete Warnhinweise für Adobe Commerce: [!DNL Apdex] Warnhinweis'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung für den Fall,  [!DNL Apdex]  Sie einen Warnhinweis für den In-Score  [!DNL New Relic]. The [!DNL Apdex]  Adobe Commerce erhalten, der die Zufriedenheit der Benutzer mit der Reaktionszeit von Web-Anwendungen und -Services misst. Sofortiges Handeln ist erforderlich, um das Problem zu beheben.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: 0e1e0e001cfe07d7404b4dd9f53c1608df1e0c25
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 0%

---


# Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis [!DNL Apdex]

Dieser Artikel enthält Schritte zur Fehlerbehebung für den Fall, dass Sie in [!DNL New Relic] einen [!DNL Apdex] Warnhinweis für Adobe Commerce erhalten. Der [!DNL Apdex] Wert misst die Zufriedenheit der Benutzer mit der Reaktionszeit von Web-Anwendungen und -Services. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![APDEX-Warnhinweis](../../assets/managed-alerts/apdex-warning-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

* Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur
* Starterplanarchitektur für Adobe Commerce auf Cloud-Infrastruktur

## Problem

Sie erhalten in [!DNL New Relic] einen verwalteten Warnhinweis, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Händlern mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

<u> **DO!** </u>

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Aktivieren oder Deaktivieren des ](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)) im Commerce-Installationshandbuch. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Verwalten der Liste von ausgenommenen IP](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)Adressen) im Commerce-Installationshandbuch.

<u>**Tu&#39;s nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

1. Um die Ursache des Problems zu identifizieren, verwenden Sie [[!DNL New Relic APM's] Transaktionsseite](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems), um Transaktionen mit Leistungsproblemen zu identifizieren:
   * Buchungen in aufsteigender [!DNL Apdex scores] sortieren. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit auf die Antwortzeit Ihrer Web-Anwendungen und -Services. Ein [niedriger [!DNL Apdex] Wert](managed-alerts-for-magento-commerce-apdex-warning-alert.md) kann auf einen Engpass hinweisen (eine Transaktion mit einer höheren Antwortzeit). Normalerweise ist es die Datenbank, [!DNL Redis] oder PHP. Anweisungen hierzu finden Sie unter [[!DNL New Relic] Transaktionen mit höchster  [!DNL Apdex]  anzeigen](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Antwortzeit, dem zeitaufwendigsten Wert und anderen Schwellenwerten. Anweisungen hierzu finden Sie unter [[!DNL New Relic] Suchen spezifischer Leistungsprobleme](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Verwenden Sie [[!DNL New Relic]  Seite „Infrastruktur“ von APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) um ressourcenintensive Prozesse zu identifizieren. Anweisungen hierzu finden Sie auf [[!DNL New Relic]  Seite „Überwachung der Infrastruktur - Hosts: Registerkarte [!UICONTROL Processes]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Wenn Services wie [!DNL Redis] oder MySQL die Hauptquelle für den Speicherverbrauch sind, versuchen Sie Folgendes:
   * Vergewissern Sie sich, dass Sie die neueste Version verwenden. Neuere Versionen können manchmal Speicherlecks beheben. Wenn Sie nicht die neueste Version verwenden, sollten Sie ein Upgrade in Erwägung ziehen. Anweisungen hierzu finden Sie unter [Service ändern](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html?lang=de) im Handbuch zu Commerce in Cloud Manager.
1. Wenn das Problem nicht durch Service-Versionen verursacht wird:
   * Suchen Sie nach anderen MySQL-Problemen wie lang laufenden Abfragen, nicht definierten Primären Schlüsseln und doppelten Indizes. Anweisungen hierzu finden Sie unter [Häufigste Datenbankprobleme in Adobe Commerce in Cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html?lang=de) im Playbook für die Commerce-Implementierung.
   * Suche nach anderen PHP-Problemen. Überprüfen Sie die ausgeführten Prozesse, indem Sie `ps aufx` in der CLI/Terminal ausführen. In der Terminal-Ausgabe werden Cron-Aufträge und -Prozesse angezeigt, die derzeit ausgeführt werden. Prüft die Ausgabe auf die Ausführungszeit der Prozesse. Wenn es eine Cron mit einer langen Ausführungszeit gibt, hängt die Cron möglicherweise. Informationen zu den Schritten zur Fehlerbehebung finden Sie unter [Langsame Leistung, langsame und lang laufende Crons](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) und [Cron-Auftrag steckt im Status „Wird ausgeführt](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) in der Commerce Support Knowledge Base.
1. Sobald eine potenzielle Ursache für das Problem identifiziert ist, wird SSH in die Umgebung geleitet, um weitere Untersuchungen durchzuführen. Anweisungen hierzu finden Sie unter [SSH in Ihre Umgebung](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh) im Handbuch zu Commerce in Cloud Manager.
1. Wenn Sie immer noch Schwierigkeiten haben, die Quelle zu identifizieren, überprüfen Sie die neuesten Trends, um Probleme mit aktuellen Code-Bereitstellungen oder Konfigurationsänderungen (z. B. neue Kundengruppen und große Änderungen am Katalog) zu identifizieren. Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder -Änderungen zu überprüfen.
1. Wenn Sie innerhalb eines angemessenen Zeitraums keine Lösung finden können, fordern Sie eine Erweiterung an oder setzen Sie die Site in den Wartungsmodus, falls noch nicht geschehen. Anweisungen hierzu finden Sie unter [Anfordern temporärer Größenanpassung](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) in der Wissensdatenbank für den Commerce-Support und [Aktivieren oder Deaktivieren ](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) Wartungsmodus) im Commerce-Installationshandbuch.
1. Wenn [upsize](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) die Site wieder in den normalen Betrieb versetzt, sollten Sie eine permanente Upsize anfordern (wenden Sie sich an Ihr Adobe-Accountteam) oder versuchen Sie, das Problem in Ihrem dedizierten Staging zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf die Services reduziert. Siehe [Belastungs- und Belastungstests](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) im Handbuch zu Commerce in Cloud Manager.
