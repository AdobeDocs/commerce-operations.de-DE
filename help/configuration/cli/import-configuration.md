---
title: Importieren von Daten aus Konfigurationsdateien
description: Importieren Sie Adobe Commerce-Konfigurationseinstellungen aus Konfigurationsdateien.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Konfigurationseinstellungen importieren

{{file-system-owner}}

Wenn Sie ein Produktionssystem mit dem Commerce 2.2 [Pipeline-Bereitstellungsmodell](../deployment/technical-details.md) einrichten, müssen Sie _aus `config.php` und `env.php` in die_ importieren.
Zu diesen Einstellungen gehören Konfigurationspfade und -werte, Websites, Stores, Store-Ansichten und Designs.

Nach dem Import von Websites, Stores, Store-Ansichten und Designs können Sie Produktattribute erstellen und sie auf Websites, Stores und Store-Ansichten im Produktionssystem anwenden.

>[!INFO]
>
>Der Befehl `bin/magento app:config:import` verarbeitet keine in Umgebungsvariablen gespeicherte Konfiguration.

## Importbefehl

Führen Sie auf Ihrem Produktionssystem den folgenden Befehl aus, um Daten aus den Konfigurationsdateien (`config.php` und `env.php`) in die Datenbank zu importieren:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Verwenden Sie das optionale `[-n, --no-interaction]`-Flag, um Daten ohne Interaktion zu importieren.

Wenn Sie `bin/magento app:config:import` ohne die optionale Markierung eingeben, müssen Sie die Änderungen bestätigen.

Wenn die Konfigurationsdatei beispielsweise eine neue Website und einen neuen Store enthält, wird die folgende Meldung angezeigt:

```
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Um den Import fortzusetzen, geben Sie `yes` ein.

Wenn Bereitstellungskonfigurationsdateien einige zu importierende Daten enthalten, wird eine Meldung ähnlich der folgenden angezeigt:

```
Start import:
Some information about importing
```

Wenn Bereitstellungskonfigurationsdateien keine zu importierenden Daten enthalten, wird eine Meldung ähnlich der folgenden angezeigt:

```
Start import:
Nothing to import
```

## Was wir importieren

In den folgenden Abschnitten wird ausführlich erläutert, welche Daten wir importieren.

### Systemkonfiguration

Commerce verwendet Werte im `system`-Array direkt in den `config.php`- oder `env.php`-Dateien, anstatt sie in die Datenbank zu importieren, da sie einige Vor- und Nachbearbeitungsaktionen erfordern.

Beispielsweise muss der Wert des Konfigurationspfads `web/secure/base_url` mit Backend-Modellen validiert werden.

#### Backend-Modelle

Backend-Modelle sind der Mechanismus zum Verarbeiten von Änderungen an der Systemkonfiguration.
Backend-Module werden in `<module_name>/adminhtml/system.xml` definiert.

Alle Backend-Modelle müssen die [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php)-Klasse erweitern.

Beim Importieren von Backend-Modellen werden die Konfigurationswerte nicht gespeichert.

### Konfiguration von Websites, Stores und Store-Gruppen

Wir importieren die folgenden Arten von Konfigurationen.
(Diese Konfigurationen befinden sich unter dem `scopes` Array in `config.php`.)

- `websites`: Websites-bezogene Konfiguration
- `groups`: speichert die zugehörige Konfiguration
- `stores`: Konfiguration im Zusammenhang mit Ansichten speichern

Die vorherigen Konfigurationen können in den folgenden Modi importiert werden:

- `create`: `config.php` enthält neue Entitäten (`websites`, `groups`, `stores`), die in der Produktionsumgebung fehlen
- `update`: `config.php` enthält Entitäten (`websites`, `groups`, `stores`), die sich von der Produktionsumgebung unterscheiden
- `delete`: `config.php` enthält _nicht_ Entitäten (`websites`, `groups`, `stores`), die in der Produktionsumgebung vorhanden sind

>[!INFO]
>
>Die mit Stores verknüpfte Stammkategorie wird nicht importiert. Sie müssen mit der Commerce Admin eine Stammkategorie mit einem Store verknüpfen.

### Design-Konfiguration

Die Designkonfiguration umfasst alle Designs, die in Ihrem Commerce-System registriert sind. Die Daten stammen direkt aus der `theme` Datenbanktabelle. (Die Design-Konfiguration befindet sich im `themes`-Array in `config.php`.)

#### Struktur der Designdaten

Der Schlüssel des Arrays ist der vollständige Designpfad: `area` + `theme path`

Beispiel: `frontend/Magento/luma`.
`frontend` ist „area“ und `Magento/luma` ist „theme path“.

Der Wert des Arrays besteht aus Daten zum Design: Code, Titel, Pfad, übergeordnete ID

Beispiel:

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
>- _Design-Registrierung_. Wenn Design-Daten in `config.php` definiert sind, der Quell-Code des Designs jedoch nicht im Dateisystem vorhanden ist, wird das Design ignoriert (d. h. nicht registriert).
>- _Design-Entfernung_. Wenn in `config.php` kein Design vorhanden ist, der Quell-Code jedoch im Dateisystem vorhanden ist, wird das Design nicht entfernt.
