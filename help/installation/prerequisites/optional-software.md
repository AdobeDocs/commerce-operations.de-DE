---
title: Optionale Software
description: Erfahren Sie mehr über optionale Software, die Sie installieren können, um lokale Installationen von Adobe Commerce zu unterstützen.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Optionale Software

Es wird dringend empfohlen, NTP zu installieren, um sicherzustellen, dass cron-bezogene Aufgaben ordnungsgemäß ausgeführt werden. (Serverdaten können beispielsweise in der Vergangenheit oder in der Zukunft liegen.)

Die anderen in diesem Abschnitt beschriebenen optionalen Dienstprogramme können Ihnen bei der Installation helfen. Sie sind jedoch nicht erforderlich, um Adobe Commerce zu installieren oder zu verwenden.

## Installieren und Konfigurieren des Network Time Protocol (NTP)

[NTP](https://www.ntp.org/) ermöglicht es Servern, ihre Systemuhren mithilfe von [global verfügbaren Pool-Servern](https://www.ntppool.org/en/) zu synchronisieren. Es wird empfohlen, vertrauenswürdige NTP-Server zu verwenden, unabhängig davon, ob es sich um dedizierte Hardwarelösungen in Ihrem internen Netzwerk oder externe, öffentliche Server handelt.

Wenn Sie Adobe Commerce auf mehreren Hosts bereitstellen, ist NTP eine einfache Möglichkeit, um sicherzustellen, dass alle Uhren synchronisiert sind, unabhängig von der Zeitzone, in der sich die Server befinden. Außerdem hängen Cron-bezogene Aufgaben (wie Indizierung und Transaktions-E-Mails) davon ab, dass die Server-Uhr korrekt ist.

### Installieren und Konfigurieren von NTP auf Ubuntu

Geben Sie den folgenden Befehl ein, um NTP zu installieren:

```bash
apt-get install ntp
```

Fahren Sie mit [NTP-Pool-Server verwenden](#use-ntp-pool-servers) fort.

### Installieren und Konfigurieren von NTP auf CentOS

Installieren und Konfigurieren von NTP:

1. Geben Sie den folgenden Befehl ein, um die entsprechende NTP-Software zu finden:

   ```bash
   yum search ntp
   ```

1. Zu installierendes Paket auswählen. Beispiel: `ntp.x86_64`.

1. Installieren Sie das Paket .

   ```bash
   yum -y install ntp.x86_64
   ```

1. Geben Sie den folgenden Befehl ein, damit NTP gestartet wird, wenn der Server gestartet wird.

   ```bash
   chkconfig ntpd on
   ```

1. Fahren Sie mit dem nächsten Abschnitt fort.

### NTP-Pool-Server verwenden

Die Auswahl der Pool-Server liegt bei Ihnen. Wenn Sie NTP-Pool-Server verwenden, empfiehlt ntp.org die Verwendung [Pool-](https://www.ntppool.org/en/)), die sich in der Nähe der Zeitzone Ihrer Server befinden, wie auf der Seite [NTP-Pool-Projekt](https://www.ntppool.org/en/use.html) beschrieben. Wenn Sie über einen privaten NTP-Server verfügen, der für alle Hosts in Ihrer Bereitstellung verfügbar ist, können Sie stattdessen diesen Server verwenden.

1. Öffnen Sie `/etc/ntp.conf` in einem Texteditor.

1. Suchen Sie nach Zeilen, die den folgenden ähneln:

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Ersetzen Sie diese Zeilen oder fügen Sie zusätzliche Zeilen hinzu, die Ihren NTP-Pool-Server oder andere NTP-Server angeben. Es ist empfehlenswert, mehrere Namen zu nennen.

1. Im Folgenden finden Sie ein Beispiel für die Verwendung von drei US-basierten NTP-Servern:

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Speichern Sie Ihre Änderungen in `/etc/ntp.conf` und beenden Sie den Texteditor.

1. Starten Sie den Dienst neu.

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Geben Sie `date` ein, um das Datum des Servers zu überprüfen.

   Wenn das Datum falsch ist, stellen Sie sicher, dass der NTP-Client-Port (normalerweise UDP 123) in Ihrer Firewall geöffnet ist.

   Testen Sie den `ntpdate _[pool server hostname]_`. Wenn dies fehlschlägt, suchen Sie nach dem zurückgegebenen Fehler.

   Wenn alles andere fehlschlägt, versuchen Sie, den Server neu zu starten.

## Erstellen von phpinfo.php

Die [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php)-Datei zeigt eine große Menge an Informationen über PHP und seine Erweiterungen an.

>[!NOTE]
>
>Verwenden von `phpinfo.php` in einem Entwicklungssystem _nur_. Dies kann ein Sicherheitsproblem in der Produktion sein.

Fügen Sie den folgenden Code an einer beliebigen Stelle im Stammverzeichnis des Webservers hinzu:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Weitere Informationen finden Sie auf der [phpinfo-Handbuchseite](https://www.php.net/manual/en/function.phpinfo.php).

Um die Ergebnisse anzuzeigen, geben Sie die folgende URL in das Feld Speicherort oder Adresse Ihres Browsers ein:

```http
http://<web server host or IP>/phpinfo.php
```

Wenn der Fehler 404 (Nicht gefunden) angezeigt wird, überprüfen Sie Folgendes:

* Starten Sie bei Bedarf den Webserver.
* Stellen Sie sicher, dass Ihre Firewall Traffic auf Port 80 zulässt.

  [Hilfe für Ubuntu](https://help.ubuntu.com/community/UFW)

  [Hilfe für CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

Die phpMyAdmin-Anwendung ist ein benutzerfreundliches, kostenloses Dienstprogramm zur Datenbankverwaltung. Damit können Sie den Inhalt Ihrer Datenbank überprüfen und bearbeiten. Sie müssen sich bei phpMyAdmin als administrativer Benutzer der MySQL-Datenbank anmelden.

Weitere Informationen zu phpMyAdmin finden Sie auf der [phpMyAdmin-Startseite](https://www.phpmyadmin.net/).

Weitere Informationen zur Installation finden Sie in der [phpMyAdmin-Installationsdokumentation](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Verwenden Sie phpMyAdmin in einem Entwicklungssystem _only_. Dies kann ein Sicherheitsproblem in der Produktion sein.

1. Um phpMyAdmin zu verwenden, geben Sie den folgenden Befehl in das Adressfeld Ihres Browsers ein:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem MySQL-`root` oder dem Benutzernamen und Kennwort des Administrationsbenutzers an.
