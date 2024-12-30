---
title: Konfigurieren von Dateieigentümerschaft und Berechtigungen
description: Führen Sie die folgenden Schritte aus, um Dateisystemberechtigungen für lokale Installationen von Adobe Commerce zu konfigurieren.
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# Konfigurieren von Dateieigentümerschaft und Berechtigungen

In diesem Abschnitt wird beschrieben, wie Sie vor der Installation von Adobe Commerce Lese- und Schreibberechtigungen für die Webservergruppe festlegen. Dies ist erforderlich, damit die Befehlszeile Dateien in das Dateisystem schreiben kann.

Die Vorgehensweise unterscheidet sich, je nachdem, ob Sie [freigegebenes Hosting](#set-permissions-for-one-user-on-shared-hosting) verwenden und einen Benutzer haben oder ob Sie einen [privaten Server](#set-ownership-and-permissions-for-two-users) und zwei Benutzer haben.

## Festlegen von Berechtigungen für einen Benutzer beim freigegebenen Hosting

In diesem Abschnitt wird beschrieben, wie Sie Berechtigungen vor der Installation festlegen, wenn Sie sich beim Anwendungsserver als derselbe Benutzer anmelden, der auch den Webserver ausführt. Diese Art der Einrichtung ist in freigegebenen Hosting-Umgebungen üblich.

So legen Sie Berechtigungen vor der Installation der Anwendung fest:

1. Melden Sie sich beim Anwendungs-Server an.
1. Verwenden Sie eine Datei-Manager-Anwendung, die von Ihrem freigegebenen Hosting-Anbieter bereitgestellt wird, um zu überprüfen, ob Schreibberechtigungen für die folgenden Ordner festgelegt sind:

   * `vendor` (Composer- oder komprimierte Archivinstallation)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * Alle anderen statischen Ressourcen

1. Wenn Sie Befehlszeilenzugriff haben, geben Sie die folgenden Befehle in der angegebenen Reihenfolge ein:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   Um optional alle Befehle in einer Zeile einzugeben, geben Sie Folgendes ein, vorausgesetzt, die Anwendung ist in `/var/www/html/magento2` installiert:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Wenn Sie dies noch nicht getan haben, rufen Sie die Anwendung auf eine der folgenden Arten ab:

   * [Composer-Metapaket](../../composer.md)
   * [Klonen Sie das Repository (nur beitragende Entwickler)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Nachdem Sie die Eigentümerschaft und Berechtigungen für das Dateisystem festgelegt haben, [ Sie die Anwendung](../../advanced.md)

>[!NOTE]
>
>Um die Berechtigungen nach der Installation der Anwendung weiter einzuschränken, können Sie [eine umask konfigurieren](../../next-steps/set-umask.md).

## Festlegen von Eigentümerschaft und Berechtigungen für zwei Benutzer

In diesem Abschnitt wird beschrieben, wie Sie den Besitz und die Berechtigungen für Ihren eigenen Server oder ein privates Hosting-Setup festlegen. Bei dieser Art von Setup können *sich normalerweise* Webserver-Benutzer anmelden oder zu diesem wechseln. Normalerweise melden Sie sich als ein Benutzer an und führen den Webserver als einen anderen Benutzer aus.

So legen Sie die Eigentümerschaft und Berechtigungen für ein System mit zwei Benutzern fest:

Führen Sie die folgenden Aufgaben in der angegebenen Reihenfolge aus:

* [Über die freigegebene Gruppe](#about-the-shared-group)
* [Erstellen Sie den Dateisystembesitzer und geben Sie dem Benutzer ein sicheres Kennwort](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Suchen der Benutzergruppe des Webservers](#find-the-web-server-user-group)
* [Legen Sie den Dateisystembesitzer in die Webservergruppe fest.](#put-the-file-system-owner-in-the-web-server-group)
* [Abrufen der Software](#get-the-software)
* [Festlegen von Eigentümerschaft und Berechtigungen für die freigegebene Gruppe](#set-ownership-and-permissions-for-the-shared-group)

### Über die freigegebene Gruppe

Damit der Webserver Dateien und Verzeichnisse im Dateisystem schreiben kann, aber auch *Eigentümer“ des Dateisystems* kann, müssen beide Benutzer derselben Gruppe angehören. Dies ist erforderlich, damit beide Benutzer gemeinsamen Zugriff auf Dateien haben (einschließlich Dateien, die mit dem Admin-Programm oder anderen webbasierten Dienstprogrammen erstellt wurden).

In diesem Abschnitt wird beschrieben, wie Sie einen Dateisystembesitzer erstellen und diesen Benutzer in die Gruppe des Webservers einfügen. Sie können bei Bedarf ein vorhandenes Benutzerkonto verwenden. Wir empfehlen, dass der Benutzer aus Sicherheitsgründen ein sicheres Kennwort hat.

>[!NOTE]
>
>Wechseln Sie zu [Webserver-Benutzergruppe suchen](#find-the-web-server-user-group), wenn Sie ein vorhandenes Benutzerkonto verwenden möchten.

### Erstellen Sie den Dateisystembesitzer und geben Sie dem Benutzer ein sicheres Kennwort

In diesem Abschnitt wird beschrieben, wie Sie den Dateisystembesitzer erstellen. (Besitzer des Dateisystems ist ein weiterer Begriff für *Befehlszeilenbenutzer*.)

Um einen Benutzer unter CentOS oder Ubuntu zu erstellen, geben Sie den folgenden Befehl als Benutzer mit `root` ein:

```bash
adduser <username>
```

Um dem Benutzer ein Kennwort zu geben, geben Sie den folgenden Befehl als Benutzer mit `root` ein:

```bash
passwd <username>
```

Befolgen Sie die Anweisungen auf Ihrem Bildschirm, um ein Kennwort für den Benutzer zu erstellen.

>[!WARNING]
>
>Wenn Sie auf Ihrem Anwendungsserver keine `root` Berechtigungen haben, können Sie ein anderes lokales Benutzerkonto verwenden. Stellen Sie sicher, dass der Benutzer über ein sicheres Kennwort verfügt, und setzen Sie den Vorgang mit [Legen Sie den Dateisystembesitzer in die Webserver-Gruppe ](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Um beispielsweise einen Benutzer mit dem Namen `magento_user` zu erstellen und ihm ein Kennwort zuzuweisen, geben Sie Folgendes ein:

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Da der Zweck der Erstellung dieses Benutzers darin besteht, zusätzliche Sicherheit zu bieten, stellen Sie sicher, dass Sie ein [starkes Kennwort“ ](https://en.wikipedia.org/wiki/Password_strength).

### Suchen der Webserver-Benutzergruppe

So suchen Sie die Gruppe der Webserver-Benutzenden:

* CentOS:

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  oder

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

In der Regel werden der Benutzer- und der Gruppenname beide `apache`.

* Ubuntu: `ps aux | grep apache` den Apache-Benutzer zu finden, dann `groups <apache user>` die Gruppe zu finden.

In der Regel sind sowohl der Benutzername als auch der Gruppenname `www-data`.

### Legen Sie den Dateisystembesitzer in die Webservergruppe fest.

Um den Dateisystembesitzer in die primäre Gruppe des Webservers einzuordnen (unter Annahme des typischen Apache-Gruppennamen für CentOS und Ubuntu), geben Sie den folgenden Befehl als Benutzer mit `root` Berechtigungen ein:

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>Die `-a -G` sind wichtig, da sie `apache` oder `www-data` als *sekundäre* Gruppe zum Benutzerkonto hinzufügen, wodurch die (primäre *Gruppe des* beibehalten wird. Wenn Sie einem Benutzerkonto eine sekundäre Gruppe hinzufügen, [ Sie (Dateieigentümerschaft und Berechtigungen ](#set-ownership-and-permissions-for-two-users)) sicherstellen, dass Mitglieder einer freigegebenen Gruppe nur Zugriff auf bestimmte Dateien haben.

So fügen Sie beispielsweise die `magento_user` der `apache` primären Gruppe unter CentOS hinzu:

```bash
sudo usermod -a -G apache magento_user
```

Um zu bestätigen, dass Ihr Benutzer Mitglied der Webserver-Gruppe ist, geben Sie den folgenden Befehl ein:

```bash
groups magento_user
```

Das folgende Beispielergebnis zeigt die primäre (`magento`) und sekundäre (`apache`) Gruppe des Benutzers.

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>Normalerweise sind der Benutzername und der Name der primären Gruppe identisch.

Um die Aufgabe abzuschließen, starten Sie den Webserver neu:

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### Abrufen der Software

Wenn Sie dies noch nicht getan haben, rufen Sie die Software auf eine der folgenden Arten ab:

* [Composer-Metapaket](../../composer.md)
* [Klonen Sie das Repository (nur beitragende Entwickler)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Festlegen von Eigentümerschaft und Berechtigungen für die freigegebene Gruppe

So legen Sie die Eigentümerschaft und Berechtigungen vor der Installation der Anwendung fest:

1. Melden Sie sich bei Ihrem Anwendungs-Server als Eigentümer des Dateisystems an oder wechseln Sie zu diesem.
1. Geben Sie die folgenden Befehle in der angegebenen Reihenfolge ein:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

Um optional alle Befehle in einer Zeile einzugeben, geben Sie Folgendes ein, vorausgesetzt, die Anwendung ist in `/var/www/html/magento2` installiert und der Name der Webserver-Gruppe ist `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Falls die Dateisystemberechtigungen nicht ordnungsgemäß festgelegt sind und vom Dateisystembesitzer nicht geändert werden können, können Sie den Befehl als Benutzer mit `root` Berechtigungen eingeben:

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## Wechseln zum Dateisystembesitzer

Nachdem Sie die anderen Aufgaben in diesem Thema ausgeführt haben, geben Sie einen der folgenden Befehle ein, um zu diesem Benutzer zu wechseln:

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

Beispiel:

```bash
su magento_user
```
