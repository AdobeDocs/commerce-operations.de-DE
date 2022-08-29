---
title: Datenmigrationseinstellungen
description: Erfahren Sie, wie Sie mit der Migration der Einstellungen von Magento 1 zu Magento 2 beginnen. [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Datenmigrationseinstellungen

Die `Settings` -Modus migriert Stores, Websites und Systemkonfigurationen wie Versand-, Zahlungs- und Steuereinstellungen. Gemäß unserer Datenmigration [order](overview.md#migration-order), sollten Sie die Einstellungen zuerst migrieren.

Bevor Sie beginnen, bereiten Sie die folgenden Schritte vor:

1. Melden Sie sich mit Ihrer Magento 2-Instanz als [der Dateisysteminhaber](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Änderung an Magento 2 `/bin` Verzeichnis oder stellen Sie sicher, dass es zu Ihrem System-PATH hinzugefügt wird.

>[!NOTE]
>
>Stellen Sie sicher, dass Magento 2 in `default` -Modus. Der Entwicklermodus kann Überprüfungsfehler im Migrationstool verursachen.


Siehe [Erste Schritte](overview.md#first-steps) für weitere Details.

## Führen Sie den Konfigurationsmigrationsbefehl aus

Um mit der Migration der Einstellungen zu beginnen, führen Sie Folgendes aus:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

* `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden

* `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn bei der Integritätsprüfung Fehler auftreten.

* `{<path to config.xml>}` ist der absolute Dateisystempfad zum Migrationstool [`config.xml`](../configure.md#configure-migration-in-vendor-folder) Datei; Dieses Argument ist erforderlich.

>[!NOTE]
>
>Dieser Befehl migriert nicht alle Konfigurationseinstellungen. Überprüfen Sie alle Einstellungen in Magento 2. [Admin](https://glossary.magento.com/admin) vor dem Fortfahren.


Die `Migration completed` wird angezeigt, nachdem die Einstellungen erfolgreich übertragen wurden.

## Benutzerdefinierte Migrationsregeln konfigurieren

Sie können die Systemkonfigurationen beim Migrieren von Einstellungen ignorieren, umbenennen oder ändern. Geben Sie dazu Ihre benutzerdefinierten Regeln im `settings.xml` -Datei.

1. Melden Sie sich mit Ihrer Magento 2-Instanz als Server an oder wechseln Sie zu der [Dateisysteminhaber](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Wechseln Sie in den folgenden Ordner:

   ```bash
   cd <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Wenn beispielsweise Magento 2 in `/var/www/html`, die `settings.xml.dist` -Datei sich in einem der folgenden Verzeichnisse befindet:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. So erstellen Sie eine `settings.xml` -Datei aus dem bereitgestellten Beispiel ausführen:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Nehmen Sie Ihre Änderungen in vor `settings.xml`.

1. Um den neuen Namen der Einstellungsdatei für die Zuordnung anzugeben, ändern Sie die `<settings_map_file>` -Tag im `path/to/config.xml` -Datei.

Weitere Informationen finden Sie unter [Migrationsmodus für Einstellungen](../technical-specification.md#settings-migration-mode) des Tools [Spezifikation](../technical-specification.md).

## Nächster Migrationsschritt

* [Daten migrieren](data.md)
