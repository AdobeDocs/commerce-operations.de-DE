---
title: '[!DNL Upgrade Compatibility Tool] requirements'
description: Vergewissern Sie sich, dass Ihr System die erforderlichen Anforderungen erfüllt, um den [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle für Ihr Adobe Commerce-Projekt auszuführen.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Adobe Commerce-Zugriffsschlüssel

{{commerce-only}}

Sie müssen über [Adobe Commerce-Zugriffsschlüssel](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) verfügen, um die [!DNL Upgrade Compatibility Tool] herunterzuladen und zu verwenden. Fügen Sie Ihre Adobe Commerce-Zugriffsschlüssel zu Ihrer `auth.json` -Datei hinzu, die sich standardmäßig unter `~/.composer` befindet.

>[!NOTE]
>
>Überprüfen Sie Ihre Umgebungsvariable **COMPOSER_HOME** , um zu sehen, wo sich die Datei `auth.json` befindet.

Der **öffentliche Schlüssel** entspricht dem _Benutzernamen_, während der **private Schlüssel** dem _Kennwort_ entspricht:

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
> Wenn Sie Ihre **Adobe Commerce-Zugriffsschlüssel** nicht richtig konfigurieren, können Sie den Befehl [!DNL Upgrade Compatibility Tool] nicht herunterladen. Der Befehl `composer create-project` schlägt dann fehl.

Führen Sie `composer install` in Ihrem Terminal aus, um Abhängigkeiten zu installieren.

## Systemanforderungen

Die Mindestanforderungen für die Verwendung von [!DNL Upgrade Compatibility Tool] in einer Befehlszeilenschnittstelle sind:

| **Anforderungen** | **Einschränkungen** |
|----------------|-----------------|
| PHP-Version | >= 7.3 |
| Verfasser | keine bekannten Anforderungen. |
| Node.js | Node.js-Versionen `^12.22.0`, `^14.17.0` oder `>=16.0.0` (siehe [Installieren von Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)) |
| Speicherbeschränkungen | Mindestens 2 GB RAM. |

[!DNL Upgrade Compatibility Tool] erfordert [PCNTL](https://www.php.net/manual/en/book.pcntl.php) und andere PHP-Erweiterungen für die Ausführung. Überprüfen Sie die erforderlichen PHP-Erweiterungen mit dem Befehl `composer check-platform-reqs` :

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

Adobe Commerce wird nur unter Linux-Betriebssystemen unterstützt. Sie können den [!DNL Upgrade Compatibility Tool] in einem Linux-Betriebssystem ausführen. Sie müssen nicht die [!DNL Upgrade Compatibility Tool] ausführen, in der sich Ihre Adobe Commerce-Instanz befindet.

Der [!DNL Upgrade Compatibility Tool] muss Zugriff auf den Quellcode der Adobe Commerce-Instanz haben. Sie können es beispielsweise auf einem Server installieren und auf eine andere Adobe Commerce-Installation verweisen.

Wenn Sie den [!DNL Upgrade Compatibility Tool] für eine Adobe Commerce-Instanz mit großen Modulen und Dateien ausführen, erfordert das Tool möglicherweise eine hohe RAM-Menge (mindestens 2 GB).

Führen Sie die [!DNL Upgrade Compatibility Tool] aus dem [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) für [Adobe Commerce in Cloud-Infrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} -Projekte aus.
