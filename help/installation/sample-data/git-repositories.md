---
title: Beispieldaten-Git-Repositorys klonen
description: Führen Sie diese Schritte aus, um Adobe Commerce-Beispieldaten durch Klonen von Git-Repositorys zu installieren.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# Beispieldaten-Git-Repositorys klonen

In diesem Thema wird erläutert, wie Sie beim Klonen des Magento Open Source-GitHub-Repositorys Beispieldaten hinzufügen und hinzufügen können. Diese Methode ist nur für beitragende Entwickler gedacht (d. h. Entwickler, die planen, zur Magento Open Source-Codebase beizutragen).

Wenn Sie kein Entwickler sind, wählen Sie eine der anderen Optionen, die im Inhaltsverzeichnis auf der linken Seite der Seite angezeigt werden.

Beitragende Entwickler können diese Methode verwenden, um Beispieldaten *nur* zu installieren, wenn Folgendes zutrifft:

* Sie verwenden Magento Open Source
* Sie [ haben das GitHub-Repository geklont](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Sie können Beispieldaten mit der Verzweigung `develop` (aktueller) oder einer veröffentlichten Verzweigung (z. B. `2.4` (stabiler) verwenden. Es wird empfohlen, eine veröffentlichte Verzweigung zu verwenden, da sie stabiler ist. Wenn Sie Code zum Repository beitragen und den neuesten Code benötigen, verwenden Sie die Verzweigung `develop` . Unabhängig von der ausgewählten Verzweigung müssen Sie die entsprechende Verzweigung des Magento Open Source-GitHub-Repositorys [klonen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/). Beispieldaten für den Zweig `develop` können beispielsweise *nur* mit dem Zweig Magento Open Source `develop` verwendet werden.

## Klonen Sie das Beispieldatenrepository

In diesem Abschnitt wird beschrieben, wie Sie Beispieldaten installieren, indem Sie das Beispieldaten-Repository klonen. Sie können das Beispieldaten-Repository auf eine der folgenden Arten klonen:

* Klonen mit dem [SSH-Protokoll](#clone-with-ssh)
* Klonen mit dem [HTTPS-Protokoll](#clone-with-https)

### Klonen mit SSH

So klonen Sie das GitHub-Beispielrepository mit dem SSH-Protokoll:

1. Wechseln Sie in einem Webbrowser zum [Beispieldaten-Repository](https://github.com/magento/magento2-sample-data).
1. Klicken Sie neben dem Namen des Zweigs in der Liste auf **SSH** .
1. Klicken Sie auf **In die Zwischenablage kopieren**

   Die folgende Abbildung zeigt ein Beispiel.

   ![Klonen Sie das GitHub-Repository mithilfe von SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Wechseln Sie zum Basisverzeichnis Ihres Webservers.

   Normalerweise ist es für Ubuntu `/var/www` und für CentOS `/var/www/html`.

1. Geben Sie `git clone` ein und fügen Sie den zuvor erhaltenen Wert ein.

   Ein Beispiel:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Warten Sie, bis das Repository auf Ihrem Server klon ist.

   >[!NOTE]
   >
   >Wenn der folgende Fehler angezeigt wird, stellen Sie sicher, dass Sie [Ihren SSH-Schlüssel freigegeben haben](https://docs.github.com/articles/generating-ssh-keys/), und GitHub:<br>

   ```
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Stellen Sie sicher, dass Sie die Verzweigung des Beispiel-Daten-Repositorys, die der von Ihnen verwendeten Verzweigung entspricht, aus dem Haupt-Repository `magento2` auschecken.

   Beispiel:

   Wenn Sie die Verzweigung `2.4-develop` des Magento Open Source-GitHub-Repositorys verwendet haben, sollte die Verzweigung &quot;Beispieldaten&quot;den Wert `2.4-develop` haben.

   Um die richtige Verzweigung auszuchecken, führen Sie den folgenden Befehl aus dem Stammverzeichnis des Beispieldatenrepository aus (vorausgesetzt, Sie benötigen die Verzweigung `2.4-develop` ):

   ```bash
   git checkout 2.4-develop
   ```

1. Ändern Sie in &quot;`<app_root>`&quot;.
1. Geben Sie den folgenden Befehl ein, um symbolische Verknüpfungen zwischen den Dateien zu erstellen, die Sie geklont haben, damit die Beispieldaten ordnungsgemäß funktionieren:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Warten Sie, bis der Befehl abgeschlossen ist.

1. Siehe [Festlegen von Dateisystemberechtigungen und -eigentum](#set-file-system-ownership-and-permissions).

1. Führen Sie den folgenden Befehl aus:

   ```bash
   bin/magento setup:upgrade
   ```

### Klonen mit HTTPS

So klonen Sie das GitHub-Beispielrepository mit dem HTTPS-Protokoll:

1. Wechseln Sie in einem Webbrowser zum [Beispieldaten-Repository](https://github.com/magento/magento2-sample-data).
1. Klicken Sie rechts auf der Seite unter dem Feld **URL klonen** auf **HTTPS**.
1. Klicken Sie auf **In die Zwischenablage kopieren**.

   Die folgende Abbildung zeigt ein Beispiel.

   ![Klonen Sie das GitHub-Repository mithilfe von HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Wechseln Sie zum Basisverzeichnis Ihres Webservers.

   Normalerweise ist es für Ubuntu `/var/www` und für CentOS `/var/www/html`.

1. Geben Sie `git clone` ein und fügen Sie den zuvor erhaltenen Wert ein.

   Ein Beispiel:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Warten Sie, bis das Repository auf Ihrem Server klon ist.
1. Stellen Sie sicher, dass Sie die Verzweigung des Beispiel-Daten-Repositorys, die der von Ihnen verwendeten Verzweigung entspricht, aus dem Haupt-Repository `magento2` auschecken.

   Beispiel:

   Wenn Sie die Verzweigung `2.4-develop` des Magento Open Source-GitHub-Repositorys verwendet haben, sollte die Verzweigung &quot;Beispieldaten&quot;den Wert `2.4-develop` haben.

   Um die richtige Verzweigung auszuchecken, führen Sie den folgenden Befehl aus dem Stammverzeichnis des Beispieldatenrepository aus (vorausgesetzt, Sie benötigen die Verzweigung `2.4-develop` ):

   ```bash
   git checkout 2.4-develop
   ```

1. Ändern Sie in &quot;`<magento_root>`&quot;.
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
>Wenn Sie die Beispieldaten *nach der Installation von Adobe Commerce* installieren, müssen Sie auch den folgenden Befehl ausführen, um die Datenbank und das Schema zu aktualisieren:
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## Festlegen der Berechtigungen zum Dateisystem

Da das `php build-sample-data.php` -Skript Symlinks zwischen dem Beispiel-Daten-Repository und Ihrem Magento Open Source-Repository erstellt, müssen Sie Dateisystemberechtigungen und -eigentum im Beispiel-Daten-Repository festlegen. Andernfalls treten Fehler beim Zugriff auf die Storefront auf.

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
