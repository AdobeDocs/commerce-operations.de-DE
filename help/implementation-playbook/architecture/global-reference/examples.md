---
title: Beispiele für globale Referenzarchitekturen
description: Siehe Beispiele für die Verwaltung von Code für große Adobe Commerce-Projekte.
role: Developer, Architect
level: Experienced
source-git-commit: 64f330919abab9644de1163c9a6d6501a9c50cc1
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---


# Beispiele für globale Referenzarchitekturen

In diesem Thema werden gängige Methoden zur Organisation einer [globale Referenzarchitektur (GRA)](overview.md) Codebasis. Obwohl die Variable [separate Pakete](#option-1-separate-packages) empfohlen wird, erfordern einige Situationen eine der anderen unten beschriebenen Optionen.

## Definitionen

{{$include /help/_includes/gra-definitions.md}}

## Option 1: Separate Pakete

Siehe [Projektstruktur des Composers](composer/project-structure.md) Best Practices für die Einrichtung dieser Methode.

![Abbildung der Option für separate Pakete für die globale Referenzarchitektur](../../../assets/playbooks/gra-separate-packages.png)

Die flexibelste Methode zur Verwaltung von GRA Composer-Paketen besteht in Metapaketen. Metapakete enthalten eine `composer.json` -Datei, die andere Paketabhängigkeiten definiert. Erstellen von Metapaketen mit [Private Packagist](https://packagist.com/) Repositorys

### Hauptprojekt `composer.json`

```json
{
    "name": "example-client/region-1",
    "description": "Example Client Region 1",
    "type": "project",
    "require": {
        "magento/product-enterprise-edition": "2.3.5",
        "example-client/meta-region-1": "~1.0"
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {"type": "composer", "url": "https://repo.packagist.com/example-client/"},
        {"packagist.org": false}
    ]
}
```

### `example-client/meta-region-1 composer.json`

```json
{
    "name": "example-client/meta-region-1",
    "description": "Region 1 meta package",
    "type": "metapackage",
    "require": {
        "example-client/meta-gra": "~1.0",
        "example-client/theme-frontend-region1",
        "example-client/language-es-es",
        "ingenico/ogone-client"
    }
}
```

### `example-client/meta-gra composer.json`

```json
{
    "name": "example-client/meta-gra",
    "description": "GRA meta package",
    "type": "metapackage",
    "require": {
        "geoip2/geoip2": "~2.0",
        "magento-services/module-stackify-logger": "~1.1",
        "example-client/sap-connector",
        "example-client/service-chat",
        "example-client/store-locator"
    }
}
```

Jedes Modul, Sprachpaket, Design und jede Bibliothek verfügt über ein eigenes Git-Repository. Jedes Git-Repository synchronisiert automatisch mit dem privaten Packagist-Repository und generiert dort ein Paket, solange ein `composer.json` im Stammverzeichnis des Git-Repositorys.

## Optionen 2: Massenpakete

Nachfolgend finden Sie ein Beispiel für mehrere Module in einem einzelnen Composer-Paket.

Ein Massenpaket kann nur Pakete desselben Typs enthalten. Wenn Sie beispielsweise mehrere Pakete für Adobe Commerce-Module, Designs, Sprachpakete und Bibliotheken haben, müssen Sie für jeden Typ separate Bulk-Pakete erstellen.

Die Dateistruktur im Verzeichnis &quot;Anbieter&quot;sollte wie im folgenden Beispiel aussehen. Prüfen Sie jedoch Ihr Projekt, um zu sehen, was in Ihrem Git-Repository enthalten sein sollte):

```tree
.
└── example-client/
    └── gra/
        └── src/
            ├── SapConnector/
            │   ├── etc/
            │   └── registration.php
            ├── ServiceChat/
            │   ├── etc/
            │   └── registration.php
            ├── StoreLocator/
            │   ├── etc/
            │   └── registration.php
            └── composer.json
```

Die `composer.json` sollte wie folgt aussehen:

```json
{
    "name": "example-client/gra",
    "description": "GRA Modules",
    "require": {
        "magento/magento-composer-installer": "*"
    },
    "type": "magento2-module",
    "autoload": {
        "files": [
            "src/SapConnector/registration.php",
            "src/ServiceChat/registration.php",
            "src/StoreLocator/registration.php"
        ],
        "psr-4": {
            "ExampleClient\\SapConnector\\": "src/SapConnector",
            "ExampleClient\\ServiceChat\\": "src/ServiceChat",
            "ExampleClient\\StoreLocator\\": "src/StoreLocator"
        }
    }
}
```

## Option 3: Git teilen

Diese Architektur verwendet vier Git-Repositorys zum Speichern von Code:

- `core`: Enthält die Adobe Commerce-Kerninstallation. Wird verwendet, um Adobe Commerce-Versionen zu aktualisieren.
- `GRA`: Enthält GRA-Code. Alle GRA-Module, Sprachpakete, White Label-Designs und Bibliotheken.
- `brand/region`: Jede Marke oder Region verfügt über ein eigenes Repository mit nur marken- oder regionsspezifischem Code.
- `release`: Alle oben genannten Elemente werden in diesem Git-Repository zusammengeführt. Hier sind nur Zusammenführungsbefehle zulässig.

![Abbildung der Git-Aufspaltungsoption für die globale Referenzarchitektur](../../../assets/playbooks/gra-split-git.png)

So richten Sie diese Option ein:

1. Erstellen Sie die vier Repository-Typen in Git. Erstellen Sie die `core` und `GRA` Repositorys nur einmal. Erstellen einer `brand/region` und einem `release` Repository für jede Marke.

   Vorgeschlagene Repository-Namen:

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` (zum Beispiel: `m2-emea`/`m2-adobe`)
   - `m2-release-region-x`/`m2-release-brand-x` (zum Beispiel: `m2-release-emea`/`m2-release-adobe`)

1. Erstellen Sie eine `release/` und führen Sie Folgendes aus, um einen freigegebenen Git-Verlauf für alle Repos zu erstellen.

   ```bash
   git init
   git remote add origin git@github.com:example-client/m2-release-brand-x.git
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   touch .gitkeep
   git add .gitkeep
   git commit -m 'initialize repository'
   git push -u origin master
   git push core master
   git push gra master
   git push region-x master
   ```

1. Jedes Repository klonen, außer `core`, in einem anderen Verzeichnis auf Ihrem Computer.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [Installieren von Adobe Commerce mit Composer](../../../installation/composer.md). Entfernen Sie die `.gitignore` -Datei, fügen Sie die `core` entfernen, den Code hinzufügen und übertragen und pushen.

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition m2-core
   cd m2-core
   git init
   rm .gitignore
   git remote add origin git@github.com:example-client/m2-core.git
   git fetch
   git checkout .gitkeep
   git add --all
   git commit -m 'install Adobe Commerce'
   git push
   ```

1. Im `GRA` Repository erstellen Sie die folgenden Verzeichnisse:

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. Code hinzufügen. Entfernen Sie die `.gitignore` -Datei, fügen Sie den Code hinzu und übertragen Sie ihn, fügen Sie die Remote- und Push-Benachrichtigung hinzu.

1. Im `brand/region` Repository. Gehen Sie wie in `GRA` Repository zu speichern und zu beachten, dass Dateien eindeutig sein müssen. Dieselbe Datei kann nicht sowohl in dieses Repository als auch in die `GRA` Repository.

1. Im `release` Repository verwenden, die Zusammenführung anwenden.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   cd m2-release-brand-x
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

1. Entfernen Sie die `.gitkeep` -Datei.

1. Stellen Sie die `release` Repository auf den Produktions-, Test-, QA- und Entwicklungsservern. Upgrade `core`, `GRA`, und `brand` -Code ist so einfach, die folgenden Befehle auszuführen:

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## Option 4: Monorepo (empfohlen)

Diese Strategie ahmt genau nach, wie das Magento Open Source-Git-Repository funktioniert.

Der gesamte Code wird in einem einzigen Repository entwickelt und getestet. Durch die Automatisierung werden Pakete aus diesem einzigen Repository entfernt, das mithilfe von Composer in UAT- und Produktionsumgebungen installiert werden kann.

![Abbildung der Monorepo-Option für die globale Referenzarchitektur](../../../assets/playbooks/gra-monorepo1.png)

Die monorepo -Option ermöglicht Ihnen die einfache Arbeit in einem einzelnen Repository und bietet gleichzeitig die Flexibilität, Instanzen mit Paketen zusammenzustellen.

Die Versionierung und Paketdestillation erfolgt durch Automatisierung, mithilfe von GitHub-Aktionen oder GitLab-Aktionen.

![Abbildung der Monorepo-Option für die globale Referenzarchitektur](../../../assets/playbooks/gra-monorepo2.png)

Weitere Informationen zu dieser Automatisierung finden Sie in den folgenden Ressourcen:

- [https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>Die Einrichtung eines Monorepos ist zwar fortgeschritten, bietet jedoch die größte Flexibilität bei den geringsten Gemeinkosten.

## Strategien nicht mischen

Es ist nicht ratsam, einen kombinierten Ansatz mit Composer für GRA-Pakete und die `app/` Verzeichnis für Marken- oder Regionspakete.

Sie bekommen nicht nur alle _Vorteile_ aber auch _Nachteile_ von beiden Methoden. Sie sollten das eine oder das andere auswählen (Git oder Composer), um optimal zu funktionieren.

## Lösungen zur Vermeidung

- **Namenskonventionen für Module zur Angabe von GRA oder Marke**

  Namensmodule, die GRA oder Marke darstellen, führen zu mangelnder Flexibilität. Verwenden Sie stattdessen Composer-Metapakete, um zu bestimmen, zu welcher Gruppe ein Modul gehört. Beispiel: Für Kunden-VF: package `vf/meta-gra` enthält Verweise auf alle GRA-Pakete und kann mithilfe der `composer require vf/meta-gra` Befehl. Paket `vf/meta-kipling` enthält Verweise auf alle Kipling-spezifischen Pakete und auf die `vf/meta-gra` Paket. Module werden `vf/module-sales` und `vf/module-sap` zum Beispiel. Mit dieser Namenskonvention können Sie Pakete mit geringer Auswirkung zwischen Marke und GRA-Status verschieben.

- **Adobe Commerce Core-Upgrades pro Instanz**

  Planen Sie zentrale Adobe Commerce-Upgrades, einschließlich Patch-Upgrades, für verschiedene Marken oder Regionen so nah wie möglich an einer Stelle wie möglich. Die Unterstützung mehrerer Adobe Commerce-Versionen für gemeinsam genutzte Module führt aufgrund von Kompatibilitätsbeschränkungen zur Abspaltung von Modulen und verdoppelt den Wartungsaufwand mehr als. Verhindern Sie diesen erhöhten Aufwand, indem Sie sicherstellen, dass alle Instanzen auf derselben Adobe Commerce-Version ausgeführt werden, bevor Sie die reguläre Entwicklung fortsetzen.
