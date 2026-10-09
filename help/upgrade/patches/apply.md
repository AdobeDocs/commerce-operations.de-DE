---
title: Patches anwenden
description: Erfahren Sie mehr über die Methoden zum Anwenden von Patches auf ein Adobe Commerce-Projekt.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '324'
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

   ```shell
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

   ```shell
   composer -v install
   ```

1. Aktualisieren Sie die `composer.lock`. Die Sperrdatei verfolgt, welche Patches auf jedes Composer-Paket in einem -Objekt angewendet wurden.

   ```shell
   composer update --lock
   ```

## Befehlszeile

So wenden Sie Patches über die Befehlszeile an:

1. Laden Sie die lokale Datei mithilfe von FTP, SFTP, SSH oder Ihrer normalen Transportmethode in das `<Magento_root>`-Verzeichnis auf den Server hoch.
1. Melden Sie sich beim Server als [Admin-Benutzer](../../configuration/cli/config-cli.md#prerequisites) an und stellen Sie sicher, dass sich die Datei im richtigen Verzeichnis befindet.
1. Führen Sie in der Befehlszeilenschnittstelle die folgenden Befehle gemäß der Patch-Erweiterung aus:

   ```shell
   patch < patch_file_name.patch
   ```

   Der Befehl setzt voraus, dass sich die zu patchende Datei relativ zur Patchdatei befindet.

   >[!NOTE]
   >
   >Wenn in der Befehlszeile Folgendes angezeigt wird: `File to patch:`, bedeutet dies, dass die gewünschte Datei nicht gefunden werden kann, auch wenn der Pfad korrekt erscheint. In dem Feld, das im Befehlszeilen-Terminal angezeigt wird, zeigt die erste Zeile die Datei an, die gepatcht werden soll. Kopieren Sie den Dateipfad, fügen Sie ihn in die `File to patch:` ein, und drücken Sie `Enter`. Der Patch sollte abgeschlossen sein.

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > Tools > **Cache-Verwaltung**.

   Alternativ kann der Patch lokal mit demselben Befehl angewendet werden, dann übertragen und normal gepusht.
