---
title: Laden Sie die [!DNL Upgrade Compatibility Tool]
description: Führen Sie die folgenden Schritte aus, um die [!DNL Upgrade Compatibility Tool] für Ihr Adobe Commerce-Projekt.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# Installieren Sie die [!DNL Upgrade Compatibility Tool]

{{commerce-only}

Die [!DNL Upgrade Compatibility Tool] ist ein Befehlszeilen-Tool, das eine benutzerdefinierte Adobe Commerce-Instanz anhand einer bestimmten Version prüft, indem alle darin installierten Module analysiert werden. Es wird eine Liste mit Fehlern und Warnungen zurückgegeben, die behoben werden müssen, bevor auf die neueste Version von Adobe Commerce aktualisiert wird.

## Voraussetzungen

So installieren Sie die [!DNL Upgrade Compatibility Tool], müssen Sie die erforderlichen Voraussetzungen installieren.

Siehe [Voraussetzungen](../upgrade-compatibility-tool/prerequisites.md) für weitere Informationen.

## Laden Sie die [!DNL Upgrade Compatibility Tool]

So laden Sie die [!DNL Upgrade Compatibility Tool], führen Sie den folgenden Befehl aus:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

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

Laden Sie die [!DNL Upgrade Compatibility Tool] Repository und Ausführung `composer install` in Ihrem Terminal, um Abhängigkeiten zu installieren.

>[!WARNING]
>
>Wenn die Variable **Adobe Commerce-Zugriffsschlüssel** nicht korrekt konfiguriert sind, können Sie die [!DNL Upgrade Compatibility Tool] und beim Ausführen von `composer create-project` -Befehl schlägt fehl.

### Node.js

Informationen zum Installieren von Node.js finden Sie unter Node.js . [Dokumentation](https://nodejs.dev/learn/how-to-install-nodejs).

## Drittanbietererweiterungen

Adobe empfiehlt, dass Sie sich an Ihren Erweiterungsanbieter wenden, um festzustellen, ob Ihre Erweiterung vollständig mit der neuesten veröffentlichten Adobe Commerce-Version kompatibel ist.

Siehe [Tool ausführen](../upgrade-compatibility-tool/run.md) Informationen zum Ausführen der [!DNL Upgrade Compatibility Tool].
