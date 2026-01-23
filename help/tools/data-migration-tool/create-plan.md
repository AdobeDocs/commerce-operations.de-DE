---
title: Erstellen eines Datenmigrationsplans
description: Erfahren Sie, wie Sie einen Datenmigrationsplan für das Upgrade von Magento 1 auf Magento 2 erstellen. Planen und testen Sie Ihre Migration, um Probleme zu vermeiden.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Erstellen eines Datenmigrationsplans

Um erfolgreich zu migrieren und Probleme zu vermeiden, müssen Sie Ihre Migration gründlich planen und testen.

## Bevor Sie beginnen: Erwägen Sie ein Upgrade

Die Migration ist ein guter Zeitpunkt, um ernsthafte Änderungen vorzunehmen und Ihre Site für das nächste Wachstumsniveau vorzubereiten. Überlegen Sie, ob Ihre neue Site mit zusätzlicher Hardware oder einer erweiterten Topologie mit besseren Caching-Ebenen entwickelt werden muss.

## Schritt 1: Erweiterungen auf der aktuellen Site überprüfen

* Welche Erweiterungen haben Sie installiert?

* Haben Sie festgestellt, ob Sie alle diese Erweiterungen auf Ihrer neuen Site benötigen? Es könnte alte geben, die Sie sicher entfernen können.

* Haben Sie festgestellt, ob Magento 2-Versionen Ihrer Erweiterungen vorhanden sind? Besuchen Sie [Commerce Marketplace](https://commercemarketplace.adobe.com/) um die neuesten Versionen zu finden oder wenden Sie sich an Ihren Erweiterungsanbieter.

* Welche Datenbank-Assets aus Ihren Erweiterungen möchten Sie migrieren?

## Schritt 2: Erstellen und Vorbereiten des Stores auf die Migration

* Richten Sie ein Magento 2-Hardwaresystem mit einer Topologie und einem Design ein, die mindestens Ihrem bestehenden Magento 1-System entspricht

* Installieren Sie Magento 2 (mit allen Modulen dieser Version) und den [!DNL Data Migration Tool] auf einem System, das die [Systemanforderungen](../../installation/system-requirements.md) erfüllt

* Passen Sie den [!DNL Data Migration Tool]-Code an, um bestimmte Daten zu überspringen (z. B. CMS-Seiten, Verkaufsregeln) oder Anpassungen während der Migration zu konvertieren. Weitere Informationen zur Funktionsweise der Migration finden [!DNL Data Migration Tool] in der [&#x200B; der &#x200B;](technical-specification.md)

## Schritt 3: Probelauf

Bevor Sie mit der Migration in der Produktionsumgebung beginnen, führen Sie alle Migrationsschritte in Ihrer Testumgebung durch.

Führen Sie bei solchen Migrationstests die folgenden Schritte aus:

* Kopieren Sie Ihren Magento 1-Store auf einen Staging-Server

* Vollständige Migration des replizierten Magento 1-Stores zu Magento 2

* Testen Sie Ihren neuen Store gründlich

## Schritt 4: Starten Sie Ihre Migration

1. Stellen Sie sicher, dass der [!DNL Data Migration Tool] über Netzwerkzugriff verfügt, um eine Verbindung zu Magento 1- und Magento 2-Datenbanken herzustellen. Öffnen Sie die entsprechenden Ports in Ihrer Firewall.

1. Beenden Sie alle Aktivitäten im Admin-Panel von Magento 1 (mit Ausnahme von Order Management), z. B. den Versand, die Erstellung von Rechnungen und Gutschriften. Die Liste der zulässigen Aktivitäten kann erweitert werden, indem die Einstellungen des Delta-Modus im [!DNL Data Migration Tool] angepasst werden.

   >[!NOTE]
   >
   >Setzen Sie diese Aktivitäten erst fort, wenn Ihr Magento 2-Store live geschaltet wird.

1. Es wird empfohlen, alle Magento 1-Cron-Aufträge zu stoppen.

   Wenn einige Aufträge während der Migration ausgeführt werden müssen, stellen Sie sicher, dass sie keine Datenbankentitäten auf eine Weise erstellen oder ändern, die der Delta-Modus nicht verarbeiten kann.

   Beispielsweise verschiebt der `enterprise_salesarchive_archive_orders` Cron-Auftrag alte Aufträge in das Archiv. Die Ausführung dieses Auftrags während der Migration ist sicher, da der Delta-Modus diesen Auftrag erkennt und die archivierten Aufträge ordnungsgemäß verarbeitet.

1. Verwenden Sie die [!DNL Data Migration Tool], um Einstellungen und Websites zu migrieren.

1. Kopieren Sie Ihre Magento 1-Mediendateien nach Magento 2.

   Kopieren Sie diese Dateien manuell aus dem `magento1-root/media` Verzeichnis nach `magento2-root/pub/media`.

1. Verwenden Sie die [!DNL Data Migration Tool], um Ihre Daten aus der Magento 1-Datenbank stapelweise in die Magento 2-Datenbank zu kopieren.

   Wenn einige Ihrer Erweiterungen Daten enthalten, die Sie migrieren möchten, müssen Sie diese Erweiterungen möglicherweise installieren, die für Magento 2 angepasst sind. Falls die Erweiterungen in der Magento 2-Datenbank eine andere Struktur aufweisen, verwenden Sie die mit der [!DNL Data Migration Tool] bereitgestellten Zuordnungsdateien.

1. Indizieren Sie alle Magento 2-Indexer neu. Weitere Informationen finden Sie [Indexer verwalten](../../configuration/cli/manage-indexers.md) im _Konfigurationshandbuch_.

## Schritt 5: Nehmen Sie Änderungen an den migrierten Daten vor (falls erforderlich)

Manchmal empfiehlt es sich, den Magento 2-Store nach der Migration mit einer anderen Katalogstruktur, unterschiedlichen Vertriebsregeln und anderen CMS-Seiten zu verwenden.

Es ist wichtig, bei der Bearbeitung manueller Datenänderungen Vorsicht walten zu lassen. Fehler verursachen Fehler im folgenden inkrementellen Schritt zur Datenmigration.

Beispiel: Ein aus Magento 2 gelöschtes Produkt: das Produkt, das in Ihrem Magento 1-Live-Store gekauft wurde und nicht mehr in Ihrem Magento 2-Store verfügbar ist. Die Übertragung von Daten über einen solchen Kauf kann einen Fehler verursachen, wenn der [!DNL Data Migration Tool] im Delta-Modus ausgeführt wird.

## Schritt 6: Inkrementelle Daten aktualisieren

Verwenden Sie nach der Migration von Daten den Delta-Modus, um inkrementelle Aktualisierungen von Magento 1 (z. B. neue Bestellungen, Überprüfungen und Kundenprofiländerungen) zu Magento 2 zu erfassen und zu übertragen.

* Inkrementelle Migration starten; Aktualisierungen werden kontinuierlich ausgeführt. Sie können die Übertragung von Updates jederzeit unterbrechen, indem Sie `Ctrl+C` drücken.

* Testen Sie in diesem Zeitraum Ihre Magento 2-Site, um Probleme so schnell wie möglich zu beheben. Wenn Probleme auftreten, drücken Sie `Ctrl+C`, um die inkrementelle Migration zu stoppen und nach Behebung der Probleme erneut zu starten.

>[!NOTE]
>
>Wenn Sie Ihre Magento 2-Site testen und den Migrationsprozess gleichzeitig ausführen, können Warnhinweise zur Volumeprüfung angezeigt werden. Dies geschieht, weil Sie in Magento 2 Entitäten erstellen, die nicht in der Magento 1-Instanz vorhanden sind.

## Schritt 7: Live-Schaltung

Sobald Ihre Magento 2-Site vollständig migriert ist und normal funktioniert, schließen Sie die Umstellung ab:

1. Setzen Sie Ihr Magento 1-System in den Wartungsmodus (DOWNTIME STARTS).

1. Drücken Sie Strg+C im Befehlsfenster des Migrations-Tools, um inkrementelle Aktualisierungen zu stoppen.

1. Starten Sie Ihre Magento 2 Cron-Aufträge.

1. Indizieren Sie in Ihrem Magento 2-System den Aktienindexer neu. Weitere Informationen finden Sie unter [Indexer verwalten](../../configuration/cli/manage-indexers.md) im _Konfigurationshandbuch_.

1. Verwenden Sie ein Tool Ihrer Wahl, und rufen Sie Seiten in Ihrem Magento 2-System auf, um Seiten vor Kunden zwischenzuspeichern, die Ihre Storefront verwenden.

1. Führen Sie eine abschließende Überprüfung Ihrer Magento 2-Site durch.

1. Ändern Sie DNS, Load-Balancer usw., um auf neue Produktions-Hardware zu verweisen (DOWNTIME ENDS).

1. Der Magento 2-Store ist jetzt einsatzbereit. Sie und Ihre Kunden können alle Aktivitäten fortsetzen.
