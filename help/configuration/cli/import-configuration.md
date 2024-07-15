---
title: Daten aus Konfigurationsdateien importieren
description: Importieren Sie die Adobe Commerce-Konfigurationseinstellungen aus Konfigurationsdateien.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Konfigurationseinstellungen importieren

{{file-system-owner}}

Wenn Sie ein Produktionssystem mit dem Commerce 2.2 [Pipeline-Bereitstellungsmodell](../deployment/technical-details.md) einrichten, müssen Sie _Konfigurationseinstellungen vom Typ `config.php` und vom Typ `env.php` in die Datenbank importieren._
Zu diesen Einstellungen gehören Konfigurationspfade und -werte, Websites, Stores, Store-Ansichten und Designs.

Nach dem Import von Websites, Geschäften, Ansichten und Designs können Sie Produktattribute erstellen und auf Websites, Stores und Store-Ansichten im Produktionssystem anwenden.

>[!INFO]
>
>Der Befehl `bin/magento app:config:import` verarbeitet keine in Umgebungsvariablen gespeicherten Konfigurationen.

## Import, Befehl

Führen Sie auf Ihrem Produktionssystem den folgenden Befehl aus, um Daten aus den Konfigurationsdateien (`config.php` und `env.php`) in die Datenbank zu importieren:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Verwenden Sie das optionale Flag `[-n, --no-interaction]` , um Daten ohne Interaktion zu importieren.

Wenn Sie &quot;`bin/magento app:config:import`&quot;ohne die optionale Markierung eingeben, müssen Sie die Änderungen bestätigen.

Wenn die Konfigurationsdatei beispielsweise eine neue Website und einen neuen Store enthält, wird die folgende Meldung angezeigt:

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Geben Sie `yes` ein, um den Import fortzusetzen.

Wenn Bereitstellungskonfigurationsdateien zu importierende Daten enthalten, wird eine Meldung ähnlich der folgenden angezeigt:

```terminal
Start import:
Some information about importing
```

Wenn Bereitstellungskonfigurationsdateien keine zu importierenden Daten enthalten, wird eine Meldung ähnlich der folgenden angezeigt:

```terminal
Start import:
Nothing to import
```

## Was wir importieren

In den folgenden Abschnitten wird ausführlich beschrieben, welche Daten importiert werden.

### Systemkonfiguration

Commerce verwendet direkt Werte im Array `system` in den Dateien `config.php` oder `env.php`, anstatt sie in die Datenbank zu importieren, da sie einige Vorab- und Nachbearbeitungsvorgänge erfordern.

Beispielsweise muss der Wert des Konfigurationspfads `web/secure/base_url` mit Backend-Modellen überprüft werden.

#### Backend-Modelle

Backend-Modelle sind der Mechanismus zur Verarbeitung von Änderungen in der Systemkonfiguration.
Sie definieren Backend-Module in `<module_name>/adminhtml/system.xml`.

Alle Backend-Modelle müssen die Klasse [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) erweitern.

Beim Importieren von Backend-Modellen werden die Konfigurationswerte nicht gespeichert.

### Konfiguration von Websites, Stores und Stores

Wir importieren die folgenden Arten von Konfigurationen.
(Diese Konfigurationen befinden sich unter dem `scopes` -Array in `config.php`.)

- `websites`: Konfiguration im Zusammenhang mit Websites
- `groups`: Speichert die zugehörige Konfiguration
- `stores`: Konfiguration von Ansichten speichern

Die vorangehenden Konfigurationen können in den folgenden Modi importiert werden:

- `create`: `config.php` enthält neue Entitäten (`websites`, `groups`, `stores`), die in der Produktionsumgebung fehlen
- `update`: `config.php` enthält Entitäten (`websites`, `groups`, `stores`), die sich von der Produktionsumgebung unterscheiden
- `delete`: `config.php` enthält _nicht_ Entitäten (`websites`, `groups`, `stores`), die in der Produktionsumgebung vorhanden sind

>[!INFO]
>
>Die mit Stores verknüpfte Stammkategorie wird nicht importiert. Sie müssen mit dem Commerce-Administrator eine Stammkategorie mit einem Store verknüpfen.

### Designkonfiguration

Die Designkonfiguration umfasst alle in Ihrem Commerce-System registrierten Designs. Die Daten stammen direkt aus der Datenbanktabelle `theme`. (Die Designkonfiguration befindet sich im Array `themes` in `config.php`.)

#### Struktur der Designdaten

Der Schlüssel des Arrays ist der vollständige Designpfad: `area` + `theme path`

Beispiel: `frontend/Magento/luma`.
`frontend` ist Bereich und `Magento/luma` ist Designpfad.

Der Wert des Arrays ist Daten zum Thema: Code, Titel, Pfad, übergeordnete ID

Vollständiges Beispiel:

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _Themenregistrierung_. Wenn Designdaten in `config.php` definiert sind, der Quellcode des Designs jedoch nicht im Dateisystem vorhanden ist, wird das Design ignoriert (d. h. nicht registriert).
>- _Designentfernung_. Wenn in `config.php` kein Design vorhanden ist, der Quellcode jedoch im Dateisystem vorhanden ist, wird das Design nicht entfernt.
