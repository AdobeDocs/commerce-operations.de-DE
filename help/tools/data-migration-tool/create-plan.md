---
title: Erstellen eines Datenmigrationsplans
description: Führen Sie diese Schritte aus, um einen Datenmigrationsplan zu erstellen, um eine erfolgreiche Aktualisierung von Magento 1 auf Magento 2 sicherzustellen.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# Erstellen eines Datenmigrationsplans

Um eine erfolgreiche Migration durchzuführen und Probleme zu vermeiden, müssen Sie Ihre Migration gründlich planen und testen.

## Vor dem Start: Upgrade erwägen

Die Migration ist der perfekte Zeitpunkt, um ernsthafte Änderungen vorzunehmen und Ihre Site für das nächste Wachstumsniveau vorzubereiten. Überlegen Sie, ob Ihre neue Site mit mehr Hardware oder einer fortschrittlicheren Topologie mit besseren Caching-Ebenen gestaltet werden muss.

## Schritt 1: Überprüfen von Erweiterungen auf Ihrer aktuellen Site

* Welche Erweiterungen haben Sie installiert?

* Haben Sie festgestellt, ob Sie all diese Erweiterungen auf Ihrer neuen Site benötigen? Es kann alte geben, die Sie sicher entfernen können.

* Haben Sie festgestellt, ob Magento 2-Versionen Ihrer Erweiterungen vorhanden sind? Besuchen Sie [Commerce Marketplace] , um die neuesten Versionen zu finden, oder kontaktieren Sie Ihren Erweiterungsanbieter.

* Welche Datenbank-Assets aus Ihren Erweiterungen möchten Sie migrieren?

## Schritt 2: Erstellen und Vorbereiten Ihres Stores für die Migration

* Richten Sie ein Magento 2-Hardwaresystem mithilfe von Topologie und Design ein, das mindestens mit Ihrem bestehenden Magento 1-System übereinstimmt.

* Installieren Sie Magento 2.x (mit allen Modulen dieser Version) und den [!DNL Data Migration Tool] auf einem System, das die [Systemanforderungen](../../installation/system-requirements.md) erfüllt

* Nehmen Sie Ihre benutzerdefinierten Anpassungen am [!DNL Data Migration Tool] -Code vor, falls Sie einige Daten (wie CMS-Seiten, Verkaufsregeln) nicht migrieren müssen oder Ihre Magento-Anpassung während der Migration konvertieren möchten. Lesen Sie die [Technische Spezifikation ](technical-specification.md) von [!DNL Data Migration Tool] , um besser zu verstehen, wie die Migration von innen funktioniert.

## Schritt 3: Probelauf

Bevor Sie mit der Migration in die Produktionsumgebung beginnen, sollten Sie am besten alle Migrationsschritte in Ihrer Testumgebung durchführen.

Führen Sie bei solchen Migrationstests die folgenden Schritte aus:

* Kopieren Sie Ihren Magento 1-Store auf einen Staging-Server.

* Vollständige Migration des replizierten Magento 1-Stores auf Magento 2

* Testen Sie den neuen Store gründlich.

## Schritt 4: Migration starten

1. Stellen Sie sicher, dass der [!DNL Data Migration Tool] Netzwerkzugriff hat, um eine Verbindung zu Magento 1- und Magento 2-Datenbanken herzustellen. Öffnen Sie die entsprechenden Ports in Ihrer Firewall.

1. Beenden Sie alle Aktivitäten im Admin-Panel von Magento 1.x (mit Ausnahme der Auftragsverwaltung) wie Versand, Erstellung von Rechnungen und Kreditkarten. Die Liste der zulässigen Aktivitäten kann erweitert werden, indem die Einstellungen des Deltamodus im [!DNL Data Migration Tool] angepasst werden.

   >[!NOTE]
   >
   >Sie dürfen diese Aktivitäten erst fortsetzen, wenn Ihr Magento 2-Store live geschaltet ist.

1. Es wird empfohlen, alle Cron-Aufträge von Magento 1.x zu beenden.

   Wenn jedoch einige Aufträge während der Migration ausgeführt werden müssen, stellen Sie sicher, dass sie keine neuen Datenbankentitäten erstellen oder die vorhandenen so ändern, dass solche Entitäten nicht im Delta-Modus verarbeitet werden können.

   Beispielsweise verschiebt der Cron-Auftrag `enterprise_salesarchive_archive_orders` alte Bestellungen zum Archivieren. Die Ausführung dieses Auftrags während der Migration ist sicher, da der Delta-Modus diesen Vorgang erkennt und die archivierten Bestellungen ordnungsgemäß verarbeitet.

1. Verwenden Sie den [!DNL Data Migration Tool] , um Einstellungen und Websites zu migrieren.

1. Kopieren Sie Ihre Magento 1.x-Mediendateien auf Magento 2.x.

   Sie müssen diese Dateien manuell aus dem Verzeichnis `magento1-root/media` in `magento2-root/pub/media` kopieren.

1. Verwenden Sie den [!DNL Data Migration Tool], um Ihre Daten von der Magento 1-Datenbank in die Magento 2-Datenbank zu kopieren.

   Wenn einige Ihrer Erweiterungen über Daten verfügen, die Sie migrieren möchten, müssen Sie diese Erweiterungen möglicherweise installieren, die für Magento 2 angepasst sind. Falls die Erweiterungen in der Magento 2-Datenbank eine andere Struktur aufweisen, verwenden Sie die mit dem Tag [!DNL Data Migration Tool] bereitgestellten Zuordnungsdateien.

1. Neuindizieren aller Magento 2.x-Indexer. Weitere Informationen finden Sie unter [Indexer verwalten](../../configuration/cli/manage-indexers.md) im _Konfigurationshandbuch_.

## Schritt 5: Nehmen Sie bei Bedarf Änderungen an den migrierten Daten vor.

Manchmal möchten Sie vielleicht, dass Ihr Magento 2-Store nach der Migration eine andere Katalogstruktur, Verkaufsregeln und CMS-Seiten aufweist.

Bei manuellen Datenänderungen ist Vorsicht geboten. Fehler verursachen Fehler im folgenden Schritt der inkrementellen Datenmigration.

Beispielsweise ein Produkt, das aus Magento 2 gelöscht wurde: das Produkt, das auf Ihrem Live-Magento-1-Store gekauft wurde und das nicht mehr in Ihrem Magento 2-Store verfügbar ist. Die Übertragung von Daten zu einem solchen Kauf kann während der Ausführung von [!DNL Data Migration Tool] im Deltamodus zu einem Fehler führen.

## Schritt 6: Aktualisieren der inkrementellen Daten

Nach der Datenmigration müssen Sie schrittweise Daten-Updates erfassen, die im Magento 1 Store hinzugefügt wurden (z. B. neue Bestellungen, Überprüfungen und Änderungen an Kundenprofilen), und diese Aktualisierungen mithilfe des Delta-Modus an den Magento 2-Store übertragen.

* Starten Sie die inkrementelle Migration. Aktualisierungen werden kontinuierlich ausgeführt. Sie können die Übertragung von Updates jederzeit beenden, indem Sie auf `Ctrl+C` drücken.

* Testen Sie während dieser Zeit Ihre Magento 2 Website, um Probleme so schnell wie möglich zu beheben. Wenn Probleme auftreten, drücken Sie die Taste &quot;`Ctrl+C`&quot;, um die inkrementelle Migration zu stoppen und nach Behebung der Probleme erneut zu starten.

>[!NOTE]
>
>Warnungen zur Volumenüberprüfung können angezeigt werden, wenn Sie gleichzeitig Ihre Magento 2-Site testen und den Migrationsprozess ausführen. Dies geschieht, weil Sie in Magento 2 Entitäten erstellen, die nicht in der Magento 1-Instanz vorhanden sind.

## Schritt 7: Live-Schaltung

Da Ihre Magento 2-Website mit Magento 1 aktuell ist und normal funktioniert, führen Sie die folgenden Schritte aus, um die neue Website zu besuchen:

1. Setzen Sie Ihr Magento 1-System in den Wartungsmodus (DOWNTIME STARTS).

1. Drücken Sie Strg+C im Befehlsfenster des Migrationswerkzeugs, um inkrementelle Aktualisierungen zu stoppen.

1. Starten Sie Ihre Magento 2 Cron-Aufträge.

1. Indizieren Sie in Ihrem Magento 2-System den Aktienindex neu. Weitere Informationen finden Sie im [Konfigurationshandbuch].

1. Führen Sie mit einem Tool Ihrer Wahl Seitenaufrufe in Ihrem Magento 2-System durch, um Seiten zwischenzuspeichern, bevor Kunden Ihre Storefront verwenden.

1. Führen Sie eine abschließende Überprüfung Ihrer Magento 2-Site durch.

1. Ändern Sie DNS, Lastenausgleich usw. so, dass sie auf neue Produktionshardware verweisen (DOWNTIME ENDS).

1. Magento 2 Store ist jetzt einsatzbereit. Sie und Ihre Kunden können alle Aktivitäten fortsetzen.

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
