---
title: Installieren Sie die [!DNL Upgrade Compatibility Tool]
description: Führen Sie die folgenden Schritte aus, um die [!DNL Upgrade Compatibility Tool] für Ihr Adobe Commerce-Projekt.
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---


# Installieren Sie die [!DNL Upgrade Compatibility Tool]

Die [!DNL Upgrade Compatibility Tool] ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle darin installierten Module analysiert werden. Es wird eine Liste mit Fehlern und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird.

## Workflow

Das folgende Diagramm zeigt den erwarteten Workflow bei Ausführung des [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Abbildung](../../assets/upgrade-guide/mvp-diagram-v3.png)

## Wer ist der [!DNL Upgrade Compatibility Tool] für?

Im folgenden Anwendungsbeispiel wird der typische Prozess für einen Adobe Commerce-Partner zum Aktualisieren der Client-Instanz beschrieben:

1. Der Softwareingenieur eines Partners lädt die [!DNL Upgrade Compatibility Tool] aus dem [Adobe Commerce-Repository](https://repo.magento.com/) und führt es in der Betaphase der neuesten Adobe Commerce-Version aus. Siehe [Laden Sie die [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) für weitere Informationen.
1. Der Softwareingenieur generiert eine Vanilla-Instanz für die spezifische Version von Adobe Commerce, die derzeit installiert ist. Siehe [Mitarbeiter-Handbuch](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) Weitere Informationen zur Verwendung der `instance` -Befehl, um eine Vanilla-Installation zu generieren.
1. Der Softwareingenieur sieht, dass in den Inventar- und Katalogmodulen mehrere benutzerdefinierte Bereiche fehlerhaft sind und auch eine Komplexitätsbewertung von X erhalten. Siehe [Entwickler](../upgrade-compatibility-tool/developer.md) Anleitung für weitere Informationen zum Komplexitätswert.
1. Mit diesen Informationen kann der Softwareingenieur die Komplexität des Upgrades verstehen und diese Informationen an den Kundenbetreuer des Partners weiterleiten.
1. Der Kundenbetreuer erstellt einen Zeitplan und die Kosten für das Adobe Commerce-Upgrade, damit er die Genehmigung seines Managers erhalten kann.
1. Mit der Genehmigung ihres Managers arbeitet der Softwareingenieur an den erforderlichen Code-Änderungen, um die fehlerhaften Module zu beheben.
1. Der Softwareingenieur führt die [!DNL Upgrade Compatibility Tool] eine weitere Vorversion von Adobe Commerce verwenden, um sicherzustellen, dass keine neuen Probleme auftreten und dass ihre Codeänderungen die während der Beta-Phase gefundenen Probleme beheben.
1. Alles wird ausgecheckt und der Softwareingenieur sendet den Code in eine Staging-Umgebung, in der Regressionstests bestätigen, dass alle Tests grün sind. Dadurch können sie die neueste Adobe Commerce-Version am selben Tag, an dem die Adobe Commerce-Vorabversion veröffentlicht wird, in der Produktion freigeben.

   ![[!DNL Upgrade Compatibility Tool] audience](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Eine Vanilla-Instanz ist eine saubere Installation eines angegebenen Versions-Tags oder Zweigs für eine bestimmte Release-Version.

## Voraussetzungen

Siehe [Voraussetzungen](../upgrade-compatibility-tool/prerequisites.md) für weitere Informationen.

>[!NOTE]
>
>Sie können die [!DNL Upgrade Compatibility Tool] in allen Betriebssystemen. Es ist nicht erforderlich, die [!DNL Upgrade Compatibility Tool] wo sich Ihre Adobe Commerce-Instanz befindet. Es ist notwendig, [!DNL Upgrade Compatibility Tool] , um Zugriff auf den Quellcode der Adobe Commerce-Instanz zu erhalten. Beispielsweise können Sie das Tool auf einem Server installieren und es auf Ihre Adobe Commerce-Installation auf einem anderen Server verweisen.

Wenn Sie die [!DNL Upgrade Compatibility Tool] Bei einer Adobe Commerce-Instanz mit großen Modulen und Dateien erfordert das Tool möglicherweise eine hohe RAM-Menge von mindestens 2 GB RAM.

### Empfohlene Aktionen

Es wird empfohlen, zwei Module mit demselben Namen zu vermeiden. In diesem Fall wird die [!DNL Upgrade Compatibility Tool] zeigt einen Segmentierungsfehler an.

Um diesen Fehler zu vermeiden, wird empfohlen, die `bin` -Befehl mit der hinzugefügten Option `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>Die `<dir>` -Wert ist der Ordner, in dem sich Ihre Adobe Commerce-Instanz befindet.

Die `-m` -Option ermöglicht die [!DNL Upgrade Compatibility Tool] , um jedes spezifische Modul unabhängig zu analysieren, um zu vermeiden, dass in Ihrer Adobe Commerce-Instanz zwei Module mit demselben Namen auftreten.

Diese Befehlsoption ermöglicht auch die [!DNL Upgrade Compatibility Tool] um einen Ordner zu analysieren, der mehrere Module enthält:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Diese Empfehlung hilft auch bei Speicherproblemen, die beim Ausführen der [!DNL Upgrade Compatibility Tool].

## Laden Sie die [!DNL Upgrade Compatibility Tool]

So laden Sie die [!DNL Upgrade Compatibility Tool], führen Sie den folgenden Befehl aus:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Installieren

So installieren Sie die [!DNL Upgrade Compatibility Tool], müssen Sie die erforderlichen Voraussetzungen installieren:

* Adobe Commerce-Zugriffsschlüssel
* Verfasser
* Node.js

### Adobe Commerce-Zugriffsschlüssel

Sie müssen [Adobe Commerce-Zugriffsschlüssel](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) zum Herunterladen und Verwenden der [!DNL Upgrade Compatibility Tool]. Fügen Sie Ihre Adobe Commerce-Zugriffsschlüssel zu Ihren `auth.json` Datei, die sich unter `~/.composer` Standardmäßig.

>[!WARNING]
>
>Überprüfen Sie Ihre **COMPOSER_HOME** Umgebungsvariable, um zu sehen, wo die `auth.json` -Datei befindet.

Die **öffentlicher Schlüssel** entspricht _Benutzername_ in der Erwägung, dass **privater Schlüssel** ist die _password_:

### Beispiel für Adobe Commerce-Zugriffsschlüssel

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### Verfasser

Klonen Sie die [!DNL Upgrade Compatibility Tool] Repository und Ausführung `composer install` in Ihrem Terminal, um Abhängigkeiten zu installieren.

>[!WARNING]
>
>Wenn die Variable **Adobe Commerce-Zugriffsschlüssel** nicht korrekt konfiguriert sind, wird die [!DNL Upgrade Compatibility Tool] wird nicht installiert und Sie erhalten Fehler beim Ausführen von `composer install` Befehl.

### Node.js

Informationen zum Installieren von Node.js finden Sie unter Node.js . [Dokumentation](https://nodejs.dev/learn/how-to-install-nodejs).

## Drittanbietererweiterungen

Adobe empfiehlt, dass Sie sich an Ihren Erweiterungsanbieter wenden, um zu ermitteln, ob Ihre Erweiterung vollständig mit Adobe Commerce 2.4.x kompatibel ist.

Siehe [Tool ausführen](../upgrade-compatibility-tool/run.md) Informationen zum Ausführen der [!DNL Upgrade Compatibility Tool].
