---
title: Konfigurieren von Dateieigentum und Berechtigungen
description: Führen Sie diese Schritte aus, um Dateisystemberechtigungen für lokale Installationen von Adobe Commerce zu konfigurieren.
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# Konfigurieren von Dateieigentum und Berechtigungen

In diesem Thema wird beschrieben, wie Sie Lese- und Schreibberechtigungen für die Webservergruppe festlegen, bevor Sie Adobe Commerce installieren. Dies ist erforderlich, damit die Befehlszeile Dateien in das Dateisystem schreiben kann.

Die Vorgehensweise, die Sie verwenden, ist unterschiedlich, je nachdem, ob Sie [freigegebenes Hosting](#set-permissions-for-one-user-on-shared-hosting) verwenden und einen Benutzer haben oder einen [privaten Server](#set-ownership-and-permissions-for-two-users) verwenden und über zwei Benutzer verfügen.

## Festlegen von Berechtigungen für einen Benutzer beim freigegebenen Hosting

In diesem Abschnitt wird beschrieben, wie Sie Berechtigungen vor der Installation festlegen, wenn Sie sich beim Anwendungsserver als derselbe Benutzer anmelden, der auch den Webserver ausführt. Diese Art der Einrichtung ist in freigegebenen Hosting-Umgebungen üblich.

So legen Sie Berechtigungen vor der Installation des Programms fest:

1. Melden Sie sich bei Ihrem Anwendungsserver an.
1. Verwenden Sie eine von Ihrem freigegebenen Hosting-Anbieter bereitgestellte Dateiverwaltungsanwendung, um zu überprüfen, ob Schreibberechtigungen für die folgenden Ordner festgelegt sind:

   * `vendor` (Composer- oder komprimierte Archivierungsinstallation)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * Alle anderen statischen Ressourcen

1. Wenn Sie Zugriff auf die Befehlszeile haben, geben Sie die folgenden Befehle in der angegebenen Reihenfolge ein:

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

   Wenn Sie optional alle Befehle in einer Zeile eingeben möchten, geben Sie Folgendes ein, vorausgesetzt die Anwendung ist in `/var/www/html/magento2` installiert:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Sofern noch nicht geschehen, erhalten Sie die Anwendung auf eine der folgenden Arten:

   * [Composer-Metapaket](../../composer.md)
   * [Klonen Sie das Repository (nur beitragende Entwickler)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Nachdem Sie die Eigentümerschaft und Berechtigungen des Dateisystems festgelegt haben, installieren Sie [die Anwendung](../../advanced.md)

>[!NOTE]
>
>Um die Berechtigungen nach der Installation des Programms weiter einzuschränken, können Sie [eine Umfrage konfigurieren](../../next-steps/set-umask.md).

## Festlegen von Eigentümern und Berechtigungen für zwei Benutzer

In diesem Abschnitt wird beschrieben, wie Sie Eigentümer und Berechtigungen für Ihren eigenen Server oder ein privates Hosting-Setup festlegen. Bei dieser Art von Einrichtung können Sie sich in der Regel *nicht als Webserver-Benutzer anmelden oder zu ihm wechseln.* Normalerweise melden Sie sich als ein Benutzer an und führen den Webserver als einen anderen Benutzer aus.

So legen Sie die Eigentümerschaft und Berechtigungen für ein System mit zwei Benutzern fest:

Führen Sie die folgenden Aufgaben in der angegebenen Reihenfolge aus:

* [Über die freigegebene Gruppe](#about-the-shared-group)
* [Erstellen Sie den Dateisysteminhaber und geben Sie dem Benutzer ein sicheres Kennwort.](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Suchen Sie die Gruppe des Webserver-Benutzers.](#find-the-web-server-user-group)
* [Legen Sie den Dateisysteminhaber in die Webservergruppe](#put-the-file-system-owner-in-the-web-server-group)
* [Software abrufen](#get-the-software)
* [Festlegen von Eigentümern und Berechtigungen für die freigegebene Gruppe](#set-ownership-and-permissions-for-the-shared-group)

### Über die freigegebene Gruppe

Damit der Webserver Dateien und Ordner im Dateisystem schreiben kann, aber auch *Eigentümer* des Dateisysteminhabers beibehalten kann, müssen sich beide Benutzer in derselben Gruppe befinden. Dies ist erforderlich, damit beide Benutzer den Zugriff auf Dateien (einschließlich Dateien, die mit Admin oder anderen webbasierten Dienstprogrammen erstellt wurden) freigeben können.

In diesem Abschnitt wird beschrieben, wie Sie einen Dateisysteminhaber erstellen und diesen Benutzer in die Gruppe des Webservers setzen. Sie können bei Bedarf ein bestehendes Benutzerkonto verwenden. Wir empfehlen dem Benutzer aus Sicherheitsgründen, über ein sicheres Kennwort zu verfügen.

>[!NOTE]
>
>Wechseln Sie zu &quot;[Suchen Sie die Webserver-Benutzergruppe](#find-the-web-server-user-group)&quot;, wenn Sie ein bestehendes Benutzerkonto verwenden möchten.

### Erstellen Sie den Dateisysteminhaber und geben Sie dem Benutzer ein sicheres Kennwort.

In diesem Abschnitt wird beschrieben, wie Sie den Dateisysteminhaber erstellen. (Dateisysteminhaber ist ein anderer Begriff für den *Befehlszeilenbenutzer*.)

Um einen Benutzer unter CentOS oder Ubuntu zu erstellen, geben Sie den folgenden Befehl als Benutzer mit `root` -Berechtigungen ein:

```bash
adduser <username>
```

Geben Sie den folgenden Befehl als Benutzer mit `root` -Berechtigungen ein, um dem Benutzer ein Kennwort zu geben:

```bash
passwd <username>
```

Befolgen Sie die Anweisungen auf Ihrem Bildschirm, um ein Kennwort für den Benutzer zu erstellen.

>[!WARNING]
>
>Wenn Sie auf Ihrem Anwendungsserver nicht über `root` -Berechtigungen verfügen, können Sie ein anderes lokales Benutzerkonto verwenden. Stellen Sie sicher, dass der Benutzer über ein sicheres Kennwort verfügt, und fahren Sie mit [Legen Sie den Dateisysteminhaber in die Webservergruppe](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Geben Sie beispielsweise Folgendes ein, um einen Benutzer mit dem Namen `magento_user` zu erstellen und dem Benutzer ein Kennwort zu geben:

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Da der Zweck der Erstellung dieses Benutzers darin besteht, zusätzliche Sicherheit zu bieten, müssen Sie ein [sicheres Kennwort](https://en.wikipedia.org/wiki/Password_strength) erstellen.

### Suchen Sie die Webserver-Benutzergruppe

So suchen Sie die Gruppe des Webserver-Benutzers:

* CentOS:

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  oder

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

In der Regel sind der Benutzer- und Gruppenname beide `apache`.

* Ubuntu: `ps aux | grep apache` , um den Apache-Benutzer zu finden, und `groups <apache user>`, um die Gruppe zu finden.

Normalerweise sind der Benutzername und der Gruppenname jeweils `www-data`.

### Legen Sie den Dateisysteminhaber in die Webservergruppe

Um den Dateisysteminhaber in die primäre Gruppe des Webservers einzubeziehen (vorausgesetzt, der typische Apache-Gruppenname für CentOS und Ubuntu wird verwendet), geben Sie den folgenden Befehl als Benutzer mit `root` -Berechtigungen ein:

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>Die `-a -G` -Optionen sind wichtig, da sie dem Benutzerkonto `apache` oder `www-data` als *sekundäre* Gruppe hinzufügen, wodurch die Gruppe *primary* des Benutzers erhalten bleibt. Durch das Hinzufügen einer sekundären Gruppe zu einem Benutzerkonto hilft [das Eigentum an Dateien und die Berechtigungen zu beschränken](#set-ownership-and-permissions-for-two-users), sicherzustellen, dass Mitglieder einer freigegebenen Gruppe nur Zugriff auf bestimmte Dateien haben.

Um beispielsweise den Benutzer `magento_user` zur primären Gruppe `apache` unter CentOS hinzuzufügen:

```bash
sudo usermod -a -G apache magento_user
```

Geben Sie den folgenden Befehl ein, um zu bestätigen, dass Ihr Benutzer Mitglied der Webservergruppe ist:

```bash
groups magento_user
```

Das folgende Beispielergebnis zeigt die primären (`magento`) und sekundären (`apache`) Gruppen des Benutzers.

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>Normalerweise sind Benutzername und primärer Gruppenname identisch.

Starten Sie den Webserver neu, um die Aufgabe abzuschließen:

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### Software abrufen

Wenn Sie dies noch nicht getan haben, rufen Sie die Software auf eine der folgenden Arten auf:

* [Composer-Metapaket](../../composer.md)
* [Klonen Sie das Repository (nur beitragende Entwickler)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Festlegen von Eigentümern und Berechtigungen für die freigegebene Gruppe

So legen Sie den Besitz und die Berechtigungen fest, bevor Sie die Anwendung installieren:

1. Melden Sie sich bei Ihrem Anwendungsserver als Dateisysteminhaber an oder wechseln Sie zu ihm.
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

Wenn Sie optional alle Befehle in einer Zeile eingeben möchten, geben Sie Folgendes ein (vorausgesetzt, die Anwendung ist in `/var/www/html/magento2` installiert und der Webserver-Gruppenname ist `apache`):

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Wenn die Systemberechtigungen für die Ereignisdatei falsch festgelegt sind und vom Dateisysteminhaber nicht geändert werden können, können Sie den Befehl als Benutzer mit `root` -Berechtigungen eingeben:

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## Wechseln Sie zum Dateisysteminhaber.

Nachdem Sie die anderen Aufgaben in diesem Thema ausgeführt haben, geben Sie einen der folgenden Befehle ein, um zu diesem Benutzer zu wechseln:

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

Beispiel:

```bash
su magento_user
```
