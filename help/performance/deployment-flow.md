---
title: Bereitstellungsfluss
description: Erfahren Sie mehr über die Schritte, die für die Bereitstellung von Adobe Commerce in einer Produktionsumgebung erforderlich sind.
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Implementierungsfluss

Der Produktionsbereitstellungsfluss [!DNL Commerce] hilft einem Store, die maximale Leistung zu erreichen.

## Installieren von Abhängigkeiten

Die Dateien `composer.json` und `composer.lock` verwalten [!DNL Commerce] Abhängigkeiten und installieren die entsprechende Version für jedes Paket. Sie müssen Abhängigkeiten vor [Anweisungen zur Vorverarbeitung der Abhängigkeitsinjektion](#preprocess-dependency-injection-instructions) installieren, wenn Sie planen, den [Autoloader](#update-the-autoloader) zu aktualisieren.

So installieren Sie [!DNL Commerce] -Abhängigkeiten:

```bash
composer install --no-dev
```

## Anweisungen zur Injektion von Vorprozessabhängigkeiten

Magento:

* Alle vorhandenen Konfigurationen werden gelesen und verarbeitet
* Analysiert Abhängigkeiten zwischen Klassen
* Erstellt automatisch generierte Dateien (einschließlich Proxys, Fabriken usw.)
* Speichert kompilierte Daten und Konfigurationen in einem Cache, der bis zu 25 % Zeit bei der Verarbeitung von Anforderungen einspart

So erstellen und kompilieren Sie ID-Anweisungen:

```bash
bin/magento setup:di:compile
```

## Aktualisieren des Autoloaders

Bestätigen Sie nach Abschluss der Kompilierung, dass [APCu aktiviert ist](../performance/software.md#php-settings), und aktualisieren Sie den Autoloader:

So aktualisieren Sie den Autoloader:

>[!INFO]
>
>Die Option `-o` konvertiert das automatische Laden von PSR-0/4 in Classmap, um einen schnelleren Autoloader zu erhalten. Die Option `--apcu` verwendet APCu, um gefundene/nicht gefundene Klassen zwischenzuspeichern.

```bash
composer dump-autoload -o --apcu
```

Wenn Sie die Aktualisierung des Autoloaders planen, müssen Sie die folgenden Befehle in der richtigen Reihenfolge ausführen:

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

Durch das Bereitstellen von statischem Inhalt führt [!DNL Commerce] die folgenden Aktionen aus:

* Alle statischen Ressourcen analysieren
* Zusammenführen, Minimieren und Bündeln von Inhalten
* Designdaten lesen und verarbeiten
* Fallback zum Thema analysieren
* Speichern Sie alle verarbeiteten und materialisierten Inhalte in einem bestimmten Ordner für die weitere Verwendung.

Wenn Ihr statischer Inhalt nicht bereitgestellt wird, führt [!DNL Commerce] alle aufgelisteten Vorgänge direkt durch, was zu einer erheblichen Zeitsteigerung der Antwort führt.

Sie können verschiedene Optionen verwenden, um Bereitstellungsvorgänge basierend auf der Speichergröße und den Anforderungen an die Erfüllung anzupassen. Am häufigsten ist die kompakte Bereitstellungsstrategie. Siehe [Bereitstellungsstrategien für statische Dateien](../configuration/cli/static-view-file-strategy.md)

So stellen Sie statischen Inhalt bereit:

```bash
bin/magento setup:static-content:deploy
```

Mit diesem Befehl kann Composer die Zuordnung zu Projektdateien neu erstellen, damit sie schneller geladen werden.

## Produktionsmodus festlegen

>[!INFO]
>
>Wenn Sie den Modus auf &quot;Produktion&quot;einstellen, werden automatisch `setup:di:compile` und `setup:static-content:deploy` ausgeführt.

Schließlich müssen Sie Ihren Store im Produktionsmodus platzieren. Der Produktionsmodus ist speziell für die maximale Leistung Ihres Stores optimiert. Außerdem werden alle entwicklerspezifischen Funktionen deaktiviert. Dies kann in Ihrer `.htaccess` - oder `nginx.conf` -Datei erfolgen:

`SetEnv MAGE_MODE production`

Sie können auch statischen Inhalt bereitstellen, den Inhalt kompilieren und den Modus in einem CLI-Befehl festlegen:

```bash
bin/magento deploy:mode:set production
```

Der Befehl wird im Hintergrund ausgeführt und ermöglicht es nicht, zusätzliche Optionen für jeden einzelnen Schritt festzulegen.

## Zusätzliche Vorab-Launch-Aktionen

Diese Schritte werden empfohlen, sind jedoch nicht obligatorisch. Sie können sie sofort ausführen, bevor Sie Ihren Store im Produktionsmodus starten. Die Liste umfasst:

* Indizieren Sie Daten neu, um das Vorhandensein inkonsistenter Daten in Ihren Indizes zu vermeiden.
* Leeren Sie den Cache, um sicherzustellen, dass keine alten oder falschen Daten im Cache verbleiben.
* Erwärmen Sie den Cache, der die beliebtesten oder wichtigsten Speicherseiten im Voraus aufruft, sodass der Cache für sie generiert und gespeichert wird. Dieser Vorgang kann mit jedem Internet-Crawler oder manuell durchgeführt werden, wenn Sie einen kleinen Speicher haben.
