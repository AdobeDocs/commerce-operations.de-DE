---
title: Herunterladen von Beispieldaten-Composer-Paketen
description: Führen Sie die folgenden Schritte aus, um Adobe Commerce-Beispieldaten mit dem PHP Package Manager von Composer zu installieren.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Herunterladen von Beispieldaten-Composer-Paketen

In diesem Abschnitt wird beschrieben, wie Sie Beispieldaten installieren, wenn Sie die Adobe Commerce-Software auf eine der folgenden Arten erhalten:

* Herunterladen eines komprimierten Archivs von `https://magento.com/tech-resources/download`.

  Wenn Sie ein Archiv von GitHub heruntergeladen haben, funktioniert diese Methode nicht, da die `composer.json`-Datei die `repo.magento.com` URL nicht enthält.

* `composer create-project` verwendet

Sie können diese Methode zum Abrufen von Beispieldaten für Adobe Commerce verwenden, müssen jedoch dieselben [Authentifizierungsschlüssel](../prerequisites/authentication-keys.md) verwenden, die Sie zum Installieren der Anwendung verwendet haben.

>[!NOTE]
>
>Wenn Fehler wie `Could not find package...` oder `...no matching package found...` auftreten, stellen Sie sicher, dass der Befehl keine Tippfehler enthält. Wenn weiterhin Fehler auftreten, haben Sie möglicherweise keinen Zugriff auf die richtigen Composer-Repositorys, insbesondere wenn Sie Adobe Commerce verwenden. Wenden Sie sich an den [Adobe Commerce](https://support.magento.com/hc/en-us)Support, um Hilfe zu erhalten.

Sie können Composer verwenden, um Beispieldaten entweder vor oder nach der Installation der Anwendung zu installieren. Es können jedoch [&#x200B; „zusätzliche Aufgaben“ &#x200B;](remove-or-update.md).

Wenn Sie selbst Entwickler sind, lesen Sie den Abschnitt [Installieren durch Klonen von Repositorys](git-repositories.md).

>[!WARNING]
>
>Installieren Sie keine Beispieldaten, wenn die Anwendung für den [Produktionsmodus“ &#x200B;](../../configuration/bootstrap/application-modes.md#production-mode) ist. Wechseln Sie zuerst [Entwicklermodus](../../configuration/bootstrap/application-modes.md#developer-mode). Die Installation der Beispieldaten im Produktionsmodus schlägt [fehl](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Um Beispieldaten über die Befehlszeile zu installieren, geben Sie den folgenden Befehl als Eigentümer des Dateisystems im `<app_root>` ein:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Wenn Sie Beispieldaten installieren (_), müssen_ auch den folgenden Befehl ausführen, um die Datenbank und das Schema im `<app_root>`-Verzeichnis zu aktualisieren:

```bash
bin/magento setup:upgrade
```

Sie müssen sich [authentifizieren](../prerequisites/authentication-keys.md) um die Aktion abzuschließen.

## Authentifizierungsfehler

Der folgende Authentifizierungsfehler wird möglicherweise angezeigt:

```
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Wenn der Fehler angezeigt wird, wechseln Sie zu Ihrem Anwendungsverzeichnis und führen Sie `composer update` aus, wodurch Sie zur Eingabe Ihrer [Authentifizierungsschlüssel“ &#x200B;](../prerequisites/authentication-keys.md).

## Abschließen der Beispieldateninstallation

{{$include /help/_includes/sample-data-complete.md}}

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
