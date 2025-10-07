---
title: Bereitstellungsfluss
description: Erfahren Sie mehr über den Bereitstellungsprozess für Adobe Commerce-Produktionsumgebungen. Erfahren Sie mehr über die Schritte, die für maximale Leistung und Zuverlässigkeit erforderlich sind.
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Bereitstellungsfluss

Der [!DNL Commerce] Produktionsbereitstellungsfluss hilft einem Store, die maximale Leistung zu erreichen.

## Installieren von Abhängigkeiten

Die `composer.json`- und `composer.lock` verwalten [!DNL Commerce] Abhängigkeiten und installieren die entsprechende Version für jedes Paket. Sie müssen Abhängigkeiten vor [Injections-Anweisungen für die Vorverarbeitung](#preprocess-dependency-injection-instructions) installieren, wenn Sie den [Autoloader“ aktualisieren &#x200B;](#update-the-autoloader).

So installieren Sie [!DNL Commerce]:

```bash
composer install --no-dev
```

## Anweisungen zur Voreinstellung der Injektion von Abhängigkeiten

Wenn Sie Anweisungen zur Injektion von Abhängigkeiten (Dependency Injection, DI) vorverarbeiten und kompilieren, führt Magento Folgendes aus:

* Liest und verarbeitet alle vorhandenen Konfigurationen
* Analysiert Abhängigkeiten zwischen Klassen
* Erstellt automatisch generierte Dateien (einschließlich Proxys, Factories usw.)
* Speichert kompilierte Daten und Konfiguration in einem Cache, der bei der Verarbeitung von Anfragen bis zu 25 % Zeit spart

So verarbeiten und kompilieren Sie ID-Anweisungen:

```bash
bin/magento setup:di:compile
```

## Autoloader aktualisieren

Bestätigen Sie nach Abschluss der Kompilierung, dass [APCu aktiviert ist](../performance/software.md#php-settings) und aktualisieren Sie den Autoloader:

So aktualisieren Sie den Autoloader:

>[!INFO]
>
>Die `-o` Option konvertiert PSR-0/4-Autoloading in Classmap, um einen schnelleren Autoloader zu erhalten. Die `--apcu` Option verwendet APCu, um gefundene/nicht gefundene Klassen zwischenzuspeichern.

```bash
composer dump-autoload -o --apcu
```

Wenn Sie den Autoloader aktualisieren möchten, müssen Sie die folgenden Befehle in der richtigen Reihenfolge ausführen:

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## Statischen Inhalt bereitstellen

Bei der Bereitstellung statischer Inhalte führen [!DNL Commerce] die folgenden Aktionen aus:

* Alle statischen Ressourcen analysieren
* Zusammenführen, Minimieren und Bündeln von Inhalten
* Lesen und Verarbeiten von Designdaten
* Design-Fallback analysieren
* Alle verarbeiteten und materialisierten Inhalte in einem bestimmten Ordner zur weiteren Verwendung speichern

Wenn Ihr statischer Inhalt nicht bereitgestellt wird, führt [!DNL Commerce] alle aufgelisteten Vorgänge spontan durch, was zu einer erheblichen Verlängerung der Reaktionszeit führt.

Sie können eine Vielzahl von Optionen verwenden, um Bereitstellungsvorgänge auf der Grundlage der Store-Größe und der Erfüllungsanforderungen anzupassen. Die häufigste ist die kompakte Bereitstellungsstrategie. Siehe [Strategien zur Bereitstellung statischer Dateien](../configuration/cli/static-view-file-strategy.md)

So stellen Sie statische Inhalte bereit:

```bash
bin/magento setup:static-content:deploy
```

Dieser Befehl ermöglicht es Composer, die Zuordnung zu Projektdateien neu zu erstellen, sodass sie schneller geladen werden.

## Festlegen des Produktionsmodus

>[!INFO]
>
>Wenn Sie den -Modus auf Produktion setzen, wird automatisch `setup:di:compile` und `setup:static-content:deploy` ausgeführt.

Schließlich müssen Sie Ihren Store in den Produktionsmodus versetzen. Der Produktionsmodus wurde speziell für die maximale Leistung Ihres Geschäfts optimiert. Außerdem werden dadurch alle entwicklerspezifischen Funktionen deaktiviert. Dies kann in Ihrer `.htaccess`- oder `nginx.conf`-Datei erfolgen:

`SetEnv MAGE_MODE production`

Sie können auch statische Inhalte bereitstellen, den Inhalt kompilieren und den Modus in einem CLI-Befehl festlegen:

```bash
bin/magento deploy:mode:set production
```

Der Befehl wird im Hintergrund ausgeführt und erlaubt es nicht, bei jedem Schritt zusätzliche Optionen festzulegen.

## Zusätzliche Aktionen vor dem Start

Diese Schritte werden empfohlen, sind jedoch nicht obligatorisch. Sie können sie unmittelbar vor dem Starten Ihres Stores im Produktionsmodus ausführen. Die Liste umfasst:

* Indizieren Sie Daten neu, um zu vermeiden, dass die Indizes inkonsistente Daten enthalten.
* Leeren Sie den Cache, um sicherzustellen, dass keine alten oder falschen Daten im Cache verbleiben.
* Erwärmen Sie den Cache, der die beliebtesten oder wichtigsten Store-Seiten im Voraus aufruft, damit der Cache für sie generiert und gespeichert wird. Dieser Vorgang kann mit jedem Internet-Crawler oder manuell durchgeführt werden, wenn Sie einen kleinen Store haben.
