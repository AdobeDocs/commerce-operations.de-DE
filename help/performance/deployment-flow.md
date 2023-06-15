---
title: Bereitstellungsfluss
description: Erfahren Sie mehr über die erforderlichen Schritte für die Bereitstellung von Adobe Commerce oder Magento Open Source in einer Produktionsumgebung.
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Implementierungsfluss

Die [!DNL Commerce] Der Produktionsbereitstellungsfluss hilft einem Store, maximale Leistung zu erzielen.

## Installieren von Abhängigkeiten

Die `composer.json` und `composer.lock` Dateiverwaltung [!DNL Commerce] Abhängigkeiten erstellen und die entsprechende Version für jedes Paket installieren. Sie müssen die Abhängigkeiten vor [Anweisungen zur Vorverarbeitung der Abhängigkeitseinfügung](#preprocess-dependency-injection-instructions) wenn Sie die [Autoloader](#update-the-autoloader).

Installieren [!DNL Commerce] dependencies:

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

Bestätigen Sie nach Abschluss der Kompilierung Folgendes: [APCu ist aktiviert](../performance/software.md#php-settings) und aktualisieren Sie den Autoloader:

So aktualisieren Sie den Autoloader:

>[!INFO]
>
>Die `-o` -Option konvertiert PSR-0/4-Autoloading in Classmap, um einen schnelleren Autoloader zu erhalten. Die `--apcu` -Option verwendet APCu, um gefundene/nicht gefundene Klassen zwischenzuspeichern.

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

Bereitstellen von statischem Inhalt verursacht [!DNL Commerce] um die folgenden Aktionen durchzuführen:

* Alle statischen Ressourcen analysieren
* Zusammenführen, Minimieren und Bündeln von Inhalten
* Designdaten lesen und verarbeiten
* Fallback zum Thema analysieren
* Speichern Sie alle verarbeiteten und materialisierten Inhalte in einem bestimmten Ordner für die weitere Verwendung.

Wenn Ihr statischer Inhalt nicht bereitgestellt wird, [!DNL Commerce] führt alle aufgelisteten Vorgänge direkt durch, was zu einer erheblichen Verlängerung der Reaktionszeit führt.

Sie können verschiedene Optionen verwenden, um Bereitstellungsvorgänge basierend auf der Speichergröße und den Anforderungen an die Erfüllung anzupassen. Am häufigsten ist die kompakte Bereitstellungsstrategie. Siehe [Bereitstellungsstrategien für statische Dateien](../configuration/cli/static-view-file-strategy.md)

So stellen Sie statischen Inhalt bereit:

```bash
bin/magento setup:static-content:deploy
```

Mit diesem Befehl kann Composer die Zuordnung zu Projektdateien neu erstellen, damit sie schneller geladen werden.

## Produktionsmodus festlegen

>[!INFO]
>
>Wird der Modus automatisch auf die Produktion eingestellt, wird dies automatisch ausgeführt `setup:di:compile` und `setup:static-content:deploy`.

Schließlich müssen Sie Ihren Store im Produktionsmodus platzieren. Der Produktionsmodus ist speziell für die maximale Leistung Ihres Stores optimiert. Außerdem werden alle entwicklerspezifischen Funktionen deaktiviert. Dies kann in Ihrer `.htaccess` oder `nginx.conf` Datei:

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
