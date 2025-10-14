---
title: Verwaltete Warnhinweise zu kritischen Warnhinweisen auf Adobe Commerce [!DNL Redis] Arbeitsspeicher
description: Dieser Artikel enthält Schritte zur Fehlerbehebung für den Fall, dass Sie  [!DNL Redis]  wichtigen Warnhinweis für Adobe Commerce in erhalten [!DNL New Relic]. Sofortiges Handeln ist erforderlich, um das Problem zu lösen.
feature: Cache, Categories, Observability, Services, Support, Tools and External Services, Variables
role: Admin
exl-id: 1233889e-8c02-4ad6-b12c-683010b7bf35
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---

# Verwaltete Warnhinweise auf Adobe Commerce: Kritischer Warnhinweis zu [!DNL Redis] Arbeitsspeicher

Dieser Artikel enthält Schritte zur Fehlerbehebung für den Fall, dass Sie in [!DNL Redis] einen kritischen Warnhinweis zu [!DNL New Relic] Arbeitsspeicher für Adobe Commerce erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu lösen. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![new_relic_redis_memory_critical.png](../../assets/managed-alerts/new_relic_redis_memory_critical.png)

## Betroffene Produkte und Versionen

Alle Versionen von Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur

## Problem

Sie erhalten einen Warnhinweis in [!DNL New Relic], wenn Sie sich für [Verwaltete Warnhinweise für Adobe Commerce](managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Händlern mithilfe von Einblicken aus Support und Engineering einen Standardsatz von Warnhinweisen bereitzustellen.

**<u>Do!</u>**

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Wartungsmodus aktivieren oder deaktivieren](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode) im Commerce-Installationshandbuch. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Verwalten der Liste von ausgenommenen IP](https://experienceleague.adobe.com/de/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses)Adressen) im Commerce-Installationshandbuch.

**<u>Tu&#39;s nicht!</u>**

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben durch (d. h. wichtige Aktionen im Commerce-Admin, wie z. B. Datenimporte/-exporte, Leeren von Medien, Speichern von Kategorien mit einer großen Anzahl zugewiesener Produkte und Massenaktualisierungen).
* Leeren Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

**Da es sich um einen kritischen Warnhinweis handelt, wird dringend empfohlen, Schritt 1 abzuschließen, bevor Sie versuchen, das Problem zu beheben (Schritt 2 ab).**

1. Überprüfen, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie unter [Support-Tickets nachverfolgen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case) in der Commerce Support Knowledge Base. Möglicherweise hat der Support bereits einen Warnhinweis für einen [!DNL New Relic] Schwellenwert erhalten, ein Ticket erstellt und die Arbeit an diesem Problem begonnen. Wenn kein Ticket vorhanden ist, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:

   * Grund des Kontakts: Wählen Sie **[!UICONTROL New Relic CRITICAL alert received]**.
   * Beschreibung des Warnhinweises
   * [[!DNL New Relic] Link zum Vorfall](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents/). Dies ist in Ihren [Verwaltete Warnhinweise für Adobe Commerce](managed-alerts-for-magento-commerce.md) enthalten.

1. Wenn kein Support-Ticket vorhanden ist, überprüfen Sie, ob [!DNL Redis] Verwendete Speicher zunimmt oder abnimmt, indem Sie zur Seite [one.newrelic.com](https://login.newrelic.com) > **[!UICONTROL Infrastructure]** > **[!UICONTROL Third-party services]** wechseln. Wählen Sie das [!DNL Redis]-Dashboard aus. Wenn er stabil ist oder zunimmt, [&#x200B; Sie ein Support-Ticket](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case), um den Cluster vergrößern zu lassen, oder erhöhen Sie das `maxmemory` auf die nächste Ebene.
1. Wenn Sie die Ursache für den erhöhten [!DNL Redis]-Speicherverbrauch nicht identifizieren können, überprüfen Sie die neuesten Trends, um Probleme mit aktuellen Code-Bereitstellungen oder Konfigurationsänderungen (z. B. neue Kundengruppen und große Änderungen am Katalog) zu identifizieren. Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder -Änderungen zu überprüfen.
1. Überprüfen Sie, ob sich Drittanbietererweiterungen falsch verhalten:

   * Versuchen Sie, eine Korrelation mit den kürzlich installierten Erweiterungen von Drittanbietern und dem Zeitpunkt, zu dem das Problem begann, zu finden.
   * Überprüfen Sie Erweiterungen, die sich möglicherweise auf den Adobe Commerce-Cache auswirken und dazu führen können, dass der Cache schnell wächst. Dies betrifft beispielsweise benutzerdefinierte Layout-Blöcke, das Überschreiben der Cache-Funktionalität und das Speichern großer Datenmengen im Cache.

1. Wenn es keine Anzeichen für fehlerhafte Erweiterungen gibt, installieren [&#x200B; die neuesten Patches, um Probleme  [!DNL Redis]  Adobe Commerce in der Cloud-Infrastruktur zu &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/install-latest-patches-to-fix-magento-redis-issues).
1. Wenn Ihnen die obigen Schritte nicht dabei helfen, die Ursache des Problems zu identifizieren oder zu beheben, sollten Sie den L2-Cache aktivieren, um den Netzwerk-Traffic zwischen der App und [!DNL Redis] zu reduzieren. Allgemeine Informationen zum L2-Cache finden Sie unter [L2-Caching in der Adobe Commerce-Anwendung](https://experienceleague.adobe.com/de/docs/commerce-operations/configuration-guide/cache/level-two-cache) im Commerce-Konfigurationshandbuch. Um den L2-Cache für die Cloud-Infrastruktur zu aktivieren, versuchen Sie Folgendes:

   * Aktualisieren Sie die ECE-Tools, wenn diese unter Version 2002.1.2 liegen.
   * Konfigurieren Sie den L2-Cache mithilfe [Variable REDIS\_BACKEND verwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) und aktualisieren Sie die `.magento.env.yaml`:

   ```yaml
   stage:
       deploy:
           REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
   ```
