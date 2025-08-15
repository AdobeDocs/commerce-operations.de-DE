---
title: Änderungen migrieren
description: Erfahren Sie, wie Sie mit dem nur Daten migrieren können, die sich seit Ihrer letzten Magento 1-Datenmigration geändert  [!DNL Data Migration Tool].
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Änderungen migrieren

Das inkrementelle Migrations-Tool installiert deltalog-Tabellen (mit Präfix `m2_cl_*`) und Trigger (zum Tracking von Änderungen) in der Magento 1-Datenbank während der [Datenmigration](data.md). Diese Deltalog-Tabellen und -Trigger sind wichtig, um sicherzustellen, dass Sie nur die Änderungen migrieren, die seit der letzten Datenmigration in Magento 1 vorgenommen wurden. Diese Änderungen sind:

* Daten, die Kunden über die Storefront hinzugefügt haben (erstellte Bestellungen, Überprüfungen und Änderungen an Kundenprofilen)

* Alle Vorgänge mit Bestellungen, Produkten und Kategorien im Admin-Bedienfeld

>[!NOTE]
>
>Alle anderen neuen oder aktualisierten Entitäten, die über den Admin eingegeben wurden, z. B. Attribute oder CMS-Seiten, sind nicht in der inkrementellen Migration enthalten und werden nicht migriert.


Bevor Sie beginnen, führen Sie die folgenden Schritte aus, um Folgendes vorzubereiten:

1. Melden Sie sich beim Anwendungsserver als [Dateisystemeigentümer“ ](../../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie in das `/bin` Verzeichnis oder stellen Sie sicher, dass es zu Ihrem `PATH` hinzugefügt wird.

Weitere Informationen finden Sie [ Abschnitt ](overview.md#first-steps) Schritte .

## Führen Sie den inkrementellen Migrationsbefehl aus

Um mit der Migration inkrementeller Änderungen zu beginnen, führen Sie Folgendes aus:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

* `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden.

* `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn Fehler bei der Integritätsprüfung auftreten.

* `{<path to config.xml>}` ist der absolute Dateisystempfad zu `config.xml`. Dieses Argument ist erforderlich.

>[!NOTE]
>
>Die inkrementelle Migration ist ein kontinuierlicher Prozess, der automatisch alle 5 Sekunden neu gestartet wird. Verwenden Sie Strg-C, um den Migrationsprozess abzubrechen.


## Migrieren von Daten, die von Erweiterungen von Drittanbietern erstellt wurden

Im `Delta`-Modus migriert der [!DNL Data Migration Tool] nur Daten, die von den Magento-eigenen Modulen erstellt wurden, und ist nicht für den Code oder die Erweiterungen verantwortlich, die von Drittanbieterentwicklern erstellt wurden. Wenn diese Erweiterungen Daten in der Storefront-Datenbank erstellt haben und der Händler diese Daten in Magento 2 haben möchte, sollten Konfigurationsdateien des [!DNL Data Migration Tool] entsprechend erstellt und geändert werden.

Wenn eine Erweiterung über eigene Tabellen verfügt und Sie deren Änderungen für die Delta-Migration verfolgen müssen, führen Sie die folgenden Schritte aus:

1. Hinzufügen der zu verfolgenden Tabellen zur `deltalog.xml`
1. Erstellen Sie eine zusätzliche Delta-Klasse, die die `Migration\App\Step\AbstractDelta` erweitert
1. Fügen Sie den Namen der neu erstellten Klasse zum Abschnitt „Delta-Modus“ von `config.xml` hinzu
