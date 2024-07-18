---
title: Beispieldaten-Composer-Pakete herunterladen
description: Führen Sie diese Schritte aus, um Adobe Commerce-Beispieldaten mit dem Composer PHP Package Manager zu installieren.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Beispieldaten-Composer-Pakete herunterladen

In diesem Abschnitt wird beschrieben, wie Sie Beispieldaten installieren, wenn Sie die Adobe Commerce-Software auf eine der folgenden Arten erhalten haben:

* Laden Sie ein komprimiertes Archiv von `https://magento.com/tech-resources/download` herunter.

  Wenn Sie ein Archiv von GitHub heruntergeladen haben, funktioniert diese Methode nicht, da die `composer.json`-Datei nicht die `repo.magento.com`-URL enthält.

* Verwendet `composer create-project`

Sie können diese Methode zum Abrufen von Beispieldaten für Adobe Commerce verwenden. Sie müssen jedoch dieselben [Authentifizierungsschlüssel](../prerequisites/authentication-keys.md) verwenden, die Sie für die Installation des Programms verwendet haben.

>[!NOTE]
>
>Wenn Fehler wie `Could not find package...` oder `...no matching package found...` auftreten, stellen Sie sicher, dass Ihr Befehl keine Tippfehler enthält. Wenn weiterhin Fehler auftreten, haben Sie möglicherweise keinen Zugriff auf die richtigen Composer-Repositorys, insbesondere wenn Sie Adobe Commerce verwenden. Wenden Sie sich für Hilfe an den [Adobe Commerce-Support](https://support.magento.com/hc/en-us).

Sie können Composer verwenden, um Beispieldaten vor oder nach der Installation der Anwendung zu installieren. Es kann jedoch [zusätzliche Aufgaben](remove-or-update.md) geben.

Wenn Sie Entwickler sind, lesen Sie den Abschnitt [Installation durch Klonen von Repositorys](git-repositories.md).

>[!WARNING]
>
>Installieren Sie keine Beispieldaten, wenn Ihre Anwendung für den [Produktionsmodus](../../configuration/bootstrap/application-modes.md#production-mode) festgelegt ist. Wechseln Sie zuerst in den [Entwicklermodus](../../configuration/bootstrap/application-modes.md#developer-mode). Die Installation von Beispieldaten im Produktionsmodus [schlägt fehl](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Um Beispieldaten mithilfe der Befehlszeile zu installieren, geben Sie den folgenden Befehl als Dateisysteminhaber im Ordner &quot;`<app_root>`&quot;ein:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Wenn Sie Beispieldaten _nach der Installation des Programms_ installieren, müssen Sie auch den folgenden Befehl ausführen, um die Datenbank und das Schema im Verzeichnis `<app_root>` zu aktualisieren:

```bash
bin/magento setup:upgrade
```

Sie müssen [authentifizieren](../prerequisites/authentication-keys.md) , um die Aktion abzuschließen.

## Authentifizierungsfehler

Möglicherweise wird der folgende Authentifizierungsfehler angezeigt:

```
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Wenn der Fehler angezeigt wird, wechseln Sie zum Installationsverzeichnis der Anwendung und führen Sie `composer update` aus, um Sie zur Eingabe Ihrer [Authentifizierungsschlüssel](../prerequisites/authentication-keys.md) aufzufordern.

## Beispieldateninstallation abschließen

{{$include /help/_includes/sample-data-complete.md}}
