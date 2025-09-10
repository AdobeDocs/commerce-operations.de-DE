---
title: Patches anwenden
description: Erfahren Sie mehr über die Methoden zum Anwenden von Patches auf ein Adobe Commerce-Projekt.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: c8a20ad1b0b57724f389cfa5c63f6ae542758c2b
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Patches anwenden

Sie können Patches mit einer der folgenden Methoden anwenden:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [Befehlszeile](../patches/apply.md#command-line)
- [Komponist](../patches/apply.md#composer)


>[!TIP]
>
>Unter [Best Practices](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) finden Sie Informationen zum zentralisierten Patchen für Adobe Commerce im Unternehmensmaßstab.

## Komponist

{{custom-patches-disclaimer}}

So wenden Sie einen benutzerdefinierten Patch mit dem Composer an:

1. Öffnen Sie die Befehlszeilenanwendung und navigieren Sie zu Ihrem Projektverzeichnis.
1. Fügen Sie das `cweagans/composer-patches`-Plug-in zur `composer.json` hinzu.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Bearbeiten Sie die `composer.json` und fügen Sie den folgenden Abschnitt hinzu, um Folgendes anzugeben:
   - **Modul:** *\„magento/module-payment\&quot;*
   - **Titel:** *\„MAGETWO-56934: Die Checkout-Seite friert bei der Bestellung mit Authorize.net mit ungültiger Kreditkarte ein\&quot;*
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

1. Pflaster aufkleben. Verwenden Sie die Option `-v` nur, wenn Sie Debugging-Informationen anzeigen möchten.

   ```bash
   composer -v install
   ```

1. Aktualisieren Sie die `composer.lock`. Die Sperrdatei verfolgt, welche Patches auf jedes Composer-Paket in einem -Objekt angewendet wurden.

   ```bash
   composer update --lock
   ```

## Befehlszeile

So wenden Sie Patches über die Befehlszeile an:

1. Laden Sie die lokale Datei mithilfe von FTP, SFTP, SSH oder Ihrer normalen Transportmethode in das `<Magento_root>`-Verzeichnis auf den Server hoch.
1. Melden Sie sich beim Server als [Admin-Benutzer](../../configuration/cli/config-cli.md#prerequisites) an und stellen Sie sicher, dass sich die Datei im richtigen Verzeichnis befindet.
1. Führen Sie in der Befehlszeilenschnittstelle die folgenden Befehle gemäß der Patch-Erweiterung aus:

   ```bash
   patch < patch_file_name.patch
   ```

   Der Befehl setzt voraus, dass sich die zu patchende Datei relativ zur Patchdatei befindet.

   >[!NOTE]
   >
   >Wenn in der Befehlszeile Folgendes angezeigt wird: `File to patch:`, bedeutet dies, dass die gewünschte Datei nicht gefunden werden kann, auch wenn der Pfad korrekt erscheint. In dem Feld, das im Befehlszeilen-Terminal angezeigt wird, zeigt die erste Zeile die Datei an, die gepatcht werden soll. Kopieren Sie den Dateipfad, fügen Sie ihn in die `File to patch:` ein, und drücken Sie `Enter`. Der Patch sollte abgeschlossen sein.

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > Tools > **Cache-Verwaltung**.

   Alternativ kann der Patch lokal mit demselben Befehl angewendet werden, dann übertragen und normal gepusht.
