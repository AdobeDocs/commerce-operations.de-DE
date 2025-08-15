---
title: Verwaltete Warnhinweise für Adobe Commerce
description: Wenn Sie Adobe Commerce on Cloud Infrastructure Pro Plan Architecture-Kunde sind, können Sie verwaltete Warnhinweise verwenden, um den Zustand Ihrer Site zu verstehen. Wenn Sie Adobe Commerce on Cloud Infrastructure Starter Plan Architecture-Kunde sind, erhalten Sie nur Warnhinweise zu den  [!DNL Apdex]  und Fehlerquoten.
feature: Observability, Support, Tools and External Services
role: Admin
exl-id: 3fc4b07f-4e27-4833-97a9-cf9741ae5648
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Verwaltete Warnhinweise für Adobe Commerce


Wir haben wichtige Dashboards und Warnhinweise eingerichtet, die Ihnen dabei helfen zu verstehen, wann Ihre Website kritische Speicher- und [!DNL Apdex] erreicht (Zufriedenheit der Benutzer mit der Reaktionszeit von Anwendungen und Services). Dies kann Ihnen helfen, Maßnahmen zu ergreifen, bevor Sie langsame Antwortzeiten oder einen Ausfall bemerken. Sie können die Warnungen mit den unten aufgeführten Artikeln beheben. Bevor Sie die Warnhinweise verwenden können, richten Sie zunächst Benachrichtigungskanäle ein. Siehe [[!DNL New Relic] Konfigurieren von Benachrichtigungskanälen](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/monitor/new-relic/new-relic-service) im Handbuch zu Commerce in Cloud Cloud .

>[!NOTE]
>
>Wenn verwaltete Warnhinweise für die Adobe Commerce-Warnhinweisrichtlinie nicht verfügbar sind, kann dies darauf zurückzuführen sein, dass dieses Konto neu erstellt wurde oder [!DNL New Relic] vor kurzem konfiguriert wurde. Jeden Dienstag wird ein Prozess ausgeführt, um die Warnmeldungsrichtlinie zu diesen Konten hinzuzufügen. Die Warnmeldungsrichtlinie sollte Ihnen am Tag nach der Ausführung des nächsten Prozesses zur Verfügung stehen. Wenn die Richtlinie immer noch fehlt, [ Sie eine Adobe Commerce-Support-Anfrage ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-case) und geben Sie Ihre Projekt-ID an.

Unten in der Tabelle finden Sie Links zu den KB-Artikeln mit Schritten zur Fehlerbehebung bei diesen Warnhinweisen:

* Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für CPU
* Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis für CPU
* Verwaltete Warnhinweise für Adobe Commerce: Speicherwarnhinweis
* Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis zum Speicher
* Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis [!DNL Apdex]
* Verwaltete Warnhinweise für Adobe Commerce: [!DNL Apdex] Warnhinweis
* Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis bezüglich Festplatte
* Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis auf Festplatte
* Verwaltete Warnhinweise in Adobe Commerce: MariaDB-Warnhinweise
* Verwaltete Warnhinweise auf Adobe Commerce: Warnhinweis bezüglich [!DNL Redis] Arbeitsspeichers
* Verwaltete Warnhinweise auf Adobe Commerce: Kritischer Warnhinweis zu [!DNL Redis] Arbeitsspeicher

>[!NOTE]
>
>Die festgelegten Schwellenwerte für Warnhinweise und kritische Warnhinweise basieren auf Untersuchungen, die wir auf der Grundlage historischer Leistungsdaten aus unserem Kundenstamm durchführen, und spiegeln die neuesten Erkenntnisse der Support- und Engineering-Teams von Adobe Commerce wider. Beachten Sie, dass sich diese Schwellenwerte auf der Grundlage aktueller, laufender Analysen ändern können. Der typische Warnhinweisfluss besteht darin, Warnhinweise zu erhalten, die hinsichtlich ihres Schweregrads niedriger oder höher sind. Daher erhalten Sie wahrscheinlich einen Warnhinweis, bevor Sie einen kritischen Warnhinweis erhalten. Informationen zu den Schritten zur Fehlerbehebung finden Sie in den Links zu den Artikeln.

| Schweregrad | CPU | Arbeitsspeicher | Festplatte | [!DNL Apdex] | MariaDB | [!DNL Redis] | Artikel zur Fehlerbehebung |
|----------|-----|--------|------|-------|---------|--------------|-------------------------|
| Warnung | ✅ |        |      |       |         |              | [Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis für CPU](managed-alerts-for-magento-commerce-cpu-warning-alert.md) |
| Kritisch | ✅ |        |      |       |         |              | [Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis für CPU](managed-alerts-on-magento-commerce-cpu-critical-alert.md) |
| Warnung |     | ✅ |      |       |         |              | [Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis bezüglich des Arbeitsspeichers](managed-alerts-for-magento-commerce-memory-warning-alert.md) |
| Kritisch |     | ✅ |      |       |         |              | [Verwaltete Warnhinweise für Adobe Commerce: Kritischer Warnhinweis im Arbeitsspeicher](managed-alerts-on-magento-commerce-memory-critical-alert.md) |
| Warnung |     |        |      | ✅ |         |              | [Verwaltete Warnhinweise für Adobe Commerce: [!DNL Apdex] Warnhinweis](managed-alerts-for-magento-commerce-apdex-warning-alert.md) |
| Kritisch |     |        |      | ✅ |         |              | [Verwaltete Warnhinweise für Adobe Commerce: [!DNL Apdex] Kritischer Warnhinweis](managed-alerts-for-magento-commerce-apdex-critical-alert.md) |
| Warnung |     |        | ✅ |       |         |              | [Verwaltete Warnhinweise für Adobe Commerce: Warnhinweis bezüglich Festplatte](managed-alerts-for-magento-commerce-disk-warning-alert.md) |
| Kritisch |     |        | ✅ |       |         |              | [Verwaltete Warnhinweise für Adobe Commerce: kritischer Warnhinweis auf Festplatte](managed-alerts-for-magento-commerce-disk-critical-alert.md) |
| Warnung und Kritisch |     |        |      |       | ✅ |              | [Verwaltete Warnhinweise in Adobe Commerce: MariaDB-Warnhinweise](managed-alerts-on-magento-commerce-mariadb-alerts.md) |
| Warnung |     |        |      |       |         | ✅ | [Verwaltete Warnhinweise zu Adobe Commerce: [!DNL Redis] Warnhinweis bezüglich Arbeitsspeicher](managed-alerts-on-magento-commerce-redis-memory-warning-alert.md) |
| Kritisch |     |        |      |       |         | ✅ | [Verwaltete Warnhinweise zu Adobe Commerce: [!DNL Redis] Kritischer Warnhinweis für Speicher](managed-alerts-on-magento-commerce-redis-memory-critical-alert.md) |
