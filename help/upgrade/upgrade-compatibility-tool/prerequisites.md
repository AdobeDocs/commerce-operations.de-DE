---
title: '"[!DNL Upgrade Compatibility Tool] Anforderungen"'
description: 'Stellen Sie sicher, dass Ihr System die zum Ausführen der [!DNL Upgrade Compatibility Tool] für Ihr Adobe Commerce-Projekt. '
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# Systemanforderungen

{{commerce-only}

Die Mindestanforderungen für die Verwendung der [!DNL Upgrade Compatibility Tool] sind:

| **Voraussetzungen** | **Einschränkungen** |
|----------------|-----------------|
| PHP-Version | >= 7.3 |
| Verfasser | keine bekannte Anforderung |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`oder `>=16.0.0`) |
| Speicherbeschränkungen | Mindestens 2 GB RAM |

Sie können die [!DNL Upgrade Compatibility Tool] in verschiedenen Betriebssystemen (Windows wird nicht unterstützt). Sie müssen die [!DNL Upgrade Compatibility Tool] wo sich Ihre Adobe Commerce-Instanz befindet.

Es ist notwendig, [!DNL Upgrade Compatibility Tool] , um Zugriff auf den Quellcode der Adobe Commerce-Instanz zu erhalten. Sie können es beispielsweise auf einem Server installieren und auf eine andere Adobe Commerce-Installation verweisen.

Wenn Sie die [!DNL Upgrade Compatibility Tool] Bei einer Adobe Commerce-Instanz mit großen Modulen und Dateien erfordert das Tool möglicherweise eine hohe RAM-Menge (mindestens 2 GB).

## Adobe Commerce-Zugriffsschlüssel

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

## Verfasser

Laden Sie die [!DNL Upgrade Compatibility Tool] Repository und Ausführung `composer install` in Ihrem Terminal, um Abhängigkeiten zu installieren.

>[!NOTE]
>
> Wenn Sie Ihre **Adobe Commerce-Zugriffsschlüssel**, können Sie die [!DNL Upgrade Compatibility Tool]. Ausführen der `composer create-project` schlägt fehl.

## Node.js

Informationen zum Installieren von Node.js finden Sie unter Node.js . [Dokumentation](https://nodejs.dev/learn/how-to-install-nodejs).

## Drittanbietererweiterungen

Adobe empfiehlt Ihnen, sich an Ihren Erweiterungsanbieter zu wenden, um festzustellen, ob Ihre Erweiterung vollständig mit der neuesten Version von Adobe Commerce kompatibel ist.
