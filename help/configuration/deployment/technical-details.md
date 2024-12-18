---
title: Technische Details
description: Erfahren Sie mehr über die technischen Details der Pipeline-Bereitstellung, Konfigurationstypen und empfohlene Workflows.
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Technische Details

In diesem Abschnitt werden technische Implementierungsdetails zur Pipeline-Bereitstellung in Commerce 2.2 und höher erläutert. Die Verbesserungen lassen sich in folgende Bereiche unterteilen:

- [Konfigurationsverwaltung](#configuration-management)
- [Änderungen in der Admin](#changes-in-the-admin)
- [Installieren und Entfernen von Cron](#install-and-remove-cron)

In diesem Thema wird auch der [empfohlene Workflow](#recommended-workflow) für die Pipeline-Bereitstellung erläutert und einige Beispiele bereitgestellt, die Ihnen dabei helfen, die Funktionsweise zu verstehen.

Bevor Sie beginnen, lesen Sie die [Voraussetzungen für Ihre Entwicklungs-, Build- und Produktionssysteme](../deployment/prerequisites.md).

## Konfigurationsverwaltung

Verwenden Sie das folgende Überschreibungsschema, um die Konfiguration Ihrer Entwicklungs- und Produktionssysteme synchronisieren und verwalten zu können.

![Wie werden Konfigurationsvariablenwerte bestimmt](../../assets/configuration/override-flow-diagram.png)

Wie das Diagramm zeigt, werden die Konfigurationswerte in der folgenden Reihenfolge verwendet:

1. Umgebungsvariablen überschreiben, falls vorhanden, alle anderen Werte.
1. In den freigegebenen Konfigurationsdateien `env.php` und `config.php`. Werte in `env.php` überschreiben Werte in `config.php`.
1. Aus in der Datenbank gespeicherten Werten.
1. Wenn in einer dieser Quellen kein Wert vorhanden ist, wird der Standardwert NULL verwendet.

### Verwalten der freigegebenen Konfiguration

Die freigegebene Konfiguration wird in `app/etc/config.php` gespeichert, das sich in der Quell-Code-Verwaltung befinden sollte.

Legen Sie die freigegebene Konfiguration im Admin-System in Ihrer Entwicklungsumgebung (oder im Adobe Commerce-_-_) fest und schreiben Sie die Konfiguration mithilfe des [`magento app:config:dump`-Befehls in `config.php`](../cli/export-configuration.md).

### Verwalten der systemspezifischen Konfiguration

Die systemspezifische Konfiguration wird in `app/etc/env.php` gespeichert, das _nicht_ der Quell-Code-Verwaltung sein sollte.

Legen Sie die systemspezifische Konfiguration im Admin-System in Ihrem Entwicklungssystem (oder in Adobe Commerce für die Cloud-Infrastrukturintegration) fest und schreiben Sie die Konfiguration mithilfe des [`magento app:config:dump`-Befehls in `env.php`](../cli/export-configuration.md).

Dieser Befehl schreibt auch vertrauliche Einstellungen in `env.php`.

### Verwalten der sensiblen Konfiguration

Die vertrauliche Konfiguration wird auch in `app/etc/env.php` gespeichert.

Sie können die vertrauliche Konfiguration auf eine der folgenden Arten verwalten:

- Umgebungsvariablen
- Speichern Sie die vertrauliche Konfiguration in `env.php` auf Ihrem Produktionssystem mithilfe des [`magento config:set:sensitive` Befehls](../cli/set-configuration-values.md)

### Konfigurationseinstellungen im Administrator gesperrt

Alle Konfigurationseinstellungen in `config.php` oder `env.php` sind im Administrator gesperrt, d. h. diese Einstellungen können im Administrator nicht geändert werden.
Verwenden Sie den Befehl [`magento config:set` oder `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set), um die Einstellungen in den `config.php`- oder `env.php`-Dateien zu ändern.

## Der Commerce-Administrator

Der Administrator zeigt im Produktionsmodus das folgende Verhalten:

- Cache-Typen können in Admin nicht aktiviert oder deaktiviert werden
- Entwicklereinstellungen sind nicht verfügbar (**Stores** > Einstellungen > **Konfiguration** > Erweitert > **Entwickler**), einschließlich:

   - Minimieren von CSS, JavaScript und HTML
   - Zusammenführen von CSS und JavaScript
   - Server- oder Client-seitige LESS-Kompilierung
   - Inline-Übersetzungen
   - Wie bereits erwähnt, sind Konfigurationseinstellungen in `config.php` oder `env.php` gesperrt und können nicht in der Admin bearbeitet werden.
   - Sie können das Admin-Gebietsschema nur in Sprachen ändern, die von bereitgestellten Designs verwendet werden

     Die folgende Abbildung zeigt ein Beispiel der Liste **Kontoeinstellung** > **Schnittstellengebietsschema** in der Admin-Liste, wobei nur zwei bereitgestellte Gebietsschemata angezeigt werden:

     ![Sie können das Admin-Gebietsschema nur in bereitgestellte Gebietsschemata ändern](../../assets/configuration/split-deploy-admin-locale.png)

- Sie können die Gebietsschema-Konfigurationen für keinen Bereich mit der Admin ändern.

  Es wird empfohlen, diese Änderungen vorzunehmen, bevor Sie in den Produktionsmodus wechseln.

  Sie können das Gebietsschema weiterhin mithilfe von Umgebungsvariablen oder dem `config:set` CLI-Befehl mit dem `general/locale/code` konfigurieren.

## Installieren und Entfernen von Cron

In Version 2.2 helfen wir Ihnen zum ersten Mal, Ihren Cron-Auftrag einzurichten, indem wir den [`magento cron:install` Befehl bereitstellen](../cli/configure-cron-jobs.md). Mit diesem Befehl wird eine crontab als Benutzer eingerichtet, der den Befehl ausführt.

Außerdem können Sie die crontab mit dem Befehl `magento cron:remove` entfernen.

## Empfohlener Workflow zur Pipeline-Bereitstellung

Das folgende Diagramm zeigt, wie die Pipeline-Bereitstellung zur Verwaltung der Konfiguration empfohlen wird.

![Empfohlener Workflow für die Pipeline-Bereitstellung](../../assets/configuration/split-deploy-workflow.png)

### Entwicklungssystem

Auf Ihrem Entwicklungssystem nehmen Sie Konfigurationsänderungen in der Admin Console vor und generieren die freigegebene Konfiguration, die `app/etc/config.php` und die systemspezifische Konfiguration, `app/etc/env.php`. Überprüfen Sie den Commerce-Code und die freigegebene Konfiguration in die Quell-Code-Verwaltung und übertragen Sie sie auf den Build-Server.

Sie sollten auch Erweiterungen installieren und den Commerce-Code im Entwicklungssystem anpassen.

Auf Ihrem Entwicklungssystem:

1. Legen Sie die Konfiguration im Admin-Bereich fest.

1. Verwenden Sie den Befehl `magento app:config:dump` , um die Konfiguration in das Dateisystem zu schreiben.

   - `app/etc/config.php` ist die freigegebene Konfiguration, die alle Einstellungen (_. B_ vertrauliche und systemspezifische Einstellungen enthält. Diese Datei sollte sich in der Quell-Code-Verwaltung befinden.
   - `app/etc/env.php` ist die systemspezifische Konfiguration, die Einstellungen enthält, die für ein bestimmtes System eindeutig sind (z. B. Hostnamen und Portnummern). Diese Datei sollte _nicht_ in der Quell-Code-Verwaltung sein.

1. Fügen Sie den geänderten Code und die freigegebene Konfiguration zur Quell-Code-Verwaltung hinzu.

1. Um generierten PHP-Code und statische Assets-Dateien während der Entwicklung zu entfernen, führen Sie die folgenden Befehle aus:

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Nach Ausführung der Befehle zum Löschen der Assets generiert Commerce Arbeitsdateien.

>[!WARNING]
>
>Seien Sie vorsichtig mit dem oben genannten Ansatz. Das Löschen der `.htacces` im `generated` oder `pub` Ordner kann Probleme verursachen.

### Build-System

Das Build-System kompiliert Code und generiert statische Ansichtsdateien für Designs, die in Commerce registriert sind. Sie benötigt keine Verbindung zur Commerce-Datenbank, sondern nur die Commerce-Code-Basis.

Auf Ihrem Build-System:

1. Rufen Sie die freigegebene Konfigurationsdatei aus der Quell-Code-Verwaltung ab.
1. Kompilieren Sie den Code mit dem Befehl `magento setup:di:compile`.
1. Verwenden Sie den Befehl `magento setup:static-content:deploy -f`, um statische Dateiansichtsdateien zu aktualisieren.
1. Überprüfen Sie die Aktualisierungen in der Quell-Code-Verwaltung.

>[!INFO]
>
>Siehe [Bereitstellungsstrategien für statische Ansichtsdateien](../cli/static-view-file-strategy.md).

### Produktionssystem

Auf Ihrem Produktionssystem (d. h. Ihrem Live Store) rufen Sie generierte Assets und Code-Aktualisierungen von der Versionsverwaltung ab und legen Sie systemspezifische und vertrauliche Konfigurationseinstellungen mithilfe der Befehlszeile oder von Umgebungsvariablen fest.

Auf Ihrem Produktionssystem:

1. Wartungsmodus starten.
1. Abrufen von Code- und Konfigurationsaktualisierungen aus der Versionsverwaltung.
1. Wenn Sie Adobe Commerce verwenden, stoppen Sie Warteschlangenarbeiter.
1. Verwenden Sie den Befehl `magento app:config:import` , um Konfigurationsänderungen in das Produktionssystem zu importieren.
1. Wenn Sie Komponenten installiert haben, die das Datenbankschema geändert haben, führen Sie `magento setup:upgrade --keep-generated` aus, um das Datenbankschema und die Daten zu aktualisieren, wobei die generierten statischen Dateien beibehalten werden.
1. Um systemspezifische Einstellungen festzulegen, verwenden Sie entweder den Befehl `magento config:set` oder Umgebungsvariablen.
1. Verwenden Sie zum Festlegen sensibler Einstellungen entweder den Befehl `magento config:sensitive:set` oder Umgebungsvariablen.
1. Löschen Sie den Cache (auch _flush_ genannt).
1. Wartungsmodus beenden

## Konfigurationsverwaltungsbefehle

Die folgenden Befehle helfen Ihnen bei der Verwaltung der Konfiguration:

- [`magento app:config:dump`](../cli/export-configuration.md) zum Schreiben der Admin-Konfigurationseinstellungen in `config.php` und `env.php` (mit Ausnahme der sensiblen Einstellungen)
- [`magento config:set`](../cli/set-configuration-values.md), um die Werte der systemspezifischen Einstellungen im Produktionssystem festzulegen.

  Verwenden Sie die optionale Option &quot;`--lock`&quot;, um die Option im Admin-Bereich zu sperren (d. h. die Einstellung nicht bearbeitbar zu machen). Wenn eine Einstellung bereits gesperrt ist, verwenden Sie die Option `--lock` , um die Einstellung zu ändern.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md), um die Werte der sensiblen Einstellungen im Produktionssystem festzulegen.
- [`magento app:config:import`](../cli/import-configuration.md) zum Importieren von Konfigurationsänderungen aus `config.php` und `env.php` in das Produktionssystem.

## Beispiele für die Konfigurationsverwaltung

Dieser Abschnitt zeigt Beispiele für die Verwaltung der Konfiguration, sodass Sie sehen können, wie Änderungen an `config.php` und `env.php` vorgenommen werden.

### Standardgebietsschema ändern

Dieser Abschnitt zeigt die Änderung, die an `config.php` vorgenommen wurde, wenn Sie die standardmäßige Gewichtungseinheit mithilfe von Admin ändern (**Stores** > Einstellungen > **Configuration** > Allgemein **Allgemein** > **Gebietsschema-Optionen**).

Nachdem Sie die Änderung in der Admin vorgenommen haben, führen Sie `bin/magento app:config:dump` aus, um den Wert in `config.php` zu schreiben. Der Wert wird in das `general`-Array unter `locale` geschrieben, wie der folgende Ausschnitt aus `config.php` zeigt:

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### Ändern mehrerer Konfigurationseinstellungen

In diesem Abschnitt werden die folgenden Konfigurationsänderungen erläutert:

- Hinzufügen einer Website-, Store- und Store-Ansicht (**Stores** > Einstellungen > **Alle Stores**)
- Ändern der Standard-E-Mail-Domain **Stores** > Einstellungen > **Konfiguration** > Kunden > **Kundenkonfiguration**)
- Festlegen des PayPal-API-Benutzernamens und API-Kennworts (**Stores** > Einstellungen > **Konfiguration** > Verkauf **Zahlungsmethoden** > **PayPal** > **Erforderliche PayPal-Einstellungen**)

Nachdem Sie die Änderung in der Admin vorgenommen haben, führen Sie `bin/magento app:config:dump` auf Ihrem Entwicklungssystem aus. Diesmal werden nicht alle Ihre Änderungen in `config.php` geschrieben. Tatsächlich werden nur die Website-, Store- und Store-Ansicht in diese Datei geschrieben, wie die folgenden Ausschnitte zeigen.

### config.php

`config.php` enthält:

- Änderungen an der Website-, Store- und Store-Ansicht.
- Nicht-systemspezifische Suchmaschineneinstellungen
- Nicht sensible PayPal-Einstellungen
- Kommentare, die Sie über vertrauliche Einstellungen informieren, die bei der `config.php` weggelassen wurden

`websites`:

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups`:

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores`:

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment`:

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

Die systemspezifische Konfigurationseinstellung der Standard-E-Mail-Domain wird in `app/etc/env.php` geschrieben.

Die PayPal-Einstellungen werden in keine der Dateien geschrieben, da der `bin/magento app:config:dump`-Befehl keine sensiblen Einstellungen schreibt. Sie müssen die PayPal-Einstellungen auf dem Produktionssystem mit den folgenden Befehlen festlegen:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
