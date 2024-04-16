---
title: Optionale Software
description: Erfahren Sie mehr über optionale Software, die Sie installieren können, um lokale Installationen von Adobe Commerce zu unterstützen.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# Optionale Software

Es wird dringend empfohlen, NTP zu installieren, um sicherzustellen, dass Cron-bezogene Aufgaben ordnungsgemäß ausgeführt werden. (Serverdaten können beispielsweise in der Vergangenheit oder Zukunft liegen.)

Die anderen in diesem Thema behandelten optionalen Hilfsprogramme können Ihnen bei Ihrer Installation helfen. Sie müssen jedoch weder Adobe Commerce noch Magento Open Source installieren oder verwenden.

## Installieren und Konfigurieren des Network Time Protocol (NTP)

[NTP](https://www.ntp.org/) ermöglicht Servern die Synchronisierung ihrer Systemuhren mithilfe von [global verfügbare Poolserver](https://www.ntppool.org/en/). Es wird empfohlen, die von Ihnen vertrauenswürdigen NTP-Server zu verwenden, unabhängig davon, ob es sich um dedizierte Hardware-Lösungen für Ihr internes Netzwerk oder externe, öffentliche Server handelt.

Wenn Sie Adobe Commerce oder Magento Open Source auf mehreren Hosts bereitstellen, ist NTP eine einfache Möglichkeit, sicherzustellen, dass alle Uhren synchronisiert werden, unabhängig davon, in welcher Zeitzone sich die Server befinden. Cron-bezogene Aufgaben (wie Indizierung und Transaktions-E-Mails) hängen außerdem von der Genauigkeit der Server-Uhr ab.

### Installieren und Konfigurieren von NTP auf Ubuntu

Geben Sie den folgenden Befehl ein, um NTP zu installieren:

```bash
apt-get install ntp
```

Fahren Sie mit [NTP-Poolserver verwenden](#use-ntp-pool-servers).

### Installieren und Konfigurieren von NTP unter CentOS

So installieren und konfigurieren Sie NTP:

1. Geben Sie den folgenden Befehl ein, um die entsprechende NTP-Software zu finden:

   ```bash
   yum search ntp
   ```

1. Wählen Sie ein zu installierendes Paket aus. Beispiel: `ntp.x86_64`.

1. Installieren Sie das Paket.

   ```bash
   yum -y install ntp.x86_64
   ```

1. Geben Sie den folgenden Befehl ein, damit NTP beim Start des Servers gestartet wird.

   ```bash
   chkconfig ntpd on
   ```

1. Fahren Sie mit dem nächsten Abschnitt fort.

### NTP-Poolserver verwenden

Die Auswahl der Poolserver liegt bei Ihnen. Wenn Sie NTP-Poolserver verwenden, empfiehlt ntp.org die Verwendung von [Poolserver](https://www.ntppool.org/en/) die sich in der Zeitzone Ihrer Server befinden, wie im Abschnitt [NTP-Pool-Projektseite](https://www.ntppool.org/en/use.html). Wenn Sie über einen privaten NTP-Server verfügen, der für alle Hosts in Ihrer Bereitstellung verfügbar ist, können Sie stattdessen diesen Server verwenden.

1. Öffnen `/etc/ntp.conf` in einem Texteditor.

1. Suchen Sie nach Zeilen, die den folgenden ähneln:

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Ersetzen Sie diese Zeilen oder fügen Sie zusätzliche Zeilen hinzu, die Ihren NTP-Poolserver oder andere NTP-Server angeben. Es empfiehlt sich, mehr als eine zu spezifizieren.

1. Ein Beispiel für die Verwendung von drei auf den USA basierenden NTP-Servern:

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Speichern Sie Ihre Änderungen in `/etc/ntp.conf` und beenden Sie den Texteditor.

1. Starten Sie den Dienst neu.

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Eingabe `date` , um das Datum des Servers zu überprüfen.

   Wenn das Datum falsch ist, stellen Sie sicher, dass der NTP-Client-Port (normalerweise UDP 123) in Ihrer Firewall geöffnet ist.

   Probieren Sie die `ntpdate _[pool server hostname]_` Befehl. Wenn es fehlschlägt, suchen Sie nach dem zurückgegebenen Fehler.

   Wenn alles andere fehlschlägt, versuchen Sie, den Server neu zu starten.

## Erstellen von phpinfo.php

Die [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) zeigt eine große Menge an Informationen über PHP und seine Erweiterungen an.

>[!NOTE]
>
>Verwendung `phpinfo.php` in einem Entwicklungssystem _only_. Es kann sich um ein Sicherheitsproblem in der Produktion handeln.

Fügen Sie den folgenden Code an einer beliebigen Stelle im Basisverzeichnis Ihres Webservers hinzu:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Weitere Informationen finden Sie unter [phpinfo-manuelle Seite](https://www.php.net/manual/en/function.phpinfo.php).

Um die Ergebnisse anzuzeigen, geben Sie die folgende URL in das Adressfeld Ihres Browsers ein:

```http
http://<web server host or IP>/phpinfo.php
```

Wenn der Fehler 404 (Nicht gefunden) angezeigt wird, überprüfen Sie Folgendes:

* Starten Sie bei Bedarf den Webserver.
* Stellen Sie sicher, dass Ihre Firewall Traffic auf Port 80 zulässt.

  [Hilfe für Ubuntu](https://help.ubuntu.com/community/UFW)

  [Hilfe für CentOS](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

Die phpMyAdmin Anwendung ist ein einfach zu bedienendes, kostenloses Dienstprogramm zur Datenbankverwaltung. Sie können damit den Inhalt Ihrer Datenbank überprüfen und bearbeiten. Sie müssen sich bei phpMyAdmin als Verwaltungsbenutzer der MySQL-Datenbank anmelden.

Weitere Informationen zu phpMyAdmin finden Sie unter [phpMyAdmin-Homepage](https://www.phpmyadmin.net/).

Weitere Informationen zur Installation finden Sie unter [phpMyAdmin-Installationsdokumentation](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>phpMyAdmin in einem Entwicklungssystem verwenden _only_. Es kann sich um ein Sicherheitsproblem in der Produktion handeln.

1. Um phpMyAdmin zu verwenden, geben Sie den folgenden Befehl in das Adressfeld oder Standortfeld Ihres Browsers ein:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Melden Sie sich bei entsprechender Aufforderung mit Ihrer MySQL-Datenbank an `root` oder dem Benutzernamen und Kennwort des Administrationsbenutzers.
