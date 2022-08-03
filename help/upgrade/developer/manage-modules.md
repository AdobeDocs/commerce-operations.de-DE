---
title: Module und Erweiterungen verwalten (Entwickler)
description: Verwalten Sie Adobe Commerce- und Magento Open Source-Module und -Erweiterungen über die Befehlszeilenschnittstelle und den Composer-Paketmanager.
source-git-commit: 3432ba8640a82269cb725b8b15854f20c270b1e3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Module und Erweiterungen verwalten

Beitragen Sie Entwickler zur Aktualisierung von Modulen und Erweiterungen, indem Sie ihre Versionen in der Adobe Commerce oder Magento Open Source angeben `composer.json` -Datei. Wenn Sie kein Entwickler sind, lesen Sie [Durchführen eines Upgrades](../implementation/perform-upgrade.md).

Sie können entweder eine `require` Abschnitt `composer.json` oder Sie können die `composer require` -Befehl wie folgt:

{{$include /help/_includes/server-login.md}}

Sie haben die folgenden Optionen:

## Verfügbare Modulversionen abrufen

Befehlsverwendung:

```bash
composer show --all <vendor>/<name>
```

Beispiel:

```bash
composer show --all example/module
```

## Verwenden Sie die `composer require` command

Befehlsverwendung:

```bash
composer require <vendor>/<name>:<version>
```

Beispiel:

```bash
composer require example/module:1.0.0
```

Warten Sie, während Composer Abhängigkeiten aktualisiert und das Modul installiert.

## Hinzufügen einer `require` Abschnitt zur Datei &quot;composer.json&quot;hinzu.

1. Öffnen Sie die `composer.json` in einem Texteditor.

1. Hinzufügen einer `require` Abschnitt.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Speichern Sie Ihre Änderungen in der `composer.json` und beenden Sie den Texteditor.

1. Abhängigkeiten auflösen und exakte Versionen in die `composer.lock` -Datei.

   ```bash
   composer update
   ```
