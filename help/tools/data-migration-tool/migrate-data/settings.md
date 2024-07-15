---
title: Datenmigrationseinstellungen
description: Erfahren Sie, wie Sie mit der Migration der Einstellungen von Magento 1 zu Magento 2 mit dem  [!DNL Data Migration Tool] beginnen.
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Datenmigrationseinstellungen

Der Modus `Settings` migriert Speicher, Websites und Systemkonfigurationen wie Versand-, Zahlungs- und Steuereinstellungen. Gemäß unserer Datenmigration [order](overview.md#migration-order) sollten Sie Einstellungen zuerst migrieren.

Bevor Sie beginnen, bereiten Sie die folgenden Schritte vor:

1. Melden Sie sich beim Anwendungsserver als [Dateisysteminhaber](../../../installation/prerequisites/file-system/overview.md) an.

1. Wechseln Sie zum Verzeichnis `/bin` oder stellen Sie sicher, dass es Ihrem System `PATH` hinzugefügt wird.

>[!NOTE]
>
>Stellen Sie sicher, dass Magento 2 im `default` -Modus bereitgestellt wird. Der Entwicklermodus kann Überprüfungsfehler im Migrationstool verursachen.


Weitere Informationen finden Sie im Abschnitt [Erste Schritte](overview.md#first-steps) .

## Führen Sie den Konfigurationsmigrationsbefehl aus

Um mit der Migration der Einstellungen zu beginnen, führen Sie Folgendes aus:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

* `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden

* `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn bei der Integritätsprüfung Fehler auftreten.

* `{<path to config.xml>}` ist der absolute Dateisystempfad zur [`config.xml`](../configure.md#configure-migration-in-vendor-folder) -Datei des Migrationstools. Dieses Argument ist erforderlich.

>[!NOTE]
>
>Dieser Befehl migriert nicht alle Konfigurationseinstellungen. Überprüfen Sie alle Einstellungen in Magento 2 Admin, bevor Sie fortfahren.


Die Meldung `Migration completed` wird angezeigt, nachdem die Einstellungen erfolgreich übertragen wurden.

## Benutzerdefinierte Migrationsregeln konfigurieren

Sie können die Systemkonfigurationen beim Migrieren von Einstellungen ignorieren, umbenennen oder ändern. Geben Sie dazu Ihre benutzerdefinierten Regeln in der Datei `settings.xml` an.

1. Melden Sie sich beim Anwendungsserver als [Dateisysteminhaber](../../../installation/prerequisites/file-system/overview.md) an oder wechseln Sie zu ihm.

1. Wechseln Sie in den folgenden Ordner:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Wenn das Programm beispielsweise in `/var/www/html` installiert ist, befindet sich die Datei `settings.xml.dist` in einem der folgenden Ordner:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Um eine `settings.xml` -Datei aus dem bereitgestellten Beispiel zu erstellen, führen Sie Folgendes aus:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Nehmen Sie Ihre Änderungen in `settings.xml` vor.

1. Um den neuen Namen der Einstellungsdatei für die Zuordnung anzugeben, ändern Sie das Tag `<settings_map_file>` in der Datei `path/to/config.xml` .

Weitere Informationen finden Sie im Abschnitt [Einstellungs-Migrationsmodus](../technical-specification.md#settings-migration-mode) der [Spezifikation des Tools](../technical-specification.md).

## Nächster Migrationsschritt

* [Daten migrieren](data.md)
