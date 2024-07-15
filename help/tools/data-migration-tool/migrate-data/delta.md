---
title: Migrieren von Änderungen
description: Erfahren Sie, wie Sie nur Daten migrieren, die sich seit der letzten Magento 1-Datenmigration mit dem  [!DNL Data Migration Tool] geändert haben.
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Migrieren von Änderungen

Das inkrementelle Migrationstool installiert Deltalog-Tabellen (mit dem Präfix `m2_cl_*`) und Trigger (zum Verfolgen von Änderungen) in der Magento 1-Datenbank während der [Datenmigration](data.md). Diese Deltalog-Tabellen und -Trigger sind unverzichtbar, um sicherzustellen, dass Sie nur die Änderungen migrieren, die seit der letzten Datenmigration in Magento 1 vorgenommen wurden. Diese Änderungen sind:

* Daten, die Kunden über Storefront hinzugefügt haben (erstellte Bestellungen, Rezensionen und Änderungen in Kundenprofilen)

* Alle Vorgänge mit Bestellungen, Produkten und Kategorien im Admin Panel

>[!NOTE]
>
>Alle anderen neuen oder aktualisierten Entitäten, die über den Admin eingegeben werden (z. B. Attribute oder CMS-Seiten), sind nicht in der inkrementellen Migration enthalten und werden nicht migriert.


Bevor Sie beginnen, bereiten Sie die folgenden Schritte vor:

1. Melden Sie sich beim Anwendungsserver als [Dateisysteminhaber](../../../installation/prerequisites/file-system/overview.md) an.
1. Wechseln Sie zum Verzeichnis `/bin` oder stellen Sie sicher, dass es Ihrem System `PATH` hinzugefügt wird.

Weitere Informationen finden Sie im Abschnitt [Erste Schritte](overview.md#first-steps) .

## Führen Sie den inkrementellen Migrationsbefehl aus

Um mit der Migration inkrementeller Änderungen zu beginnen, führen Sie Folgendes aus:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

* `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden.

* `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn bei der Integritätsprüfung Fehler auftreten.

* `{<path to config.xml>}` ist der absolute Dateisystempfad zu `config.xml`; dieses Argument ist erforderlich.

>[!NOTE]
>
>Die inkrementelle Migration ist ein kontinuierlicher Prozess, der automatisch alle 5 Sekunden neu gestartet wird. Verwenden Sie STRG-C, um den Migrationsprozess abzubrechen.


## Migrieren von Daten, die von Drittanbietererweiterungen erstellt wurden

Im Modus `Delta` migriert der Modus [!DNL Data Migration Tool] nur von Magento erstellte Daten und ist nicht für den Code oder die Erweiterungen von Drittanbieterentwicklern verantwortlich. Wenn diese Erweiterungen Daten in der Storefront-Datenbank erstellt haben und der Händler diese Daten in Magento 2 speichern möchte, sollten Konfigurationsdateien des [!DNL Data Migration Tool] entsprechend erstellt und geändert werden.

Wenn eine Erweiterung über eigene Tabellen verfügt und Sie ihre Änderungen für die Delta-Migration verfolgen müssen, führen Sie die folgenden Schritte aus:

1. Fügen Sie die zu verfolgenden Tabellen zur Datei `deltalog.xml` hinzu
1. Erstellen Sie eine zusätzliche Delta-Klasse, die die `Migration\App\Step\AbstractDelta` erweitert
1. Fügen Sie den Namen der neu erstellten Klasse zum Delta-Modus-Abschnitt von `config.xml` hinzu.
