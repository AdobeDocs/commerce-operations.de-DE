---
title: "[!DNL Upgrade Compatibility Tool] Anforderungen"
description: Stellen Sie sicher, dass Ihr System die zum Ausführen der [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle für Ihr Adobe Commerce-Projekt.
source-git-commit: 653d755023f96c0a6acc312f74fd4a0292f13a73
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# Adobe Commerce-Zugriffsschlüssel

{{commerce-only}}

Sie müssen [Adobe Commerce-Zugriffsschlüssel](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) zum Herunterladen und Verwenden der [!DNL Upgrade Compatibility Tool]. Fügen Sie Ihre Adobe Commerce-Zugriffsschlüssel zu Ihren `auth.json` Datei, die sich unter `~/.composer` Standardmäßig.

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
| Node.js | Node.js-Versionen `^12.22.0`, `^14.17.0`oder `>=16.0.0` (siehe [Installieren von Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs/)) |
| Speicherbeschränkungen | Mindestens 2 GB RAM. |

[!DNL Upgrade Compatibility Tool] erfordert [PCNTL](https://www.php.net/manual/en/book.pcntl.php) und anderen PHP-Erweiterungen für die Ausführung. Überprüfen Sie die erforderlichen PHP-Erweiterungen mit `composer check-platform-reqs` command:

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

Adobe Commerce wird nur unter Linux-Betriebssystemen unterstützt. Sie können die [!DNL Upgrade Compatibility Tool] in einem Linux-Betriebssystem. Sie müssen die [!DNL Upgrade Compatibility Tool] wo sich Ihre Adobe Commerce-Instanz befindet.

Es ist notwendig, [!DNL Upgrade Compatibility Tool] , um Zugriff auf den Quellcode der Adobe Commerce-Instanz zu erhalten. Sie können es beispielsweise auf einem Server installieren und auf eine andere Adobe Commerce-Installation verweisen.

Wenn Sie die [!DNL Upgrade Compatibility Tool] Bei einer Adobe Commerce-Instanz mit großen Modulen und Dateien erfordert das Tool möglicherweise eine hohe RAM-Menge (mindestens 2 GB).

Führen Sie die [!DNL Upgrade Compatibility Tool] von [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) für [Adobe Commerce auf Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} Projekte.
