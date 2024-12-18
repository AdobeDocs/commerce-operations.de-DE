---
title: Erstellen eines Datenmigrationsplans
description: Führen Sie die folgenden Schritte aus, um einen Datenmigrationsplan zu erstellen, um ein erfolgreiches Upgrade von Magento 1 auf Magento 2 sicherzustellen.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# Erstellen eines Datenmigrationsplans

Um erfolgreich zu migrieren und Probleme zu vermeiden, müssen Sie Ihre Migration sorgfältig planen und testen.

## Bevor Sie beginnen: Erwägen Sie ein Upgrade

Migration ist ein perfekter Moment, um ernsthafte Änderungen vorzunehmen und Ihre Site für das nächste Wachstumsniveau vorzubereiten. Überlegen Sie, ob Ihre neue Site mit mehr Hardware oder einer erweiterten Topologie mit besseren Caching-Ebenen entwickelt werden muss.

## Schritt 1: Erweiterungen auf der aktuellen Site überprüfen

* Welche Erweiterungen haben Sie installiert?

* Haben Sie festgestellt, ob Sie alle diese Erweiterungen auf Ihrer neuen Site benötigen? Es könnte alte geben, die Sie sicher entfernen können.

* Haben Sie festgestellt, ob Magento 2-Versionen Ihrer Erweiterungen existieren? Besuchen Sie [Commerce Marketplace] um die neuesten Versionen zu finden oder wenden Sie sich an Ihren Erweiterungsanbieter.

* Welche Datenbank-Assets aus Ihren Erweiterungen möchten Sie migrieren?

## Schritt 2: Erstellen und Vorbereiten des Stores auf die Migration

* Richten Sie ein Magento 2-Hardwaresystem mit Topologie und Design ein, das mindestens Ihrem bestehenden Magento 1-System entspricht

* Installieren Sie Magento 2.x (mit allen Modulen dieser Version) und den [!DNL Data Migration Tool] auf einem System, das die [Systemanforderungen](../../installation/system-requirements.md) erfüllt

* Nehmen Sie Ihre benutzerdefinierten Anpassungen am [!DNL Data Migration Tool] vor, falls Sie einige Daten nicht migrieren müssen (z. B. CMS-Seiten, Vertriebsregeln) oder Ihre Magento-Anpassung während der Migration konvertieren möchten. Lesen Sie die [Technische Spezifikation“ des [!DNL Data Migration Tool], ](technical-specification.md) besser zu verstehen, wie die Migration von innen heraus funktioniert

## Schritt 3: Probelauf

Bevor Sie mit der Migration in die Produktionsumgebung beginnen, sollten Sie alle Migrationsschritte in Ihrer Testumgebung durchlaufen.

Führen Sie bei solchen Migrationstests die folgenden Schritte aus:

* Kopieren Sie Ihren Magento 1-Speicher auf einen Staging-Server

* Vollständige Migration des replizierten Magento 1-Speichers zu Magento 2

* Testen Sie Ihren neuen Store gründlich

## Schritt 4: Starten Sie Ihre Migration

1. Stellen Sie sicher, dass der [!DNL Data Migration Tool] über Netzwerkzugriff verfügt, um eine Verbindung zu Magento 1- und Magento 2-Datenbanken herzustellen. Öffnen Sie die entsprechenden Ports in Ihrer Firewall.

1. Beenden Sie alle Aktivitäten im Admin Panel von Magento 1.x (mit Ausnahme der Bestellverwaltung), wie z. B. Versand, Rechnungserstellung und Gutschriften. Die Liste der zulässigen Aktivitäten kann durch Anpassen der Einstellungen des Delta-Modus im [!DNL Data Migration Tool] erweitert werden.

   >[!NOTE]
   >
   >Sie dürfen diese Aktivitäten erst fortsetzen, wenn Ihr Magento 2-Speicher live geschaltet wird.

1. Es wird empfohlen, alle Magento 1.x-Cron-Aufträge zu stoppen.

   Wenn während der Migration jedoch einige Aufträge ausgeführt werden müssen, stellen Sie sicher, dass keine neuen Datenbankentitäten erstellt werden und dass die vorhandenen nicht so geändert werden, dass sie vom Delta-Modus verarbeitet werden können.

   Beispielsweise verschiebt der `enterprise_salesarchive_archive_orders` Cron-Auftrag alte Aufträge in das Archiv. Die Ausführung dieses Auftrags während der Migration ist sicher, da der Delta-Modus diesen Auftrag erkennt und die archivierten Aufträge ordnungsgemäß verarbeitet.

1. Verwenden Sie die [!DNL Data Migration Tool], um Einstellungen und Websites zu migrieren.

1. Kopieren Sie Ihre Magento 1.x-Mediendateien auf Magento 2.x.

   Sie müssen diese Dateien manuell aus dem `magento1-root/media` in `magento2-root/pub/media` kopieren.

1. Verwenden Sie die [!DNL Data Migration Tool], um Ihre Daten aus der Magento 1-Datenbank in die Magento 2-Datenbank zu kopieren.

   Wenn einige Ihrer Erweiterungen Daten enthalten, die Sie migrieren möchten, müssen Sie diese Erweiterungen möglicherweise installieren, die für Magento 2 angepasst sind. Wenn die Erweiterungen in der Magento 2-Datenbank eine andere Struktur aufweisen, verwenden Sie die mit dem [!DNL Data Migration Tool] bereitgestellten Zuordnungsdateien.

1. Indizieren Sie alle Magento 2.x-Indexer neu. Weitere Informationen finden Sie unter [Indexer verwalten](../../configuration/cli/manage-indexers.md) im _Konfigurationshandbuch_.

## Schritt 5: Nehmen Sie Änderungen an den migrierten Daten vor (falls erforderlich)

Manchmal empfiehlt es sich, nach der Migration Ihren Magento 2-Store mit unterschiedlicher Katalogstruktur, unterschiedlichen Verkaufsregeln und unterschiedlichen CMS-Seiten zu verwenden.

Es ist wichtig, bei der Bearbeitung manueller Datenänderungen Vorsicht walten zu lassen. Fehler verursachen Fehler im folgenden inkrementellen Schritt zur Datenmigration.

Zum Beispiel ein Produkt, das von Magento 2 gelöscht wurde: das Produkt, das in Ihrem Live-Magento 1-Store gekauft wurde und nicht mehr in Ihrem Magento 2-Store verfügbar ist. Die Übertragung von Daten über einen solchen Kauf kann einen Fehler verursachen, wenn der [!DNL Data Migration Tool] im Delta-Modus ausgeführt wird.

## Schritt 6: Inkrementelle Daten aktualisieren

Nach der Migration von Daten müssen Sie inkrementell Datenaktualisierungen erfassen, die im Magento 1-Speicher hinzugefügt wurden (z. B. neue Bestellungen, Überprüfungen und Änderungen in Kundenprofilen), und diese Aktualisierungen mithilfe des Delta-Modus in den Magento 2-Speicher übertragen.

* Inkrementelle Migration starten; Aktualisierungen werden kontinuierlich ausgeführt. Sie können die Übertragung von Updates jederzeit unterbrechen, indem Sie `Ctrl+C` drücken.

* Testen Sie Ihre Magento 2-Site während dieser Zeit, um alle Probleme so schnell wie möglich zu erfassen. Wenn Probleme auftreten, drücken Sie `Ctrl+C`, um die inkrementelle Migration zu stoppen und nach Behebung der Probleme erneut zu starten.

>[!NOTE]
>
>Wenn Sie Ihre Magento 2-Site testen und gleichzeitig den Migrationsprozess ausführen, können Warnhinweise zur Volumeprüfung angezeigt werden. Dies geschieht, weil Sie in Magento 2 Entitäten erstellen, die nicht in der Magento 1-Instanz vorhanden sind.

## Schritt 7: Live-Schaltung

Nachdem Ihre Magento 2-Site nun mit Magento 1 aktualisiert wurde und normal funktioniert, führen Sie folgende Schritte aus, um zur neuen Site zu wechseln:

1. Setzen Sie Ihr Magento 1-System in den Wartungsmodus (DOWNTIME STARTS).

1. Drücken Sie Strg+C im Befehlsfenster des Migrations-Tools, um inkrementelle Aktualisierungen zu stoppen.

1. Starten Sie Ihre Magento 2 Cron-Aufträge.

1. Indizieren Sie den Aktienindexer in Ihrem Magento 2-System neu. Weitere Informationen finden Sie im [Konfigurationshandbuch].

1. Verwenden Sie ein Tool Ihrer Wahl, und rufen Sie Seiten in Ihrem Magento 2-System auf, um Seiten vor Kunden zwischenzuspeichern, die Ihre Storefront verwenden.

1. Führen Sie eine abschließende Überprüfung Ihrer Magento 2-Site durch.

1. Ändern Sie DNS, Load-Balancer usw., um auf neue Produktions-Hardware zu verweisen (DOWNTIME ENDS).

1. Der Magento 2-Speicher ist jetzt einsatzbereit. Sie und Ihre Kunden können alle Aktivitäten fortsetzen.

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
