---
title: Einstellung des Betriebsmodus
description: Erfahren Sie, wie Sie Adobe Commerce-Betriebsmodi zwischen Entwickler- und Produktionsmodus festlegen. Erfahren Sie mehr über Befehle zum Moduswechsel und die Auswirkungen auf die Sicherheit.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Einstellung des Betriebsmodus

{{file-system-owner}}

Um die Sicherheit und Benutzerfreundlichkeit zu verbessern, haben wir einen Befehl hinzugefügt, der [Anwendungsmodi](../bootstrap/application-modes.md) von Entwickler zu Produktion und umgekehrt wechselt.

Der Produktionsmodus hat eine bessere Leistung, da statische Ansichtsdateien im `pub/static`-Verzeichnis und aufgrund der Code-Kompilierung gefüllt werden.

>[!INFO]
>
>In Version 2.0.6 und höher legt Commerce keine expliziten Datei- oder Ordnerberechtigungen fest, wenn zwischen Standard-, Entwicklungs- und Produktionsmodus gewechselt wird. Im Gegensatz zu anderen Modi werden Entwickler- und Produktionsmodi in der `env.php` festgelegt. Adobe Commerce auf Cloud-Infrastrukturen unterstützt nur Produktions- und Wartungsmodi.
>
>Siehe [Verantwortlichkeit und Berechtigungen für Commerce in Entwicklung und Produktion](../deployment/file-system-permissions.md).

Wenn Sie in den Entwickler- oder Produktionsmodus wechseln, löschen wir den Inhalt der folgenden Verzeichnisse:

```
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Ausnahmen:

- `.htaccess` Dateien werden nicht entfernt
- `pub/static` enthält eine -Datei, die die Version des statischen Inhalts angibt; diese Datei wird nicht entfernt

>[!INFO]
>
>Standardmäßig verwendet Commerce die `var`, um den Cache, die Protokolle und den kompilierten Code zu speichern. Sie können dieses Verzeichnis anpassen, aber in diesem Handbuch wird davon ausgegangen, dass es `var` ist.

## Anzeigen des aktuellen Modus

Die einfachste Möglichkeit, dies zu erreichen, besteht darin, diesen Befehl als [Dateisystembesitzer“ &#x200B;](../../installation/prerequisites/file-system/overview.md). Wenn Sie geteiltes Hosting haben, ist dies der Benutzer, den Ihr Anbieter Ihnen zur Anmeldung beim Server gibt. Wenn Sie über einen privaten Server verfügen, handelt es sich normalerweise um ein lokales Benutzerkonto auf dem Commerce-Server.

Befehlsverwendung:

```bash
bin/magento deploy:mode:show
```

Eine Meldung ähnlich der folgenden wird angezeigt:

```
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

Dabei gilt:

- **`{mode}`** kann entweder `default`, `developer` oder `production` sein

## Modi ändern

Befehlsverwendung:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

Dabei gilt:

- **`{mode}`** ist erforderlich. Es kann entweder `developer` oder `production` sein

- **`--skip-compilation`** ist ein optionaler Parameter, mit dem Sie die [Code-Kompilierung](../cli/code-compiler.md) überspringen können, wenn Sie in den Produktionsmodus wechseln.

Es folgen Beispiele.

### In Produktionsmodus wechseln

```bash
bin/magento deploy:mode:set production
```

Meldungen ähnlich der folgenden werden angezeigt:

```
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

### Wechseln in den Entwicklermodus

Wenn Sie vom Produktions- in den Entwicklermodus wechseln, sollten Sie generierte Klassen und Objekt-Manager-Entitäten wie Proxys löschen, um unerwartete Fehler zu vermeiden. Danach können Sie den Modus ändern. Führen Sie dazu folgende Schritte aus:

1. Wenn Sie vom Produktionsmodus in den Entwicklermodus wechseln, löschen Sie die Inhalte der `generated/code`- und `generated/metadata`:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Einstellen des Modus:

   ```bash
   bin/magento deploy:mode:set developer
   ```

   Die folgende Meldung wird angezeigt:

   ```
   Enabled developer mode.
   ```

### In Standardmodus wechseln

```bash
bin/magento deploy:mode:set default
```

Die folgende Meldung wird angezeigt:

```
Enabled default mode.
```

### CLI-Befehle von überall aus ausführen

[CLI-Befehle von überall aus ausführen](../cli/config-cli.md#config-install-cli-first).

Wenn Sie `<Commerce-install-directory>/bin` nicht zu Ihrem `PATH` hinzugefügt haben, können Sie einen Fehler erwarten, wenn Sie den Befehl allein ausführen.
