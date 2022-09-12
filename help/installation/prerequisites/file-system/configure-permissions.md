---
title: Konfigurieren des Eigentums an Dateien und der Berechtigungen
description: Führen Sie diese Schritte aus, um Dateisystemberechtigungen für lokale Installationen von Adobe Commerce und Magento Open Source zu konfigurieren.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---


# Konfigurieren des Eigentums an Dateien und der Berechtigungen

In diesem Thema wird beschrieben, wie Sie Lese- und Schreibberechtigungen für die Webservergruppe festlegen, bevor Sie Adobe Commerce oder Magento Open Source installieren. Dies ist erforderlich, damit die Befehlszeile Dateien in das Dateisystem schreiben kann.

Je nachdem, ob Sie [freigegebenes Hosting](#set-permissions-for-one-user-on-shared-hosting) und einen Benutzer haben oder wenn Sie eine [privater Server](#set-ownership-and-permissions-for-two-users) und haben zwei Benutzer.

## Festlegen von Berechtigungen für einen Benutzer beim freigegebenen Hosting

In diesem Abschnitt wird beschrieben, wie Sie Berechtigungen vor der Installation festlegen, wenn Sie sich beim Anwendungsserver als derselbe Benutzer anmelden, der auch den Webserver ausführt. Diese Art der Einrichtung ist in freigegebenen Hosting-Umgebungen üblich.

So legen Sie Berechtigungen vor der Installation des Programms fest:

1. Melden Sie sich bei Ihrem Anwendungsserver an.
1. Verwenden Sie eine von Ihrem freigegebenen Hosting-Anbieter bereitgestellte Dateiverwaltungsanwendung, um zu überprüfen, ob Schreibberechtigungen für die folgenden Ordner festgelegt sind:

   * `vendor` (Installation des Composers oder komprimierten Archivs)
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

   Wenn Sie optional alle Befehle in einer Zeile eingeben möchten, geben Sie Folgendes ein, vorausgesetzt die Anwendung ist in `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Sofern noch nicht geschehen, erhalten Sie die Anwendung auf eine der folgenden Arten:

   * [Composer-Metapaket](../../composer.md)
   * [Repository klonen (nur beitragende Entwickler)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Nachdem Sie die Berechtigungen und Berechtigungen für das Dateisystem festgelegt haben, [Installieren des Programms](../../advanced.md)

>[!NOTE]
>
>Um die Berechtigungen nach der Installation des Programms weiter einzuschränken, können Sie [Umfrage konfigurieren](../../next-steps/set-umask.md).

## Festlegen von Eigentümern und Berechtigungen für zwei Benutzer

In diesem Abschnitt wird beschrieben, wie Sie Eigentümer und Berechtigungen für Ihren eigenen Server oder ein privates Hosting-Setup festlegen. Bei dieser Art von Einrichtung haben Sie normalerweise *cannot* als Webserver-Benutzer anmelden oder zu ihm wechseln. Normalerweise melden Sie sich als ein Benutzer an und führen den Webserver als einen anderen Benutzer aus.

So legen Sie die Eigentümerschaft und Berechtigungen für ein System mit zwei Benutzern fest:

Führen Sie die folgenden Aufgaben in der angegebenen Reihenfolge aus:

* [Über die freigegebene Gruppe](#about-the-shared-group)
* [Erstellen Sie den Dateisysteminhaber und geben Sie dem Benutzer ein sicheres Kennwort.](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Suchen Sie die Gruppe des Webserver-Benutzers.](#find-the-web-server-user-group)
* [Legen Sie den Dateisysteminhaber in die Webservergruppe](#put-the-file-system-owner-in-the-web-server-group)
* [Software abrufen](#get-the-software)
* [Festlegen von Eigentümern und Berechtigungen für die freigegebene Gruppe](#set-ownership-and-permissions-for-the-shared-group)

### Über die freigegebene Gruppe

Damit der Webserver Dateien und Ordner im Dateisystem schreiben kann, aber auch pflegen kann *Eigentum* durch den Dateisysteminhaber festgelegt ist, müssen sich beide Benutzer in derselben Gruppe befinden. Dies ist erforderlich, damit beide Benutzer den Zugriff auf Dateien (einschließlich Dateien, die mit Admin oder anderen webbasierten Dienstprogrammen erstellt wurden) freigeben können.

In diesem Abschnitt wird beschrieben, wie Sie einen Dateisysteminhaber erstellen und diesen Benutzer in die Gruppe des Webservers setzen. Sie können bei Bedarf ein vorhandenes Benutzerkonto verwenden. Wir empfehlen, dass der Benutzer aus Sicherheitsgründen über ein sicheres Kennwort verfügt.

>[!NOTE]
>
>Zu [Suchen Sie die Webserver-Benutzergruppe](#find-the-web-server-user-group) , wenn Sie ein bestehendes Benutzerkonto verwenden möchten.

### Erstellen Sie den Dateisysteminhaber und geben Sie dem Benutzer ein sicheres Kennwort.

In diesem Abschnitt wird beschrieben, wie Sie den Dateisysteminhaber erstellen. (Dateisysteminhaber ist ein anderer Begriff für *Befehlszeilenbenutzer*.

Um einen Benutzer unter CentOS oder Ubuntu zu erstellen, geben Sie den folgenden Befehl als Benutzer mit ein. `root` -Berechtigungen:

```bash
adduser <username>
```

Geben Sie den folgenden Befehl als Benutzer mit ein, um dem Benutzer ein Kennwort zu geben `root` -Berechtigungen:

```bash
passwd <username>
```

Befolgen Sie die Anweisungen auf Ihrem Bildschirm, um ein Kennwort für den Benutzer zu erstellen.

>[!WARNING]
>
>Wenn Sie `root` -Berechtigungen auf Ihrem Anwendungsserver verwenden, können Sie ein anderes lokales Benutzerkonto verwenden. Vergewissern Sie sich, dass der Benutzer über ein sicheres Kennwort verfügt, und fahren Sie mit dem [Legen Sie den Dateisysteminhaber in die Webservergruppe](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Um beispielsweise einen Benutzer mit dem Namen `magento_user` und geben Sie dem Benutzer ein Kennwort ein:

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Da der Zweck der Erstellung dieses Benutzers darin besteht, zusätzliche Sicherheit zu bieten, müssen Sie eine [sicheres Passwort](https://en.wikipedia.org/wiki/Password_strength).

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

In der Regel sind der Benutzer- und Gruppenname `apache`.

* Ubuntu: `ps aux | grep apache` um den Apache-Benutzer zu finden, und `groups <apache user>` um die Gruppe zu finden.

Normalerweise sind der Benutzername und der Gruppenname beide `www-data`.

### Legen Sie den Dateisysteminhaber in die Webservergruppe

Um den Dateisysteminhaber in die primäre Gruppe des Webservers aufzunehmen (ausgehend vom typischen Apache-Gruppennamen für CentOS und Ubuntu), geben Sie den folgenden Befehl als Benutzer mit ein. `root` -Berechtigungen:

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>Die `-a -G` -Optionen sind wichtig, da sie `apache` oder `www-data` as a *Sekundär* dem Benutzerkonto zugeordnet werden, wodurch die *primary* hinzugefügt. Das Hinzufügen einer sekundären Gruppe zu einem Benutzerkonto hilft dabei, [Beschränken des Eigentums an Dateien und der Berechtigungen](#set-ownership-and-permissions-for-two-users) , um sicherzustellen, dass Mitglieder einer gemeinsamen Gruppe nur Zugriff auf bestimmte Dateien haben.

So fügen Sie beispielsweise den Benutzer hinzu `magento_user` der `apache` primäre Gruppe unter CentOS:

```bash
sudo usermod -a -G apache magento_user
```

Geben Sie den folgenden Befehl ein, um zu bestätigen, dass Ihr Benutzer Mitglied der Webservergruppe ist:

```bash
groups magento_user
```

Das folgende Beispielergebnis zeigt die primäre Einstellung (`magento`) und sekundär (`apache`) Gruppen.

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

Wenn Sie dies noch nicht getan haben, können Sie die Software auf eine der folgenden Arten abrufen:

* [Composer-Metapaket](../../composer.md)
* [Repository klonen (nur beitragende Entwickler)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

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

Wenn Sie optional alle Befehle in einer Zeile eingeben möchten, geben Sie Folgendes ein, vorausgesetzt die Anwendung ist in `/var/www/html/magento2` und der Webserver-Gruppenname `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Wenn die Systemberechtigungen für die Ereignisdatei falsch festgelegt sind und vom Dateisysteminhaber nicht geändert werden können, können Sie den Befehl als Benutzer mit `root` -Berechtigungen:

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
