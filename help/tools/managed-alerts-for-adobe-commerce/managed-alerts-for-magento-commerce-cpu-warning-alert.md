---
title: 'Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für CPU'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie in [!DNL New Relic] einen CPU-Warnhinweis für Adobe Commerce erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben.
feature: Cache, Marketing Tools, Observability, Support, Tools and External Services
role: Admin
exl-id: 0abcf21b-2ccf-42f5-8823-99282fccadcf
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
  - id: 4239b8a6-e74f-567d-a7a5-b98b9ead0ea4
    internal-label: Observability
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '803'
ht-degree: 0%
---
# Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für CPU

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie in [!DNL New Relic] einen CPU-Warnhinweis für Adobe Commerce erhalten. Sofortiges Handeln ist erforderlich, um das Problem zu beheben. Je nach ausgewähltem Benachrichtigungskanal für Warnhinweise sieht der Warnhinweis etwa wie folgt aus.

![CPU-Warnhinweis](../../assets/managed-alerts/cpu-warning-magento-managed.png){width="500"}

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur

## Problem

Sie erhalten einen Warnhinweis in [!DNL New Relic], wenn Sie sich für [Verwaltete Warnhinweise für Adobe Commerce](managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kundinnen und Kunden mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

<u> **DO!** </u>

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site vollständig nicht reagiert. Anweisungen hierzu finden Sie [Aktivieren oder Deaktivieren des &#x200B;](/help/installation/tutorials/maintenance-mode.md)) im Commerce-Installationshandbuch. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Verwalten der Liste von ausgenommenen IP](/help/installation/tutorials/maintenance-mode.md#maintain-the-list-of-exempt-ip-addresses)Adressen) im Commerce-Installationshandbuch.

<u>**Tu&#39;s nicht!**</u>

* Starten Sie zusätzliche Marketing-Kampagnen, die zusätzliche Seitenansichten auf Ihre Site bringen können.
* Führen Sie Indexer oder zusätzliche Crons aus, was zu zusätzlichen Belastungen für CPU oder die Festplatte führen kann.
* Führen Sie alle wichtigen administrativen Aufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

## Lösung

Führen Sie diese Schritte aus, um die Ursache zu identifizieren und zu beheben.

1. Verwenden Sie [[!DNL New Relic]  Seite „Transaktion“ von APM](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems) um Transaktionen mit Leistungsproblemen zu identifizieren:
   * Sortieren Sie Transaktionen nach aufsteigenden [!DNL Apdex]. [[!DNL Apdex]](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction) bezieht sich auf die Benutzerzufriedenheit auf die Antwortzeit Ihrer Web-Anwendungen und -Services. [Ein niedriger  [!DNL Apdex] Score](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce) kann auf einen Engpass hinweisen (eine Transaktion mit einer höheren Antwortzeit). Normalerweise ist es die Datenbank, [!DNL Redis] oder PHP. Anweisungen hierzu finden Sie unter [!DNL New Relic] [Transaktionen mit höchster  [!DNL Apdex]  anzeigen](https://docs.newrelic.com/docs/apm/new-relic-apm/apdex/apdex-measure-user-satisfaction/#apdex-dissat).
   * Sortieren Sie Transaktionen nach dem höchsten Durchsatz, der langsamsten durchschnittlichen Reaktionszeit, dem zeitaufwendigsten Wert und anderen Schwellenwerten. Anweisungen hierzu finden Sie unter [[!DNL New Relic] Suchen spezifischer Leistungsprobleme](https://docs.newrelic.com/docs/apm/applications-menu/monitoring/transactions-page-find-specific-performance-problems).
1. Wenn Sie immer noch versuchen, die Quelle zu identifizieren, verwenden Sie [[!DNL New Relic] APMs Infrastrukturseite](https://docs.newrelic.com/docs/infrastructure/infrastructure-data/infrastructure-ui-pages/infra-hosts-ui-page/) um ressourcenintensive Services zu identifizieren. Anweisungen hierzu finden Sie auf [!DNL New Relic] Seite [Überwachung von Hosts der Infrastruktur: [!UICONTROL Processes tab]](https://docs.newrelic.com/docs/infrastructure/infrastructure-ui-pages/infra-hosts-ui-page/#processes).
1. Wenn Sie die Quelle identifizieren, SSH in die Umgebung, um weiter zu untersuchen. Anweisungen hierzu finden Sie unter [SSH in Ihre Umgebung](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/secure-connections#ssh) im Handbuch zu Commerce in Cloud Manager.
1. Wenn Sie immer noch damit kämpfen, die Quelle zu identifizieren:
   * Überprüfen Sie die neuesten Trends, um Probleme mit aktuellen Code-Bereitstellungen oder Konfigurationsänderungen zu identifizieren (z. B. neue Kundengruppen und große Änderungen am Katalog). Es wird empfohlen, die letzten sieben Tage der Aktivität auf Korrelationen in Code-Bereitstellungen oder -Änderungen zu überprüfen.
   * Erwägen Sie, nach flachen Katalogen zu suchen und sie zu deaktivieren. Anweisungen hierzu finden Sie unter [Langsame Leistung, langsame und lang laufende Crons](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/slow-performance-slow-and-long-running-crons) in der Commerce Support Knowledge Base.
   * Wenn Sie einen DDoS-Angriff vermuten, versuchen Sie, Bot-Traffic zu blockieren. Anweisungen hierzu finden Sie unter [Wie Sie bösartigen Traffic für Adobe Commerce auf Fastly-Ebene blockieren](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/how-to/block-malicious-traffic-for-magento-commerce-on-fastly-level) in der Wissensdatenbank für den Commerce-Support.
1. Wenn das Problem vorübergehend zu sein scheint, führen Sie Schritte zur Risikominderung durch, z. B. eine Vergrößerung oder setzen Sie die Site in den Wartungsmodus. Anweisungen hierzu finden Sie unter [Anfordern temporärer Größenanpassung](https://experienceleague.adobe.com/de/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-request-temporary-adobe-commerce-on-cloud-infrastructure-upsize) in der Wissensdatenbank für den Commerce-Support und [Aktivieren oder Deaktivieren &#x200B;](/help/installation/tutorials/maintenance-mode.md) Wartungsmodus) im Commerce-Installationshandbuch. Wenn die Aktualisierung zu einem normalen Betrieb der Site führt, fordern Sie ggf. eine permanente Aktualisierung an (wenden Sie sich an Ihr Adobe-Accountteam) oder versuchen Sie, das Problem in Ihrem dedizierten Staging zu reproduzieren, indem Sie einen Lasttest durchführen und Abfragen optimieren oder Code verwenden, der den Druck auf die Services reduziert. Anweisungen hierzu finden Sie unter [- und Belastungstests &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/staging-and-production#load-and-stress-testing) Handbuch zu Commerce in Cloud Manager.
