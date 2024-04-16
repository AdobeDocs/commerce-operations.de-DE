---
title: Beispieldaten-Git-Repositorys klonen
description: Führen Sie diese Schritte aus, um Adobe Commerce-Beispieldaten durch Klonen von Git-Repositorys zu installieren.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '737'
ht-degree: 0%

---

# Beispieldaten-Git-Repositorys klonen

In diesem Thema wird erläutert, wie Sie beim Klonen des Magento Open Source-GitHub-Repositorys Beispieldaten hinzufügen und hinzufügen können. Diese Methode ist nur für beitragende Entwickler gedacht (d. h. Entwickler, die planen, zur Magento Open Source-Codebase beizutragen).

Wenn Sie kein Entwickler sind, wählen Sie eine der anderen Optionen, die im Inhaltsverzeichnis auf der linken Seite der Seite angezeigt werden.

Beitragende Entwickler können diese Methode der Installation von Beispieldaten verwenden *only* wenn Folgendes wahr ist:

* Sie verwenden Magento Open Source
* You [GitHub-Repository geklont](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Sie können Beispieldaten mit der `develop` Verzweigung (aktueller) oder freigegebene Verzweigung (z. B. `2.4` (stabiler)). Es wird empfohlen, eine veröffentlichte Verzweigung zu verwenden, da sie stabiler ist. Wenn Sie Code zum Repository beitragen und den neuesten Code benötigen, verwenden Sie die `develop` -Verzweigung. Unabhängig von der ausgewählten Verzweigung müssen Sie [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) die entsprechende Verzweigung des Magento Open Source-GitHub-Repositorys. Beispieldaten für die `develop` Zweig kann verwendet werden *only* mit der Magento Open Source `develop` -Verzweigung.

## Klonen Sie das Beispieldatenrepository

In diesem Abschnitt wird beschrieben, wie Sie Beispieldaten installieren, indem Sie das Beispieldaten-Repository klonen. Sie können das Beispieldaten-Repository auf eine der folgenden Arten klonen:

* Klonen mit der [SSH-Protokoll](#clone-with-ssh)
* Klonen mit der [HTTPS-Protokoll](#clone-with-https)

### Klonen mit SSH

So klonen Sie das GitHub-Beispielrepository mit dem SSH-Protokoll:

1. Navigieren Sie in einem Webbrowser zur [Beispieldatenrepository](https://github.com/magento/magento2-sample-data).
1. Klicken Sie neben dem Namen des Zweigs auf **SSH** aus der Liste.
1. Klicks **In Zwischenablage kopieren**

   Die folgende Abbildung zeigt ein Beispiel.

   ![GitHub-Repository mithilfe von SSH klonen](../../assets/installation/install_mage2_clone-ssh.png)

1. Wechseln Sie zum Basisverzeichnis Ihres Webservers.

   Normalerweise ist es für Ubuntu `/var/www` und für CentOS `/var/www/html`.

1. Eingabe `git clone` und fügen Sie den zuvor erhaltenen Wert ein.

   Ein Beispiel:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Warten Sie, bis das Repository auf Ihrem Server klon ist.

   >[!NOTE]
   >
   >Wenn der folgende Fehler angezeigt wird, stellen Sie sicher, dass Sie [SSH-Schlüssel freigegeben haben](https://docs.github.com/articles/generating-ssh-keys/) mit GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Stellen Sie sicher, dass Sie die Verzweigung des Beispiel-Daten-Repositorys auschecken, die der von Ihnen verwendeten Verzweigung entspricht. `magento2` Repository.

   Beispiel:

   Wenn Sie die `2.4-develop` Verzweigung des Magento Open Source GitHub-Repositorys, sollte die Verzweigung Beispieldaten `2.4-develop`.

   Um die richtige Verzweigung auszuchecken, führen Sie den folgenden Befehl aus dem Stammverzeichnis des Beispieldatenrepository aus (vorausgesetzt, Sie benötigen die `2.4-develop` Verzweigung):

   ```bash
   git checkout 2.4-develop
   ```

1. Ändern Sie `<app_root>`.
1. Geben Sie den folgenden Befehl ein, um symbolische Verknüpfungen zwischen den Dateien zu erstellen, die Sie geklont haben, damit die Beispieldaten ordnungsgemäß funktionieren:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Warten Sie, bis der Befehl abgeschlossen ist.

1. Siehe [Festlegen von Dateisystemberechtigungen und -berechtigungen](#set-file-system-ownership-and-permissions).

1. Führen Sie den folgenden Befehl aus:

   ```bash
   bin/magento setup:upgrade
   ```

### Klonen mit HTTPS

So klonen Sie das GitHub-Beispielrepository mit dem HTTPS-Protokoll:

1. Navigieren Sie in einem Webbrowser zur [Beispieldatenrepository](https://github.com/magento/magento2-sample-data).
1. Auf der rechten Seite der Seite, unter dem **Klon-URL** Feld, klicken Sie auf **HTTPS**.
1. Klicks **In Zwischenablage kopieren**.

   Die folgende Abbildung zeigt ein Beispiel.

   ![GitHub-Repository mithilfe von HTTPS klonen](../../assets/installation/install_mage2_clone-https.png)

1. Wechseln Sie zum Basisverzeichnis Ihres Webservers.

   Normalerweise ist es für Ubuntu `/var/www` und für CentOS `/var/www/html`.

1. Eingabe `git clone` und fügen Sie den zuvor erhaltenen Wert ein.

   Ein Beispiel:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Warten Sie, bis das Repository auf Ihrem Server klon ist.
1. Stellen Sie sicher, dass Sie die Verzweigung des Beispiel-Daten-Repositorys auschecken, die der von Ihnen verwendeten Verzweigung entspricht. `magento2` Repository.

   Beispiel:

   Wenn Sie die `2.4-develop` Verzweigung des Magento Open Source GitHub-Repositorys, sollte die Verzweigung Beispieldaten `2.4-develop`.

   Um die richtige Verzweigung auszuchecken, führen Sie den folgenden Befehl aus dem Stammverzeichnis des Beispieldatenrepository aus (vorausgesetzt, Sie benötigen die `2.4-develop` Verzweigung):

   ```bash
   git checkout 2.4-develop
   ```

1. Ändern Sie `<magento_root>`.
1. Geben Sie den folgenden Befehl ein, um symbolische Verknüpfungen zwischen den Dateien zu erstellen, die Sie geklont haben, damit die Beispieldaten ordnungsgemäß funktionieren:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   Beispiel:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. Warten Sie, bis der Befehl abgeschlossen ist.
1. Siehe nächsten Abschnitt.

>[!WARNING]
>
>Wenn Sie Beispieldaten installieren *after* Wenn Sie Adobe Commerce oder Magento Open Source installieren, müssen Sie auch den folgenden Befehl ausführen, um die Datenbank und das Schema zu aktualisieren:
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## Festlegen der Berechtigungen zum Dateisystem

Da die `php build-sample-data.php` -Skript erstellt Symlinks zwischen dem Beispiel-Daten-Repository und Ihrem Magento Open Source-Repository. Sie müssen Dateisystemberechtigungen und -eigentum im Beispiel-Daten-Repository festlegen. Andernfalls treten Fehler beim Zugriff auf die Storefront auf.

So legen Sie Dateisystemberechtigungen und -eigentum für das Beispiel-Daten-Repository fest:

1. Wechseln Sie zum Beispiel-Datenklonverzeichnis.
1. Legen Sie den Besitz fest:

   ```bash
   chown -R :<your web server group name> .
   ```

   Typische Beispiele:

   * CentOS: `chown -R :apache .`

   * Ubuntu: `chown -R :www-data .`

1. Berechtigungen festlegen:

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. Löschen Sie statische Dateien:

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## Beispieldateninstallation abschließen

{{$include /help/_includes/sample-data-complete.md}}
