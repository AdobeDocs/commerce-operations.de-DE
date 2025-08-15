---
title: 'Verwaltete Warnhinweise in Adobe Commerce: MariaDB-Warnhinweise'
description: Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie MariaDB-Warnhinweise für Adobe Commerce in [!DNL New Relic] erhalten. Die MariaDB-Warnhinweise überwachen eine hohe Abfragelast sowie übermäßige DML-Abfragen (Data Manipulation Language). Beides kann zu einem schlechteren Benutzererlebnis oder sogar zu Ausfallzeiten führen. Sie können zwei Arten von Warnhinweisen erhalten.
feature: Cache, Observability, Support, Tools and External Services
role: Admin
exl-id: d85af2e1-090c-4ad7-a898-3a3c4a5efe3b
source-git-commit: 18c8e466bf15957b73cd3cddda8ff078ebeb23b0
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Verwaltete Warnhinweise in Adobe Commerce: MariaDB-Warnhinweise

Dieser Artikel enthält Schritte zur Fehlerbehebung, wenn Sie in [!DNL New Relic] MariaDB-Warnhinweise für Adobe Commerce erhalten. Die MariaDB-Warnhinweise überwachen eine hohe Abfragelast sowie übermäßige DML-Abfragen (Data Manipulation Language). Beides kann zu einem schlechteren Benutzererlebnis oder sogar zu Ausfallzeiten führen. Sie können zwei Arten von Warnhinweisen erhalten:

* Warnung zu DML-Abfragen
* Wichtige DML-Abfragen

## Betroffene Produkte und Versionen

Adobe Commerce auf Cloud-Infrastruktur Pro Planarchitektur

## Problem

Sie erhalten in [!DNL New Relic] einen verwalteten Warnhinweis, wenn Sie sich bei [Verwaltete Warnhinweise für Adobe Commerce](managed-alerts-for-magento-commerce.md) angemeldet haben und einer oder mehrere der Warnhinweisschwellen überschritten wurden. Diese Warnhinweise wurden von Adobe entwickelt, um Kundinnen und Kunden mithilfe von Einblicken aus Support und Engineering einen Standardsatz zu bieten.

**Do!**

* Bricht jede geplante Bereitstellung ab, bis dieser Warnhinweis gelöscht wird.
* Setzen Sie Ihre Site sofort in den Wartungsmodus, wenn Ihre Site nicht mehr reagiert oder überhaupt nicht mehr reagiert. Anweisungen hierzu finden Sie [Aktivieren oder Deaktivieren des ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode)) im Commerce-Installationshandbuch. Fügen Sie Ihre IP-Adresse der Liste der von der Steuer befreiten IP-Adressen hinzu, um sicherzustellen, dass Sie weiterhin zur Fehlerbehebung auf Ihre Website zugreifen können. Anweisungen hierzu finden Sie unter [Liste der ausgenommenen IP-Adressen verwalten](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/maintenance-mode#maintain-the-list-of-exempt-ip-addresses).
* Beenden Sie alle Skripte, z. B. Importe, die die Ursache des Warnhinweises sein könnten, wenn die Site-Leistung beeinträchtigt ist.

**Tu&#39;s nicht!**

* Führen Sie Indexer oder zusätzliche Crons aus, die zusätzlichen Stress auf MariaDB verursachen können.
* Führen Sie alle wichtigen administrativen Aufgaben aus (z. B. Commerce-Admin, Datenimporte/-exporte).
* Leeren Sie den Cache.

## Lösung

**DML-Abfragen (Abfragen, die die Datenbank mithilfe von UPDATE, INSERT und DELETE ändern)**

Wenn Sie einen Warnhinweis „Kritische DML-Abfragen“ erhalten, beginnen Sie mit Schritt 1. Wenn Sie einen Warnhinweis zu DML-Abfragen erhalten, beginnen Sie mit Schritt 2.

1. Überprüfen, ob ein Adobe Commerce-Support-Ticket vorhanden ist. Anweisungen hierzu finden Sie in unserer Wissensdatenbank [Support-Tickets ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#track-support-case). Möglicherweise hat der Support einen Warnhinweis für einen [!DNL New Relic] Schwellenwert erhalten, ein Ticket erstellt und die Arbeit an dem Problem begonnen. Wenn kein Ticket vorhanden ist, erstellen Sie eines. Das Ticket sollte die folgenden Informationen enthalten:
   * Grund des Kontakts: Wählen Sie **[!UICONTROL New Relic MariaDB alert received]**.
   * Beschreibung des Warnhinweises
   * [[!DNL New Relic] Link zum Vorfall](https://docs.newrelic.com/docs/alerts-applied-intelligence/new-relic-alerts/alert-incidents/view-violation-event-details-incidents). Dies ist in Ihren [Verwaltete Warnhinweise für Adobe Commerce](managed-alerts-for-magento-commerce.md) enthalten.
1. Um die Ursache des Problems zu identifizieren, versuchen Sie, die XML-Abfragen zu identifizieren:
   1. Überprüfen Sie Ihre Datenbankvorgänge anhand der Schritte auf der Seite „Datenbanken[ von New Relic](https://docs.newrelic.com/docs/apm/apm-ui-pages/monitoring/databases-page-view-operations-throughput-response-time).
   1. Sortieren Sie nach **[!UICONTROL CALL COUNT]** und dann nach **[!UICONTROL OPERATION]**. Überprüfen Sie `INSERT`, `DELETE` und `UPDATE` Vorgänge.
   1. Achten Sie auf hohe Durchschnitte.
   1. Durchklicken, um Aufrufe von Datenbankvorgängen zu finden. Dadurch werden Transaktionen identifiziert, die diese Abfrage nach Zeit verwenden.
   1. Suchen Sie nach Code-Optimierungen oder operativen Optimierungen:
      * Code-Optimierungen: Achten Sie auf die Optimierung von Abfragen mit Masseneinfügungen/Aktualisierungen, die Minimierung der Indexnutzung oder die Drosselung von Code.
      * Operative Optimierungen: Abladung ressourcenintensiver Datenänderungen zur Verringerung der Traffic-Zeiten.
      * Zusätzliche Optimierungen: Stellen Sie sicher, dass Sie die neueste Version von ECE-Tools verwenden. Anweisungen hierzu finden Sie unter [Aktualisieren der Version ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) ECE-Tools im Handbuch Commerce on Cloud .
