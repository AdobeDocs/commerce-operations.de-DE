---
title: Betriebsmodus festlegen
description: Erfahren Sie mehr über das Festlegen der Adobe Commerce-Betriebsmodi.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# Betriebsmodus festlegen

{{file-system-owner}}

Um die Sicherheit und Benutzerfreundlichkeit zu verbessern, haben wir einen Befehl hinzugefügt, der umschaltet [Anwendungsmodi](../bootstrap/application-modes.md) vom Entwickler zur Produktion und umgekehrt.

Der Produktionsmodus bietet eine bessere Leistung, da statische Ansichtsdateien im `pub/static` und aufgrund der Code-Kompilierung.

>[!INFO]
>
>In Version 2.0.6 und höher legt Commerce beim Wechsel zwischen Standard-, Entwicklungs- und Produktionsmodi keine expliziten Datei- oder Ordnerberechtigungen fest. Im Gegensatz zu anderen Modi werden Entwickler- und Produktionsmodi in der Variablen `env.php` -Datei. Adobe Commerce in der Cloud-Infrastruktur unterstützt nur Produktions- und Wartungsmodi.
>
>Siehe [Eigentum und Berechtigungen für Entwicklung und Produktion im Handel](../deployment/file-system-permissions.md).

Wenn Sie in den Entwickler- oder Produktionsmodus wechseln, wird der Inhalt der folgenden Ordner gelöscht:

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Ausnahmen:

- `.htaccess` Dateien werden nicht entfernt
- `pub/static` enthält eine Datei, die die Version des statischen Inhalts angibt; Diese Datei wird nicht entfernt

>[!INFO]
>
>Standardmäßig verwendet Commerce die `var` -Ordner zum Speichern des Cache, der Protokolle und des kompilierten Codes. Sie können dieses Verzeichnis anpassen. In diesem Handbuch wird jedoch davon ausgegangen, dass `var`.

## Anzeigen des aktuellen Modus

Am einfachsten ist es, diesen Befehl als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md). Wenn Sie das Hosting freigegeben haben, ist dies der Benutzer, den Ihr Provider Ihnen zur Anmeldung beim Server bereitstellt. Wenn Sie über einen privaten Server verfügen, handelt es sich normalerweise um ein lokales Benutzerkonto auf dem Commerce-Server.

Befehlsverwendung:

```bash
bin/magento deploy:mode:show
```

Eine Meldung ähnlich der folgenden wird angezeigt:

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

wobei:

- **`{mode}`** kann `default`, `developer`oder `production`

## Änderungsmodi

Befehlsverwendung:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

wobei:

- **`{mode}`** erforderlich ist; kann `developer` oder `production`

- **`--skip-compilation`** ist ein optionaler Parameter, den Sie zum Überspringen verwenden können [Codekompilierung](../cli/code-compiler.md) wenn Sie in den Produktionsmodus wechseln.

Es folgen Beispiele.

### Produktionsmodus wechseln

```bash
bin/magento deploy:mode:set production
```

Meldungen, die der folgenden Anzeige ähneln:

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or Sass files
CSS deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### Ändern in den Entwicklermodus

Wenn Sie von der Produktion in den Entwicklermodus wechseln, sollten Sie generierte Klassen und Objekt-Manager-Entitäten wie Proxys löschen, um unerwartete Fehler zu vermeiden. Danach können Sie die Modi ändern. Führen Sie die folgenden Schritte aus:

1. Wenn Sie vom Produktionsmodus zum Entwicklermodus wechseln, löschen Sie den Inhalt der `generated/code` und `generated/metadata` Verzeichnisse:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Legen Sie den Modus fest:

   ```bash
   bin/magento deploy:mode:set developer
   ```

   Die folgende Meldung wird angezeigt:

   ```terminal
   Enabled developer mode.
   ```

### Standardmodus ändern

```bash
bin/magento deploy:mode:set default
```

Die folgende Meldung wird angezeigt:

```terminal
Enabled default mode.
```

### Ausführen von CLI-Befehlen von überall aus

[Ausführen von CLI-Befehlen von überall aus](../cli/config-cli.md#config-install-cli-first).

Wenn Sie `<Commerce-install-directory>/bin` auf Ihr System `PATH`, können Sie einen Fehler erwarten, wenn Sie den Befehl allein ausführen.
