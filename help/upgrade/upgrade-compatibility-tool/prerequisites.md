---
title: '"[!DNL Upgrade Compatibility Tool] Anforderungen"'
description: 'Stellen Sie sicher, dass Ihr System die zum Ausführen der [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle für Ihr Adobe Commerce-Projekt. '
source-git-commit: 7ec999f9122eb0707ac6c37b7b49f9c423945318
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Adobe Commerce-Zugriffsschlüssel

{{commerce-only}}

Sie müssen [Adobe Commerce-Zugriffsschlüssel](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) zum Herunterladen und Verwenden der [!DNL Upgrade Compatibility Tool]. Fügen Sie Ihre Adobe Commerce-Zugriffsschlüssel zu Ihren `auth.json` Datei, die sich unter `~/.composer` Standardmäßig.

>[!NOTE]
>
>Überprüfen Sie Ihre **COMPOSER_HOME** Umgebungsvariable, um zu sehen, wo die `auth.json` -Datei befindet.

Die **öffentlicher Schlüssel** entspricht _Benutzername_ in der Erwägung, dass **privater Schlüssel** ist die _password_:

## Beispiel für Adobe Commerce-Zugriffsschlüssel

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> Wenn Sie Ihre **Adobe Commerce-Zugriffsschlüssel**, können Sie die [!DNL Upgrade Compatibility Tool] und `composer create-project` schlägt fehl.

Ausführen `composer install` in Ihrem Terminal, um Abhängigkeiten zu installieren.

## Systemanforderungen

Die Mindestanforderungen für die Verwendung der [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle sind:

| **Voraussetzungen** | **Einschränkungen** |
|----------------|-----------------|
| PHP-Version | >= 7.3 |
| Verfasser | keine bekannten Anforderungen. |
| Node.js | Node.js-Versionen `^12.22.0`, `^14.17.0`oder `>=16.0.0` (siehe [Installieren von Node.js](https://nodejs.dev/learn/how-to-install-nodejs)) |
| Speicherbeschränkungen | Mindestens 2 GB RAM. |

Adobe Commerce wird nur unter Linux-Betriebssystemen unterstützt. Sie können die [!DNL Upgrade Compatibility Tool] in einem Linux-Betriebssystem. Sie müssen die [!DNL Upgrade Compatibility Tool] wo sich Ihre Adobe Commerce-Instanz befindet.

Es ist notwendig, [!DNL Upgrade Compatibility Tool] , um Zugriff auf den Quellcode der Adobe Commerce-Instanz zu erhalten. Sie können es beispielsweise auf einem Server installieren und auf eine andere Adobe Commerce-Installation verweisen.

Wenn Sie die [!DNL Upgrade Compatibility Tool] Bei einer Adobe Commerce-Instanz mit großen Modulen und Dateien erfordert das Tool möglicherweise eine hohe RAM-Menge (mindestens 2 GB).
