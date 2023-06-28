---
title: Erstellen eines Datenmigrationsplans
description: Führen Sie diese Schritte aus, um einen Datenmigrationsplan zu erstellen, um eine erfolgreiche Aktualisierung von Magento 1 auf Magento 2 sicherzustellen.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 0%

---

# Erstellen eines Datenmigrationsplans

Um eine erfolgreiche Migration durchzuführen und Probleme zu vermeiden, müssen Sie Ihre Migration gründlich planen und testen.

## Bevor Sie beginnen: Upgrade erwägen

Die Migration ist der perfekte Zeitpunkt, um ernsthafte Änderungen vorzunehmen und Ihre Site für das nächste Wachstumsniveau vorzubereiten. Überlegen Sie, ob Ihre neue Site mit mehr Hardware oder einer fortschrittlicheren Topologie mit besseren Caching-Ebenen gestaltet werden muss.

## Schritt 1: Überprüfen von Erweiterungen auf Ihrer aktuellen Site

* Welche Erweiterungen haben Sie installiert?

* Haben Sie festgestellt, ob Sie all diese Erweiterungen auf Ihrer neuen Site benötigen? Es gibt alte, die Sie sicher entfernen können.

* Haben Sie festgestellt, ob Magento 2-Versionen Ihrer Erweiterungen vorhanden sind? Besuch [Commerce Marketplace] , um die neuesten Versionen zu finden, oder wenden Sie sich an Ihren Erweiterungsanbieter.

* Welche Datenbank-Assets aus Ihren Erweiterungen möchten Sie migrieren?

## Schritt 2: Erstellen und Vorbereiten des Stores für die Migration

* Richten Sie das Hardware-System Magento 2 mithilfe von Topologie und Design ein, das mindestens Ihrem bestehenden Magento 1-System entspricht.

* Installieren Sie Magento 2.x (mit allen Modulen dieser Version) und die [!DNL Data Migration Tool] auf einem System, das [Systemanforderungen](../../installation/system-requirements.md)

* Nehmen Sie Ihre benutzerdefinierten Anpassungen an den [!DNL Data Migration Tool] -Code, falls Sie einige Daten (z. B. CMS-Seiten, Verkaufsregeln) nicht migrieren müssen oder Ihre Magento-Anpassung während der Migration konvertieren möchten. Lesen Sie die [!DNL Data Migration Tool]s [Technische Spezifikation](technical-specification.md) , um besser zu verstehen, wie Migration von innen funktioniert

## Schritt 3: Trockenlauf

Bevor Sie mit der Migration in die Produktionsumgebung beginnen, sollten Sie am besten alle Migrationsschritte in Ihrer Testumgebung durchführen.

Führen Sie bei solchen Migrationstests die folgenden Schritte aus:

* Kopieren Sie Ihren Magento 1 Store auf einen Staging-Server.

* Vollständige Migration des replizierten Stores von Magento 1 zu Magento 2

* Testen Sie den neuen Store gründlich.

## Schritt 4: Migration starten

1. Stellen Sie sicher, dass die Variable [!DNL Data Migration Tool] verfügt über einen Netzwerkzugriff, um eine Verbindung zu Magento 1- und Magento 2-Datenbanken herzustellen. Öffnen Sie die entsprechenden Ports in Ihrer Firewall.

1. Beenden Sie alle Aktivitäten im Admin Panel von Magento 1.x (mit Ausnahme der Auftragsverwaltung), wie z. B. Versand, Erstellung von Rechnungen und Kreditkarten. Die Liste der zulässigen Aktivitäten kann durch Anpassung der Einstellungen des Delta-Modus im [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >Sie dürfen diese Aktivitäten erst fortsetzen, wenn Ihr Magento 2 Store live geschaltet ist.

1. Es wird empfohlen, alle Cron-Aufträge für Magento 1.x zu beenden.

   Wenn jedoch einige Aufträge während der Migration ausgeführt werden müssen, stellen Sie sicher, dass sie keine neuen Datenbankentitäten erstellen oder die vorhandenen so ändern, dass solche Entitäten nicht im Delta-Modus verarbeitet werden können.

   Beispiel: die `enterprise_salesarchive_archive_orders` cron job verschiebt alte Bestellungen in das Archiv. Die Ausführung dieses Auftrags während der Migration ist sicher, da der Delta-Modus diesen Vorgang erkennt und die archivierten Bestellungen ordnungsgemäß verarbeitet.

1. Verwenden Sie die [!DNL Data Migration Tool] , um Einstellungen und Websites zu migrieren.

1. Kopieren Sie Ihre Magento 1.x-Mediendateien in Magento 2.x.

   Sie müssen diese Dateien manuell aus dem `magento1-root/media` Verzeichnis in `magento2-root/pub/media`.

1. Verwenden Sie die [!DNL Data Migration Tool] zum Massenkopieren Ihrer Daten aus der Datenbank von Magento 1 in die Datenbank von Magento 2.

   Wenn einige Ihrer Erweiterungen über Daten verfügen, die Sie migrieren möchten, müssen Sie diese Erweiterungen möglicherweise installieren, die für Magento 2 angepasst sind. Wenn die Erweiterungen eine andere Struktur in der Datenbank von Magento 2 haben, verwenden Sie die Zuordnungsdateien, die mit der [!DNL Data Migration Tool].

1. Neuindizieren aller Magento 2.x-Indizes. Weitere Informationen finden Sie unter [Indexer verwalten](../../configuration/cli/manage-indexers.md) im _Konfigurationshandbuch_.

## Schritt 5: Nehmen Sie bei Bedarf Änderungen an den migrierten Daten vor.

Manchmal möchten Sie vielleicht, dass Ihr Magento 2-Store nach der Migration eine andere Katalogstruktur, Verkaufsregeln und CMS-Seiten aufweist.

Bei manuellen Datenänderungen ist Vorsicht geboten. Fehler verursachen Fehler im folgenden Schritt der inkrementellen Datenmigration.

Beispielsweise ein aus Magento 2 gelöschtes Produkt: den Artikel, der in Ihrem Live-Magento-1-Store gekauft wurde und der nicht mehr in Ihrem Magento-2-Store verfügbar ist. Das Übertragen von Daten zu einem solchen Kauf kann bei der Ausführung des [!DNL Data Migration Tool] im Deltamodus.

## Schritt 6: Inkrementelle Daten aktualisieren

Nach der Datenmigration müssen Sie schrittweise Datenaktualisierungen erfassen, die im Magento 1 Store hinzugefügt wurden (z. B. neue Bestellungen, Überprüfungen und Änderungen an Kundenprofilen), und diese Aktualisierungen mithilfe des Delta-Modus an den Magento 2-Store übertragen.

* Inkrementelle Migration starten; Aktualisierungen werden kontinuierlich ausgeführt. Sie können die Übertragung von Updates jederzeit beenden, indem Sie `Ctrl+C`.

* Testen Sie Ihre Magento 2-Site während dieser Zeit, um Probleme so schnell wie möglich zu erkennen. Wenn Probleme auftreten, drücken Sie die `Ctrl+C` , um die inkrementelle Migration zu beenden und sie nach Behebung der Probleme erneut zu starten.

>[!NOTE]
>
>Warnungen zur Volumenüberprüfung können angezeigt werden, wenn Sie Ihre Magento 2-Site testen und gleichzeitig den Migrationsprozess ausführen. Dies geschieht, weil Sie in Magento 2 Entitäten erstellen, die nicht in Magento 1-Instanz vorhanden sind.

## Schritt 7: Live-Schaltung

Nachdem Ihre Magento 2-Site mit Magento 1 auf dem neuesten Stand ist und normal funktioniert, führen Sie die folgenden Schritte aus, um die neue Site zu aktualisieren:

1. Setzen Sie Ihr Magento 1-System in den Wartungsmodus (DOWNTIME STARTS).

1. Drücken Sie Strg+C im Befehlsfenster des Migrationswerkzeugs, um inkrementelle Aktualisierungen zu stoppen.

1. Starten Sie Ihre Cron-Aufträge für Magento 2.

1. Indizieren Sie in Ihrem Magento 2-System den Aktienindex neu. Weitere Informationen finden Sie unter [Konfigurationshandbuch].

1. Führen Sie mit einem Tool Ihrer Wahl Seitenaufrufe in Ihrem Magento 2-System durch, um Seiten zwischenzuspeichern, bevor Kunden Ihre Storefront verwenden.

1. Führen Sie eine abschließende Überprüfung Ihrer Magento 2-Site durch.

1. Ändern Sie DNS, Lastenausgleich usw. so, dass sie auf neue Produktionshardware verweisen (DOWNTIME ENDS).

1. Der Store Magento 2 kann jetzt verwendet werden. Sie und Ihre Kunden können alle Aktivitäten fortsetzen.

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
