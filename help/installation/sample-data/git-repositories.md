---
title: Klonen von Beispieldaten zu Git-Repositorys
description: Führen Sie diese Schritte aus, um Adobe Commerce-Beispieldaten zu installieren, indem Sie Git-Repositorys klonen.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# Klonen von Beispieldaten zu Git-Repositorys

In diesem Abschnitt wird beschrieben, wie Sie Beispieldaten klonen und hinzufügen, wenn Sie das Magento Open Source GitHub-Repository geklont haben. Diese Methode ist nur für beitragende Entwickler vorgesehen (d. h. für Entwickler, die Beiträge zur Magento Open Source-Code-Basis leisten möchten).

Wenn Sie kein beitragender Entwickler sind, wählen Sie eine der anderen Optionen, die im Inhaltsverzeichnis links auf der Seite angezeigt werden.

Mitwirkende Entwickler können diese Methode zum Installieren von Beispieldaten verwenden *nur* wenn Folgendes zutrifft:

* Sie verwenden Magento Open Source
* Sie [das GitHub-Repository geklont](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Sie können Beispieldaten entweder mit der `develop` Verzweigung (aktueller) oder mit einer freigegebenen Verzweigung (z. B. `2.4` (stabiler)) verwenden. Es wird empfohlen, eine freigegebene Verzweigung zu verwenden, da sie stabiler ist. Wenn Sie Code zum Repository beitragen und den neuesten Code benötigen, verwenden Sie die `develop`. Unabhängig von der ausgewählten Verzweigung müssen Sie [&#x200B; entsprechende Verzweigung &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) Magento Open Source GitHub-Repositorys klonen. Beispielsweise können Beispieldaten für die `develop` Verzweigung (nur *)* der Magento Open Source-`develop` verwendet werden.

## Klonen Sie das Beispieldaten-Repository.

In diesem Abschnitt wird beschrieben, wie Sie Beispieldaten installieren, indem Sie das Beispieldaten-Repository klonen. Sie können das Beispieldaten-Repository auf eine der folgenden Arten klonen:

* Klonen mit dem [SSH-Protokoll](#clone-with-ssh)
* Klonen mit dem [HTTPS-Protokoll](#clone-with-https)

### Klonen mit SSH

So klonen Sie das GitHub-Repository der Beispieldaten mit dem SSH-Protokoll:

1. Navigieren Sie in einem Webbrowser zum [Beispieldaten-Repository](https://github.com/magento/magento2-sample-data).
1. Klicken Sie neben dem Namen der Verzweigung in der Liste auf **SSH**.
1. Klicken Sie auf **In Zwischenablage kopieren**

   Die folgende Abbildung zeigt ein Beispiel.

   ![Klonen Sie das GitHub-Repository mit SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Ändern Sie in das Stammverzeichnis Ihres Webservers.

   Normalerweise ist es für Ubuntu `/var/www` und für CentOS `/var/www/html`.

1. Geben Sie `git clone` ein und fügen Sie den zuvor erhaltenen Wert ein.

   Es folgt ein Beispiel:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Warten Sie, bis das Repository auf Ihrem Server geklont wurde.

   >[!NOTE]
   >
   >Wenn der folgende Fehler angezeigt wird, stellen Sie sicher[&#x200B; dass Sie „Ihren SSH-Schlüssel &#x200B;](https://docs.github.com/articles/generating-ssh-keys/) GitHub freigegeben haben:<br>

   ```
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Checken Sie die Verzweigung des Beispieldaten-Repositorys aus, die der Verzweigung entspricht, die Sie aus dem `magento2`-Repository verwendet haben.

   Beispiel:

   Wenn Sie die `2.4-develop` Verzweigung des Magento Open Source GitHub-Repositorys verwendet haben, sollte die Beispieldatenverzweigung `2.4-develop` werden.

   Um die richtige Verzweigung auszuchecken, führen Sie den folgenden Befehl aus dem Stammverzeichnis des Beispieldaten-Repositorys aus (vorausgesetzt, Sie benötigen die `2.4-develop` Verzweigung):

   ```bash
   git checkout 2.4-develop
   ```

1. Ändern Sie in `<app_root>`.
1. Geben Sie den folgenden Befehl ein, um symbolische Verknüpfungen zwischen den Dateien zu erstellen, die Sie geklont haben, damit die Beispieldaten ordnungsgemäß funktionieren:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Warten Sie, bis der Befehl abgeschlossen ist.

1. Siehe [Festlegen von Dateisystemberechtigungen und Eigentümerschaft](#set-file-system-ownership-and-permissions).

1. Führen Sie den folgenden Befehl aus:

   ```bash
   bin/magento setup:upgrade
   ```

### Klonen mit HTTPS

So klonen Sie das GitHub-Repository der Beispieldaten mit dem HTTPS-Protokoll:

1. Navigieren Sie in einem Webbrowser zum [Beispieldaten-Repository](https://github.com/magento/magento2-sample-data).
1. Klicken Sie rechts auf der Seite unter dem Feld **URL klonen** auf **HTTPS**.
1. Klicken Sie **In Zwischenablage kopieren**.

   Die folgende Abbildung zeigt ein Beispiel.

   ![Klonen Sie das GitHub-Repository mit HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Ändern Sie in das Stammverzeichnis Ihres Webservers.

   Normalerweise ist es für Ubuntu `/var/www` und für CentOS `/var/www/html`.

1. Geben Sie `git clone` ein und fügen Sie den zuvor erhaltenen Wert ein.

   Es folgt ein Beispiel:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Warten Sie, bis das Repository auf Ihrem Server geklont wurde.
1. Checken Sie die Verzweigung des Beispieldaten-Repositorys aus, die der Verzweigung entspricht, die Sie aus dem `magento2`-Repository verwendet haben.

   Beispiel:

   Wenn Sie die `2.4-develop` Verzweigung des Magento Open Source GitHub-Repositorys verwendet haben, sollte die Beispieldatenverzweigung `2.4-develop` werden.

   Um die richtige Verzweigung auszuchecken, führen Sie den folgenden Befehl aus dem Stammverzeichnis des Beispieldaten-Repositorys aus (vorausgesetzt, Sie benötigen die `2.4-develop` Verzweigung):

   ```bash
   git checkout 2.4-develop
   ```

1. Ändern Sie in `<magento_root>`.
1. Geben Sie den folgenden Befehl ein, um symbolische Verknüpfungen zwischen den Dateien zu erstellen, die Sie geklont haben, damit die Beispieldaten ordnungsgemäß funktionieren:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   Beispiel:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. Warten Sie, bis der Befehl abgeschlossen ist.
1. Siehe nächster Abschnitt.

>[!WARNING]
>
>Adobe Commerce Wenn Sie Beispieldaten installieren (*), müssen* auch den folgenden Befehl ausführen, um die Datenbank und das Schema zu aktualisieren:
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## Festlegen von Dateisystemeigentum und -berechtigungen

Da das `php build-sample-data.php`-Skript Symlinks zwischen dem Beispieldaten-Repository und Ihrem Magento Open Source-Repository erstellt, müssen Sie die Dateisystemberechtigungen und die Eigentümerschaft im Beispieldaten-Repository festlegen. Andernfalls tritt ein Fehler beim Zugriff auf die Storefront auf.

So legen Sie Dateisystemberechtigungen und die Eigentümerschaft für das Beispieldaten-Repository fest:

1. Wechseln Sie zu Ihrem Beispieldatenklonverzeichnis.
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

1. Statische Dateien löschen:

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## Abschließen der Beispieldateninstallation

{{$include /help/_includes/sample-data-complete.md}}

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
