---
title: Beispieldaten-Composer-Pakete herunterladen
description: Führen Sie diese Schritte aus, um mit dem PHP Package Manager von Composer Beispieldaten für Adobe Commerce und Magento Open Source zu installieren.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Beispieldaten-Composer-Pakete herunterladen

In diesem Abschnitt wird beschrieben, wie Sie Beispieldaten installieren, wenn Sie die Adobe Commerce- oder Magento Open Source-Software auf eine der folgenden Arten erhalten haben:

* Herunterladen eines komprimierten Archivs aus `https://magento.com/tech-resources/download`.

  Wenn Sie ein Archiv von GitHub heruntergeladen haben, funktioniert diese Methode nicht, da die `composer.json` enthält nicht die `repo.magento.com` URL.

* Verwendet `composer create-project`

Sie können diese Methode zum Abrufen von Beispieldaten für Adobe Commerce und Magento Open Source verwenden, müssen jedoch dieselbe Methode verwenden [Authentifizierungsschlüssel](../prerequisites/authentication-keys.md) die Sie zum Installieren des Programms verwendet haben.

>[!NOTE]
>
>Wenn Fehler auftreten, z. B. `Could not find package...` oder `...no matching package found...`, stellen Sie sicher, dass Ihr Befehl keine Tippfehler enthält. Wenn weiterhin Fehler auftreten, haben Sie möglicherweise keinen Zugriff auf die richtigen Composer-Repositorys, insbesondere wenn Sie Adobe Commerce verwenden. Kontakt [Adobe Commerce-Support](https://support.magento.com/hc/en-us) für Hilfe.

Sie können Composer verwenden, um Beispieldaten entweder vor oder nach der Installation der Anwendung zu installieren. Es kann jedoch vorkommen, dass [zusätzliche Aufgaben](remove-or-update.md).

Wenn Sie ein Entwickler sind, lesen Sie [Installation durch Klonen von Repositorys](git-repositories.md).

>[!WARNING]
>
>Installieren Sie keine Beispieldaten, wenn Ihre Anwendung für [Produktionsmodus](../../configuration/bootstrap/application-modes.md#production-mode). Wechseln zu [Entwicklermodus](../../configuration/bootstrap/application-modes.md#developer-mode) zuerst. Beispieldaten im Produktionsmodus installieren [Fehler](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Um Beispieldaten mithilfe der Befehlszeile zu installieren, geben Sie den folgenden Befehl als Dateisysteminhaber in das `<app_root>` directory:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Wenn Sie Beispieldaten installieren _after_ Installieren der Anwendung müssen Sie auch den folgenden Befehl ausführen, um die Datenbank und das Schema im `<app_root>` directory:

```bash
bin/magento setup:upgrade
```

Sie müssen [authentifizieren](../prerequisites/authentication-keys.md) , um die Aktion abzuschließen.

## Authentifizierungsfehler

Möglicherweise wird der folgende Authentifizierungsfehler angezeigt:

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Wenn der Fehler angezeigt wird, wechseln Sie zum Installationsordner der Anwendung und führen Sie `composer update`, der Sie zur Eingabe Ihrer [Authentifizierungsschlüssel](../prerequisites/authentication-keys.md).

## Beispieldateninstallation abschließen

{{$include /help/_includes/sample-data-complete.md}}
