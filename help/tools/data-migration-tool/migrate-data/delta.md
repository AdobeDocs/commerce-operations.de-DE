---
title: Migrieren von Änderungen
description: Erfahren Sie, wie Sie nur Daten migrieren, die sich seit der Datenmigration aus dem letzten Magento 1 geändert haben, mit der [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# Migrieren von Änderungen

Das Tool für die inkrementelle Migration installiert Deltalog-Tabellen (mit Präfix `m2_cl_*`) und Triggern (zur Nachverfolgung von Änderungen in der Datenbank von Magento 1 während der [Datenmigration](data.md). Diese Dialogfeldtabellen und -Trigger sind unverzichtbar, um sicherzustellen, dass Sie nur die Änderungen migrieren, die seit der letzten Datenmigration in Magento 1 vorgenommen wurden. Diese Änderungen sind:

* Daten, die Kunden über hinzugefügt haben [storefront](https://glossary.magento.com/storefront) (erstellte Bestellungen, Überprüfungen und Änderungen in Kundenprofilen)

* Alle Vorgänge mit Bestellungen, Produkten und Kategorien im [Admin](https://glossary.magento.com/magento-admin) panel

>[!NOTE]
>
>Alle anderen neuen oder aktualisierten Entitäten, die über den Admin eingegeben werden (z. B. Attribute oder CMS-Seiten), sind nicht in der inkrementellen Migration enthalten und werden nicht migriert.


Bevor Sie beginnen, bereiten Sie die folgenden Schritte vor:

1. Melden Sie sich beim Anwendungsserver als [der Dateisysteminhaber](../../../installation/prerequisites/file-system/overview.md).
1. Änderung an `/bin` Verzeichnis oder stellen Sie sicher, dass es zu Ihrem System hinzugefügt wird. `PATH`.

Siehe [Erste Schritte](overview.md#first-steps) für weitere Details.

## Führen Sie den inkrementellen Migrationsbefehl aus

Um mit der Migration inkrementeller Änderungen zu beginnen, führen Sie Folgendes aus:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

* `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden.

* `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn bei der Integritätsprüfung Fehler auftreten.

* `{<path to config.xml>}` ist der absolute Dateisystempfad zu `config.xml`; Dieses Argument ist erforderlich.

>[!NOTE]
>
>Die inkrementelle Migration ist ein kontinuierlicher Prozess. wird automatisch alle 5 Sekunden neu gestartet. Verwenden Sie STRG-C, um den Migrationsprozess abzubrechen.


## Migrieren von Daten, die von Drittanbietererweiterungen erstellt wurden

Im `Delta` -Modus, die [!DNL Data Migration Tool] migriert Daten, die nur von den eigenen Modulen von Magento erstellt wurden, und ist nicht für den Code oder die Erweiterungen von Drittanbieterentwicklern verantwortlich. Wenn diese Erweiterungen Daten in der Storefront-Datenbank erstellt haben und der Händler diese Daten in Magento 2 — Konfigurationsdateien des [!DNL Data Migration Tool] sollte entsprechend erstellt und geändert werden.

Wenn eine [Erweiterung](https://glossary.magento.com/extension) verfügt über eigene Tabellen. Sie müssen die Änderungen für die Delta-Migration verfolgen und die folgenden Schritte ausführen:

1. Fügen Sie die zu verfolgenden Tabellen zum `deltalog.xml` file
1. Erstellen Sie eine zusätzliche Delta-Klasse, die die `Migration\App\Step\AbstractDelta`
1. Fügen Sie den Namen der neu erstellten Klasse zum Delta-Modus-Abschnitt von `config.xml`
