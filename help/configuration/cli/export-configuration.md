---
title: Konfigurationseinstellungen exportieren
description: Exportieren Sie die Adobe Commerce-Konfigurationseinstellungen in Konfigurationsdateien, die auch als "config dump"bezeichnet werden.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Konfigurationseinstellungen exportieren

In Commerce 2.2 und höher [können Sie das Pipeline-Bereitstellungsmodell](../deployment/technical-details.md) systemübergreifend konsistent konfigurieren. Nachdem Sie die Einstellungen in Admin auf Ihrem Entwicklungssystem konfiguriert haben, exportieren Sie diese Einstellungen mit dem folgenden Befehl in Konfigurationsdateien:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ ist eine durch Leerzeichen getrennte Liste von Konfigurationstypen, die abgelegt werden sollen. Verfügbare Typen sind `scopes`, `system`, `themes` und `i18n`. Wenn keine Konfigurationstypen angegeben sind, werden alle Systemkonfigurationsinformationen vom Befehl ausgegeben.

Im folgenden Beispiel werden nur Bereiche und Designs ausgegeben:

```bash
bin/magento app:config:dump scopes themes
```

Aufgrund der Befehlsausführung werden die folgenden Konfigurationsdateien aktualisiert:

- `app/etc/config.php`

  Dies ist die freigegebene Konfigurationsdatei für alle Ihre Commerce-Instanzen.
Fügen Sie dies in Ihre Quell-Code-Verwaltung ein, damit es von den Entwicklungs-, Build- und Produktionssystemen gemeinsam genutzt werden kann.

  Siehe [Referenz &quot;config.php&quot;](../reference/config-reference-configphp.md).

- `app/etc/env.php`

  Dies ist die umgebungsspezifische Konfigurationsdatei.
Es enthält sensible und systemspezifische Einstellungen für einzelne Umgebungen.

  Schließen Sie diese Datei _nicht_ in die Quell-Code-Verwaltung ein.

  Siehe [env.php reference](../reference/config-reference-envphp.md).

## Sensible oder systemspezifische Einstellungen

Verwenden Sie den Befehl [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values), um die sensiblen Einstellungen auf `env.php` festzulegen.

Konfigurationswerte werden entweder als vertraulich oder systemspezifisch angegeben, indem in der Datei [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) des Moduls auf [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) verwiesen wird.

Wenn Sie bei Verwendung von `config_types` zusätzliche Systemeinstellungen exportieren möchten, sollten Sie den Befehl [`bin/magento config:set`](set-configuration-values.md#set-values) verwenden.
