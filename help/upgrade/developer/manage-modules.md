---
title: Module und Erweiterungen verwalten (Entwickler)
description: Verwalten Sie Adobe Commerce-Module und -Erweiterungen über die Befehlszeilenschnittstelle und den Composer-Paketmanager.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# Module und Erweiterungen verwalten

Wenn Sie Entwickler unterstützen, aktualisieren Sie Module und Erweiterungen, indem Sie ihre Versionen in der Adobe Commerce-Datei &quot;`composer.json`&quot;angeben. Wenn Sie kein Entwickler sind, lesen Sie [Durchführen einer Aktualisierung](../implementation/perform-upgrade.md).

Sie können der Datei `composer.json` entweder den Abschnitt `require` hinzufügen oder den Befehl `composer require` wie folgt verwenden:

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

## Verwenden Sie den Befehl `composer require` .

Befehlsverwendung:

```bash
composer require <vendor>/<name>:<version>
```

Beispiel:

```bash
composer require example/module:1.0.0
```

Warten Sie, während Composer Abhängigkeiten aktualisiert und das Modul installiert.

## Fügen Sie der Datei &quot;Composer.json&quot;einen Abschnitt &quot;`require`&quot;hinzu

1. Öffnen Sie die `composer.json` in einem Texteditor.

1. Fügen Sie einen Abschnitt `require` hinzu.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Speichern Sie Ihre Änderungen in der Datei `composer.json` und beenden Sie den Texteditor.

1. Lösen Sie Abhängigkeiten auf und schreiben Sie exakte Versionen in die Datei &quot;`composer.lock`&quot;.

   ```bash
   composer update
   ```
