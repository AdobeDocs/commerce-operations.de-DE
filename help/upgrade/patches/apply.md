---
title: Anwenden von Patches
description: Erfahren Sie mehr über die Methoden zum Anwenden von Patches auf ein Adobe Commerce- oder Magento Open Source-Projekt.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Anwenden von Patches

Sie können Patches mit einer der folgenden Methoden anwenden:

- [Werkzeug für Qualitätsmuster](https://devdocs.magento.com/quality-patches/tool.html)
- [Befehlszeile](../patches/apply.md#command-line)
- [Verfasser](../patches/apply.md#composer)

## Verfasser

>[!IMPORTANT]
>
>Verwenden Sie die [Werkzeug für Qualitätsmuster](https://devdocs.magento.com/quality-patches/tool.html). Führen Sie immer umfassende Tests durch, bevor Sie einen benutzerdefinierten Patch bereitstellen.

So wenden Sie einen benutzerdefinierten Patch mit Composer an:

1. Öffnen Sie die Befehlszeilenanwendung und navigieren Sie zum Projektverzeichnis.
1. Fügen Sie die `cweagans/composer-patches` Plug-in in der `composer.json` -Datei.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Bearbeiten Sie die `composer.json` und fügen Sie den folgenden Abschnitt hinzu, um Folgendes anzugeben:
   - **Modul:** *\&quot;magento/module-payment\&quot;*
   - **Titel:** *\&quot;MAGETWO-56934: Die Checkout-Seite friert bei der Bestellung mit Authorize.net mit ungültiger Kreditkarte ein\&quot;*
   - **Pfad zum Patch:** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   Beispiel:

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   Wenn ein Patch mehrere Module betrifft, müssen Sie mehrere Patch-Dateien erstellen, die auf mehrere Module abzielen.

1. Wenden Sie den Patch an. Verwenden Sie die `-v` nur, wenn Sie Debugging-Informationen anzeigen möchten.

   ```bash
   composer -v install
   ```

1. Aktualisieren Sie die `composer.lock` -Datei. Die Sperrdatei verfolgt, welche Patches auf jedes Composer-Paket in einem Objekt angewendet wurden.

   ```bash
   composer update --lock
   ```

## Befehlszeile

So wenden Sie Patches über die Befehlszeile an:

1. Laden Sie die lokale Datei in die `<Magento_root>` -Verzeichnis auf dem Server mit FTP, SFTP, SSH oder Ihrer normalen Transportmethode.
1. Melden Sie sich beim Server als [Admin-Benutzer](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli.html#config-install-cli-first) und überprüfen Sie, ob sich die Datei im richtigen Verzeichnis befindet.
1. Führen Sie in der Befehlszeilenschnittstelle die folgenden Befehle entsprechend der Patch-Erweiterung aus:

   ```bash
   patch < patch_file_name.patch
   ```

   Der Befehl geht davon aus, dass sich die zu patchierende Datei relativ zur Patch-Datei befindet.

   >[!NOTE]
   >
   >Wenn die Befehlszeile Folgendes anzeigt: `File to patch:`, bedeutet dies, dass die gewünschte Datei nicht gefunden werden kann, selbst wenn der Pfad richtig erscheint. In dem im Befehlszeilen-Terminal angezeigten Feld zeigt die erste Zeile die zu patchierende Datei an. Kopieren Sie den Dateipfad und fügen Sie ihn in den `File to patch:` und drücken Sie `Enter` und das Pflaster fertig gestellt werden.

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > Tools > **Cacheverwaltung**.

   Alternativ kann der Patch lokal mit demselben Befehl angewendet, dann übernommen und normal gepusht werden.
