---
title: Daten aus Konfigurationsdateien importieren
description: Importieren Sie die Adobe Commerce-Konfigurationseinstellungen aus Konfigurationsdateien.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# Konfigurationseinstellungen importieren

{{file-system-owner}}

Wenn Sie ein Produktionssystem mit Commerce 2.2 einrichten [Pipeline-Bereitstellungsmodell](../deployment/technical-details.md), müssen Sie _importieren_ Konfigurationseinstellungen aus `config.php` und `env.php` in die Datenbank.
Zu diesen Einstellungen gehören Konfigurationspfade und -werte, Websites, Stores, Store-Ansichten und Designs.

Nach dem Import von Websites, Geschäften, Ansichten und Designs können Sie Produktattribute erstellen und auf Websites, Stores und Store-Ansichten im Produktionssystem anwenden.

>[!INFO]
>
>Die `bin/magento app:config:import` -Befehl verarbeitet keine in Umgebungsvariablen gespeicherte Konfiguration.

## Import, Befehl

Führen Sie auf Ihrem Produktionssystem den folgenden Befehl aus, um Daten aus den Konfigurationsdateien zu importieren (`config.php` und `env.php`) in die Datenbank:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Verwenden Sie das optionale `[-n, --no-interaction]` -Markierung verwenden, um Daten ohne Interaktion zu importieren.

Wenn Sie `bin/magento app:config:import` ohne die optionale Markierung müssen Sie die Änderungen bestätigen.

Wenn die Konfigurationsdatei beispielsweise eine neue Website und einen neuen Store enthält, wird die folgende Meldung angezeigt:

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Um den Import fortzusetzen, geben Sie `yes`.

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

Commerce verwendet direkt Werte in der `system` -Array im `config.php` oder `env.php` -Dateien, anstatt sie in die Datenbank zu importieren, da sie einige Vorab- und Nachbearbeitungsaktionen erfordern.

Beispielsweise der Wert des Konfigurationspfads `web/secure/base_url` muss mit Backend-Modellen validiert werden.

#### Backend-Modelle

Backend-Modelle sind der Mechanismus zur Verarbeitung von Änderungen in der Systemkonfiguration.
Sie definieren Backend-Module in `<module_name>/adminhtml/system.xml`.

Alle Backend-Modelle müssen die [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) -Klasse.

Beim Importieren von Backend-Modellen werden die Konfigurationswerte nicht gespeichert.

### Konfiguration von Websites, Stores und Stores

Wir importieren die folgenden Arten von Konfigurationen.
(Diese Konfigurationen befinden sich unter der `scopes` Array in `config.php`.

- `websites`: Website-bezogene Konfiguration
- `groups`: Speichert verwandte Konfiguration
- `stores`: Konfiguration von Store-Ansichten

Die vorangehenden Konfigurationen können in den folgenden Modi importiert werden:

- `create`: `config.php` enthält neue Entitäten (`websites`, `groups`, `stores`), die in der Produktionsumgebung fehlen
- `update`: `config.php` enthält Entitäten (`websites`, `groups`, `stores`), die sich von der Produktionsumgebung unterscheiden
- `delete`: `config.php` does _not_ enthält Entitäten (`websites`, `groups`, `stores`), die in der Produktionsumgebung vorhanden sind

>[!INFO]
>
>Die mit Stores verknüpfte Stammkategorie wird nicht importiert. Sie müssen mit dem Commerce Admin eine Stammkategorie mit einem Store verknüpfen.

### Designkonfiguration

Die Designkonfiguration umfasst alle Designs, die in Ihrem Commerce-System registriert sind. Die Daten stammen direkt aus dem `theme` Datenbanktabelle. (Die Designkonfiguration befindet sich im Abschnitt `themes` Array in `config.php`.

#### Struktur der Designdaten

Der Schlüssel des Arrays ist der vollständige Designpfad: `area` + `theme path`

Beispiel: `frontend/Magento/luma`.
`frontend` ist und `Magento/luma` ist der Designpfad.

Der Wert des Arrays ist Daten zum Design: Code, Titel, Pfad, übergeordnete ID

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
>- _Themenregistrierung_. Wenn Designdaten definiert sind in `config.php` Der Quellcode des Designs ist jedoch nicht im Dateisystem vorhanden, das Design wird ignoriert (d. h. nicht registriert).
>- _Designlöschung_. Wenn ein Design nicht in `config.php` , der Quellcode jedoch im Dateisystem vorhanden ist, wird das Design nicht entfernt.

