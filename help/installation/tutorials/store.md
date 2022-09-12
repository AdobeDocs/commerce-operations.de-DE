---
title: Konfigurieren des Stores
description: Führen Sie die folgenden Schritte aus, um Ihren Adobe Commerce- oder Magento Open Source-Store zu konfigurieren.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# Konfigurieren des Stores

Bevor Sie diesen Befehl ausführen, müssen Sie Folgendes tun: *oder* Sie müssen [Installieren des Programms](../advanced.md):

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
| `--base-url` | Basis-URL, die für den Zugriff auf Ihr Admin und Ihre Storefront in einem der folgenden Formate verwendet wird:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Hinweis:** Die Regelung (`http://` oder `https://`) und ein Schrägstrich erforderlich sind. `<your install dir>` ist der docroot-relative Pfad, in dem die Anwendung installiert werden soll. Je nachdem, wie Sie Ihren Webserver und virtuelle Hosts einrichten, kann der Pfad magento2 sein oder leer sein.<br><br>Um auf die Anwendung auf localhost zuzugreifen, können Sie `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` , die eine Basis-URL darstellt, die von einer virtuellen Host-Einstellung oder einer Virtualisierungsumgebung wie Docker definiert wird. Wenn Sie beispielsweise einen virtuellen Host mit dem Hostnamen commerce.example.com einrichten, können Sie die Anwendung mit `--base-url={{base_url}}` und greifen Sie mit einer URL wie auf den Administrator zu `http://commerce.example.com/admin`. | Nein |
| `--language` | Sprachcode für die Verwendung in Admin und Storefront.<br><br>(Wenn Sie dies noch nicht getan haben, können Sie die Liste der Sprachcodes durch Eingabe von `magento info:language:list` von `bin` directory.) | Nein |
| `--currency` | Standardwährung für die Verwendung in der Storefront. <br><br>(Wenn Sie dies noch nicht getan haben, können Sie die Liste der Währungen durch Eingabe von `magento info:currency:list` von `bin` directory.) | Nein |
| `--timezone` | Standardzeitzone zur Verwendung in der Admin- und Storefront. (Wenn Sie dies noch nicht getan haben, können Sie die Liste der Zeitzonen durch Eingabe von `magento info:timezone:list` von `bin` directory.) | Nein |
| `--use-rewrites` | `1` bedeutet, dass Sie Webserver-Neuschreibungen für generierte Links in der Storefront und in Admin verwenden.<br><br>`0` deaktiviert die Verwendung von Webserver-Neuschreibungen. Dies ist die Standardeinstellung. | Nein |
| `--use-secure` | `1` ermöglicht die Verwendung von Secure Sockets Layer (SSL) in Storefront-URLs. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` deaktiviert die Verwendung von SSL. In diesem Fall wird angenommen, dass alle anderen sicheren URL-Optionen ebenfalls 0 sind. Dies ist die Standardeinstellung. | Nein |
| `--base-url-secure` | Sichere Basis-URL für den Zugriff auf Ihre Admin- und Storefront im folgenden Format: `http[s]://<host or ip>/<your install dir>/` | Nein |
| `--use-secure-admin` | `1` bedeutet, dass Sie SSL verwenden, um auf den Admin zuzugreifen. Stellen Sie sicher, dass Ihr Webserver SSL unterstützt, bevor Sie diese Option auswählen.<br><br>`0` bedeutet, dass Sie SSL nicht mit dem Administrator verwenden. Dies ist die Standardeinstellung. | Nein |
| `--admin-use-security-key` | `1` bewirkt, dass die Anwendung einen zufällig generierten Schlüsselwert verwendet, um auf Seiten in Admin und in Formularen zuzugreifen. Diese Schlüsselwerte helfen dabei, siteübergreifende Skriptfälschungsangriffe zu verhindern. Dies ist die Standardeinstellung.<br/><br/>`0` deaktiviert die Verwendung des Schlüssels. | Nein |
| `--magento-init-params` | Zu jedem Befehl hinzufügen, um die Initialisierungsparameter der Anwendung anzupassen<br/><br/>Beispiel: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nein |
