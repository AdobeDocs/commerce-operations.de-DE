---
title: Konfigurieren des Stores
description: Gehen Sie wie folgt vor, um Ihren Adobe Commerce Store zu konfigurieren.
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Konfigurieren des Stores

Bevor Sie diesen Befehl ausführen, müssen Sie Folgendes tun *oder* Sie müssen [die Anwendung installieren](../advanced.md):

* [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md)
* [Erstellen des Datenbankschemas](database.md)

## Sichere Installation

{{$include /help/_includes/secure-install.md}}

## Konfigurieren des Stores

Befehlsverwendung:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

Dabei definiert die folgende Tabelle Parameter und Werte:

| -Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--base-url` | Basis-URL für den Zugriff auf Ihre Admin- und Storefront in einem der folgenden Formate:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Hinweis:** Das Schema (`http://` oder `https://`) und ein Schrägstrich am Ende sind beide erforderlich. `<your install dir>` ist der docroot-relative Pfad, in dem die Anwendung installiert werden soll. Je nachdem, wie Sie Ihren Webserver und die virtuellen Hosts einrichten, kann der Pfad Magento2 oder leer sein.<br><br>Um auf die Anwendung auf localhost zuzugreifen, können Sie `http://127.0.0.1/<your install dir>/` verwenden.<br><br> - `{{base_url}}`, die eine Basis-URL darstellt, die durch eine Virtual-Host-Einstellung oder eine Virtualisierungsumgebung wie Docker definiert ist. Wenn Sie beispielsweise einen virtuellen Host mit dem Host-Namen commerce.example.com einrichten, können Sie die Anwendung mit `--base-url={{base_url}}` installieren und mit einer URL wie `http://commerce.example.com/admin` auf den Admin zugreifen. | Nein |
| `--language` | Sprach-Code, der in der Admin- und Storefront verwendet werden soll.<br><br>(Wenn Sie dies noch nicht getan haben, können Sie die Liste der Sprach-Codes anzeigen, indem Sie `magento info:language:list` aus dem `bin` eingeben.) | Nein |
| `--currency` | Standardwährung für die Storefront. <br><br>(Wenn Sie dies noch nicht getan haben, können Sie die Liste der Währungen anzeigen, indem Sie `magento info:currency:list` aus dem `bin` eingeben.) | Nein |
| `--timezone` | Standardmäßige Zeitzone für Admin und Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Zeitzonen anzeigen, indem Sie `magento info:timezone:list` aus dem `bin` eingeben.) | Nein |
| `--use-rewrites` | `1` bedeutet, dass Sie Webserver-Neuschreibungen für generierte Links in der Storefront und in Admin verwenden.<br><br>`0` Deaktiviert die Verwendung von Webserver-Neuschreibungen. Dies ist der Standardwert. | Nein |
| `--use-secure` | `1` ermöglicht die Verwendung von SSL (Secure Sockets Layer) in Storefront-URLs. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` deaktiviert die Verwendung von SSL. In diesem Fall wird davon ausgegangen, dass alle anderen sicheren URL-Optionen ebenfalls 0 sind. Dies ist der Standardwert. | Nein |
| `--base-url-secure` | Sichere Basis-URL für den Zugriff auf Admin und Storefront im folgenden Format: `http[s]://<host or ip>/<your install dir>/` | Nein |
| `--use-secure-admin` | `1` bedeutet, dass Sie SSL verwenden, um auf den Administrator zuzugreifen. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` bedeutet, dass Sie SSL nicht mit dem Administrator verwenden. Dies ist der Standardwert. | Nein |
| `--admin-use-security-key` | `1` verwendet die Anwendung einen zufällig generierten Schlüsselwert, um auf Seiten in Admin und in Formularen zuzugreifen. Diese Schlüsselwerte helfen, Angriffe durch Cross-Site-Script-Forgery zu verhindern. Dies ist der Standardwert.<br/><br/>`0` Deaktiviert die Verwendung des Schlüssels. | Nein |
| `--magento-init-params` | Fügen Sie zu einem beliebigen Befehl hinzu, um die Initialisierungsparameter der Anwendung anzupassen<br/><br/>Beispiel: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nein |

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
