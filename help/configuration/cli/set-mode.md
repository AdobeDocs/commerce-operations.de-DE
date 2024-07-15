---
title: Betriebsmodus festlegen
description: Erfahren Sie mehr über das Festlegen der Adobe Commerce-Betriebsmodi.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Betriebsmodus festlegen

{{file-system-owner}}

Um die Sicherheit und Benutzerfreundlichkeit zu verbessern, haben wir einen Befehl hinzugefügt, mit dem [Anwendungsmodi](../bootstrap/application-modes.md) von Entwickler zu Produktion wechselt und umgekehrt.

Der Produktionsmodus bietet eine bessere Leistung, da statische Ansichtsdateien im Verzeichnis `pub/static` und aufgrund der Code-Kompilierung gefüllt werden.

>[!INFO]
>
>In Version 2.0.6 und höher legt Commerce keine expliziten Datei- oder Ordnerberechtigungen fest, wenn Sie zwischen den Standard-, Entwicklungs- und Produktionsmodi wechseln. Im Gegensatz zu anderen Modi werden Entwickler- und Produktionsmodi in der Datei `env.php` festgelegt. Adobe Commerce on Cloud Infrastructure unterstützt nur Produktions- und Wartungsmodi.
>
>Siehe [Eigentum und Berechtigungen der Commerce in Entwicklung und Produktion](../deployment/file-system-permissions.md).

Wenn Sie in den Entwickler- oder Produktionsmodus wechseln, wird der Inhalt der folgenden Ordner gelöscht:

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Ausnahmen:

- `.htaccess` -Dateien werden nicht entfernt
- `pub/static` enthält eine Datei, die die Version des statischen Inhalts angibt. Diese Datei wird nicht entfernt

>[!INFO]
>
>Standardmäßig verwendet Commerce die Ordner &quot;`var`&quot;, um den Cache, die Protokolle und den kompilierten Code zu speichern. Sie können diesen Ordner anpassen, in diesem Handbuch wird jedoch von `var` ausgegangen.

## Anzeigen des aktuellen Modus

Am einfachsten ist es, diesen Befehl als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) auszuführen. Wenn Sie das Hosting freigegeben haben, ist dies der Benutzer, den Ihr Provider Ihnen zur Anmeldung beim Server bereitstellt. Wenn Sie über einen privaten Server verfügen, handelt es sich normalerweise um ein lokales Benutzerkonto auf dem Commerce-Server.

Befehlsverwendung:

```bash
bin/magento deploy:mode:show
```

Eine Meldung ähnlich der folgenden wird angezeigt:

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

wobei:

- **`{mode}`** kann entweder `default`, `developer` oder `production` sein.

## Änderungsmodi

Befehlsverwendung:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

wobei:

- **`{mode}`** ist erforderlich; es kann entweder `developer` oder `production` sein.

- **`--skip-compilation`** ist ein optionaler Parameter, den Sie verwenden können, um die [Codekompilierung](../cli/code-compiler.md) zu überspringen, wenn Sie in den Produktionsmodus wechseln.

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

1. Wenn Sie vom Produktionsmodus in den Entwicklermodus wechseln, löschen Sie den Inhalt der Verzeichnisse `generated/code` und `generated/metadata`:

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

[ Führen Sie CLI-Befehle von überall aus aus aus.](../cli/config-cli.md#config-install-cli-first)

Wenn Sie `<Commerce-install-directory>/bin` nicht zu Ihrem System `PATH` hinzugefügt haben, können Sie einen Fehler erwarten, wenn Sie den Befehl allein ausführen.
