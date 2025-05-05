---
title: 'Verwaltete Warnhinweise auf Adobe Commerce: Kritischer Warnhinweis bezüglich Speicher'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie einen kritischen Warnhinweis zu Arbeitsspeicher für Adobe Commerce in  [!DNL New Relic] erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
source-git-commit: dedaf4eeb9403945ada1a90a82f4be45ff98ec4e
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---

# Verwaltete Warnhinweise auf Adobe Commerce: Kritischer Warnhinweis bezüglich Speicher

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie in [!DNL New Relic] einen kritischen Warnhinweis zu Arbeitsspeicher für Adobe Commerce erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben.

![Kritischer Warnhinweis auf Festplatte](../../assets/managed-alerts/memory-critical-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Alle Versionen von Adobe Commerce auf Cloud-Infrastruktur Pro planen Architektur.

## Problem

Sie erhalten in [!DNL New Relic] einen verwalteten Warnhinweis, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kundinnen und Kunden mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

<u> **DO!** </u>

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) im Commerce-Installationshandbuch. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Verwalten der Liste von ausgenommenen IP](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)Adressen im Commerce-Installationshandbuch.

<u>**Tu&#39;s nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

Ihre Site kann nicht mehr reagieren (wenn Sie noch keinen Ausfall der Site feststellen), wenn Sie eine der „Nicht reagieren“-Aktionen durchführen, bevor Sie die Ursache des Warnhinweises untersucht und behoben haben.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

>[!WARNING]
>
>Da es sich um einen kritischen Warnhinweis handelt, wird dringend empfohlen, **Schritt 1** auszuführen, bevor Sie versuchen, das Problem zu beheben (Schritt 2 ab).

1. Überprüfen, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie unter [Support-Tickets ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) der Commerce Support Knowledge Base. Möglicherweise hat der Support bereits einen Warnhinweis für einen [!DNL New Relic] Schwellenwert erhalten, ein Ticket erstellt und die Arbeit an diesem Problem begonnen. Wenn kein Ticket vorhanden ist, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
   * Kontaktgrund: Auswahl **[!UICONTROL New Relic]** KRITISCHEN Warnhinweises
   * Beschreibung der Warnmeldung
   * [[!DNL New Relic] Link zum Vorfall](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihren [Verwaltete Warnhinweise für Adobe Commerce](managed-alerts-for-magento-commerce.md) enthalten.

1. Verwenden Sie [[!DNL New Relic]  Seite „Infrastruktur“ von APM](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/) um die speicherintensivsten Prozesse zu identifizieren. Anweisungen hierzu finden Sie auf [[!DNL New Relic]  Seite „Überwachung der Infrastruktur - Hosts: Registerkarte Prozesse](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes):
   * Wenn Services wie [!DNL Redis], MySQL oder PHP die Hauptquellen für den Speicherverbrauch sind, versuchen Sie Folgendes:
1. Vergewissern Sie sich, dass Sie die neuesten Versionen verwenden. Neuere Versionen können manchmal Speicherlecks beheben. Wenn Sie nicht die neueste Version verwenden, sollten Sie ein Upgrade in Erwägung ziehen. Anweisungen hierzu finden Sie unter [Service ändern](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) im Handbuch zu Commerce in Cloud Manager.
1. Wenn das Problem mit dem Service nicht versionsbezogen ist, versuchen Sie Folgendes:
1. **MySQL**: Überprüfen Sie, ob Probleme wie lange laufende Abfragen, nicht definierte Primäre Schlüssel und doppelte Indizes auftreten. Anweisungen hierzu finden Sie unter [Häufigste Datenbankprobleme in Adobe Commerce in Cloud](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/resolve-database-performance-issues.html) im Playbook für die Commerce-Implementierung.
1. **[!DNL Redis]**: Wenn [!DNL Redis] eine der Hauptquellen für den Speicherverbrauch ist, [ Sie ein Support-Ticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case).
1. **PHP**: Wenn PHP eine der Hauptquellen für den Speicherverbrauch ist, überprüfen Sie die laufenden Prozesse, indem Sie `ps aufx` in der CLI/Terminal ausführen. In der Terminal-Ausgabe werden Cron-Aufträge und -Prozesse angezeigt, die derzeit ausgeführt werden. Prüft die Ausgabe auf die Ausführungszeit der Prozesse. Wenn es eine Cron mit einer langen Ausführungszeit gibt, hängt die Cron möglicherweise. Informationen zu Schritten zur Fehlerbehebung finden Sie unter [Langsame Leistung, langsame und lang laufende Crons](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) und [Cron-Auftrag steckt im Status „Wird ausgeführt](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) in der Commerce Support Knowledge Base.
1. Wenn Sie immer noch Schwierigkeiten haben, die Ursache des Problems zu identifizieren, verwenden Sie [[!DNL New Relic] APMs Transaktionsseite](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) um Transaktionen mit Leistungsproblemen zu identifizieren:
   * Sortieren Sie Transaktionen nach aufsteigenden [!DNL Apdex]. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit auf die Antwortzeit Ihrer Web-Anwendungen und -Services. Ein [[!DNL Apdex score]](managed-alerts-for-magento-commerce-apdex-warning-alert.md) kann auf einen Engpass hinweisen (eine Transaktion mit einer höheren Antwortzeit). Normalerweise ist es die Datenbank, [!DNL &#x200B; Redis] oder PHP. Anweisungen hierzu finden Sie unter [[!DNL New Relic] Transaktionen mit höchster  [!DNL Apdex]  anzeigen](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/view-your-apdex-score#apdex-dissat).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Antwortzeit, dem zeitaufwendigsten Wert und anderen Schwellenwerten. Anweisungen hierzu finden Sie unter [[!DNL New Relic] [Spezifische Leistungsprobleme finden]](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems). Wenn Sie immer noch Schwierigkeiten haben, das Problem zu identifizieren, verwenden Sie [[!DNL New Relic] APMs Infrastrukturseite](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/).
1. Wenn Sie die Ursache für den erhöhten Speicherverbrauch nicht identifizieren können, überprüfen Sie die neuesten Trends, um Probleme mit aktuellen Code-Bereitstellungen oder Konfigurationsänderungen (z. B. neue Kundengruppen und große Änderungen am Katalog) zu identifizieren. Es wird empfohlen, die letzten 7 Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder -Änderungen zu überprüfen.
1. Wenn die oben genannten Methoden Ihnen nicht helfen, die Ursache und/oder Lösung innerhalb einer angemessenen Zeit zu finden, fordern Sie eine Erweiterung an oder setzen Sie die Site in den Wartungsmodus, falls Sie dies noch nicht getan haben. Anweisungen hierzu finden Sie [Anfordern temporärer Größenänderungen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize) in der Wissensdatenbank für den Commerce-Support und [Aktivieren oder Deaktivieren des ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)) im Commerce-Installationshandbuch.
1. Wenn die Aktualisierung zu einem normalen Betrieb der Site führt, sollten Sie eine permanente Aktualisierung anfordern (wenden Sie sich an Ihr Adobe-Accountteam) oder versuchen Sie, das Problem in Ihrem dedizierten Staging zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf die Services reduziert. Siehe [Belastungs- und Belastungstests](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/staging-and-production#load-and-stress-testing) im Handbuch zu Commerce in Cloud Manager.
