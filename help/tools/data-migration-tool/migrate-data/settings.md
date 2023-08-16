---
title: Datenmigrationseinstellungen
description: Erfahren Sie, wie Sie mit der Migration der Einstellungen von Magento 1 zu Magento 2 beginnen. [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Datenmigrationseinstellungen

Die `Settings` -Modus migriert Stores, Websites und Systemkonfigurationen wie Versand-, Zahlungs- und Steuereinstellungen. Gemäß unserer Datenmigration [bestellen](overview.md#migration-order), sollten Sie die Einstellungen zuerst migrieren.

Bevor Sie beginnen, bereiten Sie die folgenden Schritte vor:

1. Melden Sie sich beim Anwendungsserver als [Dateisysteminhaber](../../../installation/prerequisites/file-system/overview.md).

1. Ändern Sie die `/bin` Verzeichnis oder stellen Sie sicher, dass es Ihrem System hinzugefügt wird. `PATH`.

>[!NOTE]
>
>Stellen Sie sicher, dass Magento 2 in bereitgestellt wird `default` -Modus. Der Entwicklermodus kann Überprüfungsfehler im Migrationstool verursachen.


Siehe [Erste Schritte](overview.md#first-steps) für weitere Details.

## Führen Sie den Konfigurationsmigrationsbefehl aus

Um mit der Migration der Einstellungen zu beginnen, führen Sie Folgendes aus:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

* `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden

* `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn bei der Integritätsprüfung Fehler auftreten.

* `{<path to config.xml>}` ist der absolute Dateisystempfad zum Migrationstool [`config.xml`](../configure.md#configure-migration-in-vendor-folder) -Datei; dieses Argument ist erforderlich.

>[!NOTE]
>
>Dieser Befehl migriert nicht alle Konfigurationseinstellungen. Überprüfen Sie alle Einstellungen in Magento 2 Admin, bevor Sie fortfahren.


Die `Migration completed` wird angezeigt, nachdem die Einstellungen erfolgreich übertragen wurden.

## Benutzerdefinierte Migrationsregeln konfigurieren

Sie können die Systemkonfigurationen beim Migrieren von Einstellungen ignorieren, umbenennen oder ändern. Geben Sie dazu Ihre benutzerdefinierten Regeln im `settings.xml` -Datei.

1. Melden Sie sich beim Anwendungsserver als an oder wechseln Sie zu der [Dateisysteminhaber](../../../installation/prerequisites/file-system/overview.md).

1. Wechseln Sie in den folgenden Ordner:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Wenn das Programm beispielsweise in `/var/www/html`, die `settings.xml.dist` -Datei sich in einem der folgenden Verzeichnisse befindet:

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
