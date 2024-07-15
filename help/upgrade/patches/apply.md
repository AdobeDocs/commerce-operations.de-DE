---
title: Anwenden von Patches
description: Erfahren Sie mehr über die Methoden zum Anwenden von Patches auf ein Adobe Commerce-Projekt.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Anwenden von Patches

Sie können Patches mit einer der folgenden Methoden anwenden:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [Befehlszeile](../patches/apply.md#command-line)
- [Verfasser](../patches/apply.md#composer)


>[!TIP]
>
>Informationen zum zentralisierten Patchen für Adobe Commerce auf Unternehmensebene finden Sie unter [Best Practices](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) .

## Verfasser

>[!IMPORTANT]
>
>Um offizielle Qualitäts-Patches anzuwenden, verwenden Sie den [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Führen Sie immer umfassende Tests durch, bevor Sie einen benutzerdefinierten Patch bereitstellen.

So wenden Sie einen benutzerdefinierten Patch mit Composer an:

1. Öffnen Sie die Befehlszeilenanwendung und navigieren Sie zum Projektverzeichnis.
1. Fügen Sie das Plug-in `cweagans/composer-patches` zur Datei `composer.json` hinzu.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Bearbeiten Sie die Datei `composer.json` und fügen Sie den folgenden Abschnitt hinzu, um Folgendes anzugeben:
   - **Modul:** *\&quot;magento/module-payment\&quot;*
   - **Titel:** *\&quot;MAGETWO-56934: Checkout-Seite friert bei der Bestellung mit Authorize.net mit ungültiger Kreditkarte ein\&quot;*
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

1. Wenden Sie den Patch an. Verwenden Sie die Option `-v` nur, wenn Sie Debugging-Informationen anzeigen möchten.

   ```bash
   composer -v install
   ```

1. Aktualisieren Sie die Datei &quot;`composer.lock`&quot;. Die Sperrdatei verfolgt, welche Patches auf jedes Composer-Paket in einem Objekt angewendet wurden.

   ```bash
   composer update --lock
   ```

## Befehlszeile

So wenden Sie Patches über die Befehlszeile an:

1. Laden Sie die lokale Datei mithilfe von FTP, SFTP, SSH oder Ihrer normalen Übertragungsmethode in das Verzeichnis `<Magento_root>` auf dem Server hoch.
1. Melden Sie sich beim Server als [Admin-Benutzer](../../configuration/cli/config-cli.md#prerequisites) an und überprüfen Sie, ob sich die Datei im richtigen Verzeichnis befindet.
1. Führen Sie in der Befehlszeilenschnittstelle die folgenden Befehle entsprechend der Patch-Erweiterung aus:

   ```bash
   patch < patch_file_name.patch
   ```

   Der Befehl geht davon aus, dass sich die zu patchierende Datei relativ zur Patch-Datei befindet.

   >[!NOTE]
   >
   >Wenn die Befehlszeile &quot;`File to patch:`&quot; anzeigt, bedeutet dies, dass die gewünschte Datei nicht gefunden werden kann, selbst wenn der Pfad richtig erscheint. In dem im Befehlszeilen-Terminal angezeigten Feld zeigt die erste Zeile die zu patchierende Datei an. Kopieren Sie den Dateipfad, fügen Sie ihn in die Eingabeaufforderung `File to patch:` ein und drücken Sie auf `Enter` . Der Patch sollte abgeschlossen sein.

1. Damit die Änderungen übernommen werden, aktualisieren Sie den Cache im Admin unter **System** > Tools > **Cache-Verwaltung**.

   Alternativ kann der Patch lokal mit demselben Befehl angewendet, dann übernommen und normal gepusht werden.
