---
title: Einstellungen für die Datenmigration
description: Erfahren Sie, wie Sie mit der Migration von Einstellungen von Magento 1 zu Magento 2 mit dem  [!DNL Data Migration Tool] beginnen.
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Einstellungen für die Datenmigration

Der `Settings` Modus migriert Stores, Websites und Systemkonfigurationen wie Versand-, Zahlungs- und Steuereinstellungen. Gemäß unserer Datenmigration [Reihenfolge](overview.md#migration-order) sollten Sie zuerst die Einstellungen migrieren.

Bevor Sie beginnen, führen Sie die folgenden Schritte aus, um Folgendes vorzubereiten:

1. Melden Sie sich beim Anwendungs-Server als [Dateisystemeigentümer“ &#x200B;](../../../installation/prerequisites/file-system/overview.md).

1. Wechseln Sie in das `/bin` Verzeichnis oder stellen Sie sicher, dass es zu Ihrem `PATH` hinzugefügt wird.

>[!NOTE]
>
>Stellen Sie sicher, dass Magento 2 im `default` bereitgestellt wird. Der Entwicklermodus kann zu Validierungsfehlern im Migrations-Tool führen.


Weitere Informationen finden Sie [&#x200B; Abschnitt &#x200B;](overview.md#first-steps) Schritte .

## Ausführen des Befehls zur Einstellungsmigration

Um mit der Migration von Einstellungen zu beginnen, führen Sie Folgendes aus:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Dabei gilt:

* `[-r|--reset]` ist ein optionales Argument, das die Migration von Anfang an startet. Sie können dieses Argument zum Testen der Migration verwenden

* `[-a|--auto]` ist ein optionales Argument, das verhindert, dass die Migration angehalten wird, wenn Fehler bei der Integritätsprüfung auftreten.

* `{<path to config.xml>}` ist der absolute Dateisystempfad zur [`config.xml`](../configure.md#configure-migration-in-vendor-folder) des Migrations-Tools. Dieses Argument ist erforderlich.

>[!NOTE]
>
>Dieser Befehl migriert nicht alle Konfigurationseinstellungen. Überprüfen Sie alle Einstellungen in Magento 2 Admin, bevor Sie fortfahren.


Die `Migration completed` wird angezeigt, nachdem die Einstellungen erfolgreich übertragen wurden.

## Konfigurieren benutzerdefinierter Migrationsregeln

Sie können die Systemkonfigurationen beim Migrieren von Einstellungen ignorieren, umbenennen oder ändern. Geben Sie dazu Ihre benutzerdefinierten Regeln in der `settings.xml` an.

1. Melden Sie sich beim Anwendungs-Server als oder wechseln Sie zum [Dateisystembesitzer](../../../installation/prerequisites/file-system/overview.md).

1. Wechseln Sie in das folgende Verzeichnis:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Wenn die Anwendung beispielsweise in `/var/www/html` installiert ist, befindet sich die `settings.xml.dist` in einem der folgenden Verzeichnisse:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Um eine `settings.xml` Datei aus dem bereitgestellten Beispiel zu erstellen, führen Sie Folgendes aus:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Nehmen Sie Ihre Änderungen in `settings.xml` vor.

1. Um den neuen Namen der Einstellungsdatei für die Zuordnung anzugeben, ändern Sie das `<settings_map_file>`-Tag in der `path/to/config.xml`.

Weitere Informationen finden Sie [&#x200B; Abschnitt „Einstellungen Migrationsmodus](../technical-specification.md#settings-migration-mode) der [&#x200B; des Tools](../technical-specification.md).

## Nächster Migrationsschritt

* [Daten migrieren](data.md)
