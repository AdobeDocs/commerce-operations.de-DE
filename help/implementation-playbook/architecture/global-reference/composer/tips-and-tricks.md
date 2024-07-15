---
title: Tipps und Tricks zum Verfasser
description: Erfahren Sie mehr über gängige Entwicklungsaufgaben für Composer und Anleitungen für die schnelle Lösung von Problemen.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Tipps und Tricks zum Verfasser

Bei der Entwicklung von Adobe Commerce-Modulen mit Composer treten möglicherweise Probleme auf. Diese Best Practices beschreiben einige gängige Aufgaben, die die Entwicklung erleichtern und Ihnen dabei helfen, Probleme schnell zu lösen.

>[!NOTE]
>
>Diese Richtlinien gelten hauptsächlich für [globale Referenzarchitektur (GRA)](../overview.md)-Projekte.

## Beschleunigen von Composer

Installieren Sie [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) , um den Composer mit asynchronen Paketdownloads zu beschleunigen.

```bash
composer global require hirak/prestissimo
```

Wenn Probleme auftreten, deinstallieren Sie `prestissimo`:

```bash
composer global remove hirak/prestissimo
```

## Beheben vager Versionsprobleme

Composer wird manchmal mit Paketversionen blockiert. Es können Meldungen zu inkompatiblen Versionen angezeigt werden, auch wenn sie nicht vorliegen. Versuchen Sie vor dem Debugging von Kompatibilitätsproblemen, den Composer zurückzusetzen:

1. Löschen Sie den Composer-Cache.

   ```bash
   composer clearcache
   ```

1. Entfernen Sie die Datei &quot;`composer.lock`&quot; für alle Pakete.

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Installieren Sie die Composer-Pakete neu.

   ```bash
   composer install
   ```

>[!TIP]
>
>Mit diesen Schritten werden alle Pakete auf die neueste verfügbare Version aktualisiert. Wiederherstellen der Datei &quot;`composer.lock`&quot; von Git, um diese Aktualisierungen rückgängig zu machen.

## Auf mögliche Aktualisierungen in Client-Paketen überprüfen

1. Finden Sie heraus, welche Pakete veraltet sein könnten.

   ```bash
   composer outdated
   ```

1. Filtern Sie nach Platzhaltern und/oder der Option `--minor-only` , um rückwärtsinkompatible Aktualisierungen zu überspringen:

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## Ermitteln Sie, ob ein Modul installiert ist.

Details zu allen installierten Paketen in einer Git-Verzweigung anzeigen.

```bash
composer info
```

Führen Sie `composer install` aus, nachdem Sie Git-Verzweigungen gewechselt haben und bevor Sie `composer info` ausführen. Andernfalls zeigt Composer Details zur vorherigen Verzweigung an, die Sie ausgecheckt haben.

>[!TIP]
>
>Verwenden Sie einen der folgenden Befehle, um zu filtern oder zu suchen.
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## Erfahren Sie, warum ein (spezifisches) Paket installiert ist

Manchmal installiert Composer die neueste verfügbare Version eines Pakets aufgrund einer strikten Abhängigkeit in einem anderen Paket.

Finden Sie heraus, ob es eine strikte Abhängigkeit in einem anderen Paket gibt.

```bash
composer why client/module-example
```

Wenn die Ergebnisse eine Liste von Metapacken oder ein anderes Paket anzeigen, das nicht explizit erforderlich ist, führen Sie den Befehl für dieses Paket aus:

```bash
composer why example/metapackage
```

## Erfahren Sie, warum ein Paket nicht installiert ist

Manchmal installiert der Composer kein Paket, weil es mit einem anderen Paket in Konflikt gerät, ein anderes Paket es ersetzt es, oder Sie haben nicht definiert, dass es sich um eine Abhängigkeit handelt.

Erfahren Sie, warum ein Paket nicht installiert ist.

```bash
composer why-not client/module-example
```

## Hosten eines privaten Composer-Repositorys

Wenn Sie ein privates Composer-Repository benötigen, verwenden Sie [Private Packagist](https://packagist.com/) oder [JFrog Artifactory](https://jfrog.com/integration/php-composer-repository/). Verwenden Sie nicht [satis](https://github.com/composer/satis).

- **Private Packagist** ist sicher, kostet etwa 600 USD pro Jahr bei drei Administratoren und wird gehostet.

- **JFrog Artifactory** beginnt bei 1.176 USD pro Jahr. Es wird nicht so häufig wie Packagist verwendet, aber es unterstützt mehr Sprachen als PHP.

- **Satis** verfügt über keine integrierte Sicherheit, keine Automatisierung und erfordert zusätzliches Hosting. Es ist nur kostenlos, wenn Ihre Zeit auch kostenlos ist.

## Versionspakete

Verwenden Sie [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html) , wie im Adobe Commerce [Versionierungsschema](https://developer.adobe.com/commerce/php/development/versioning/) beschrieben. Erfinden Sie das Rad nicht neu.

Folgen Sie für Adobe Commerce-Modulabhängigkeiten der Dokumentation [Modulversionsabhängigkeiten](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) .

Verwenden Sie nicht die Versionsdefinition in der Datei &quot;`composer.json`&quot;. Verwenden Sie stattdessen Git-Tags für Versionen. Siehe [Composer-Versionen und -Einschränkungen](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints).

## Wo platzieren Sie Module, die in eine Archivdatei und nicht über den Composer kommen?

Erstellen Sie ein Git-Repository für Module in einem Archiv und hosten Sie sie selbst. Jedes Adobe Commerce-Modul verfügt über eine `composer.json` -Datei. Nachdem Sie ihn in Git gehostet und mit Private Packagist synchronisiert haben, können Sie ihn mit Composer installieren.

Wenn Sie eine neue Version des Pakets erhalten, laden Sie den Code in Git hoch, taggen Sie ihn und installieren Sie die neue Version mit Composer.
