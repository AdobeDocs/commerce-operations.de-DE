---
title: Konfigurieren des Stores
description: Führen Sie diese Schritte aus, um Ihren Adobe Commerce Store zu konfigurieren.
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Konfigurieren des Stores

Bevor Sie diesen Befehl ausführen, müssen Sie die folgenden *oder* ausführen, die Anwendung [installieren](../advanced.md):

* [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md)
* [Datenbankschema erstellen](database.md)

## Sichere Installation

{{$include /help/_includes/secure-install.md}}

## Konfigurieren des Stores

Befehlsverwendung:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

Wobei die folgende Tabelle Parameter und Werte definiert:

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--base-url` | Basis-URL für den Zugriff auf Ihren Admin und Ihre Storefront in einem der folgenden Formate:<br><br> - `http[s]://<host or ip>/<your install dir>/`.<br><br>**Hinweis:** Das Schema (`http://` oder `https://`) und ein Schrägstrich sind beide erforderlich. `<your install dir>` ist der docroot-relative Pfad, in dem die Anwendung installiert werden soll. Je nachdem, wie Sie Ihren Webserver und virtuelle Hosts einrichten, kann der Pfad magento2 sein oder leer sein.<br><br>Um auf die Anwendung auf localhost zuzugreifen, können Sie `http://127.0.0.1/<your install dir>/` verwenden.<br><br> - `{{base_url}}` , was eine Basis-URL darstellt, die von einer virtuellen Host-Einstellung oder einer Virtualisierungsumgebung wie Docker definiert wird. Wenn Sie beispielsweise einen virtuellen Host mit dem Hostnamen commerce.example.com einrichten, können Sie die Anwendung mit `--base-url={{base_url}}` installieren und mit einer URL wie `http://commerce.example.com/admin` auf den Admin zugreifen. | Nein |
| `--language` | Sprachcode für die Verwendung in Admin und Storefront.<br><br>(Wenn Sie dies noch nicht getan haben, können Sie die Liste der Sprachcodes anzeigen, indem Sie `magento info:language:list` aus dem Verzeichnis `bin` eingeben.) | Nein |
| `--currency` | Standardwährung für die Verwendung in der Storefront. <br><br>(Wenn Sie dies noch nicht getan haben, können Sie die Liste der Währungen durch Eingabe von `magento info:currency:list` aus dem Verzeichnis `bin` anzeigen.) | Nein |
| `--timezone` | Standardzeitzone zur Verwendung in der Admin- und Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Zeitzonen anzeigen, indem Sie `magento info:timezone:list` aus dem Verzeichnis `bin` eingeben.) | Nein |
| `--use-rewrites` | `1` bedeutet, dass Sie Webserver-Neuschreibungen für generierte Links in der Storefront und in Admin verwenden.<br><br>`0` deaktiviert die Verwendung von Webserver-Neuschreibungen. Dies ist die Standardeinstellung. | Nein |
| `--use-secure` | `1` ermöglicht die Verwendung von Secure Sockets Layer (SSL) in Storefront-URLs. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` deaktiviert die Verwendung von SSL. In diesem Fall wird angenommen, dass alle anderen sicheren URL-Optionen ebenfalls 0 sind. Dies ist die Standardeinstellung. | Nein |
| `--base-url-secure` | Sichere Basis-URL für den Zugriff auf Ihren Admin und Ihre Storefront im folgenden Format: `http[s]://<host or ip>/<your install dir>/` | Nein |
| `--use-secure-admin` | `1` bedeutet, dass Sie SSL verwenden, um auf den Admin zuzugreifen. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` bedeutet, dass Sie SSL nicht mit dem Administrator verwenden. Dies ist die Standardeinstellung. | Nein |
| `--admin-use-security-key` | `1` bewirkt, dass die Anwendung einen zufällig generierten Schlüsselwert verwendet, um auf Seiten in Admin und in Formularen zuzugreifen. Diese Schlüsselwerte helfen dabei, siteübergreifende Skriptfälschungsangriffe zu verhindern. Dies ist die Standardeinstellung.<br/><br/>`0` deaktiviert die Verwendung des Schlüssels. | Nein |
| `--magento-init-params` | Fügen Sie zu jedem Befehl hinzu, um die Initialisierungsparameter der Anwendung anzupassen<br/><br/>Beispiel: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nein |
