---
title: Sicheres cron-PHP
description: Beschränken Sie, wer die Datei cron.php in einem Browser ausführen kann.
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 1%

---

# Sicheres cron-PHP

In diesem Thema wird das Schützen von `pub/cron.php` beschrieben, um zu verhindern, dass es in einer böswilligen Exploit verwendet wird. Wenn Sie Cron nicht schützen, kann jeder Benutzer möglicherweise Cron ausführen, um Ihre Commerce-Anwendung anzugreifen.

Der Cron-Auftrag führt mehrere geplante Aufgaben aus und ist ein wichtiger Bestandteil Ihrer Commerce-Konfiguration. Geplante Aufgaben umfassen unter anderem:

- Neuindizierung
- E-Mails erstellen
- Newsletter erstellen
- Erstellen von Sitemaps

>[!INFO]
>
>Weitere Informationen zu Cron-Gruppen finden Sie unter [CRON konfigurieren und ausführen](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) .

Sie können einen Cron-Auftrag wie folgt ausführen:

- Verwenden des Befehls [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) entweder über die Befehlszeile oder in einer Registerkarte mit der Clientfunktion
- Zugriff auf `pub/cron.php?[group=<name>]` in einem Webbrowser

>[!INFO]
>
>Sie müssen nichts tun, wenn Sie den Befehl [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) zum Ausführen von Cron verwenden, da er einen anderen Prozess verwendet, der bereits sicher ist.

## Sicheres Cron mit Apache

In diesem Abschnitt wird beschrieben, wie Sie Cron mit der HTTP Basic-Authentifizierung mit Apache sichern. Diese Anweisungen basieren auf Apache 2.2 mit CentOS 6. Weitere Informationen finden Sie in einer der folgenden Ressourcen:

- [Tutorial zur Authentifizierung und Autorisierung mit Apache 2.2](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Tutorial zur Authentifizierung und Autorisierung mit Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

### Kennwortdatei erstellen

Aus Sicherheitsgründen können Sie die Kennwortdatei an einer beliebigen Stelle außerhalb des Basisverzeichnisses für Ihren Webserver finden. In diesem Beispiel speichern wir die Kennwortdatei in einem neuen Verzeichnis.

Geben Sie die folgenden Befehle als Benutzer mit `root` -Berechtigungen ein:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

Dabei kann `<username>` der Webserver-Benutzer oder ein anderer Benutzer sein. In diesem Beispiel verwenden wir den Webserver-Benutzer, aber die Wahl des Benutzers liegt bei Ihnen.

Befolgen Sie die Anweisungen auf Ihrem Bildschirm, um ein Kennwort für den Benutzer zu erstellen.

Um Ihrer Kennwortdatei einen weiteren Benutzer hinzuzufügen, geben Sie den folgenden Befehl als Benutzer mit `root` -Berechtigungen ein:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### Benutzer hinzufügen, um eine autorisierte Cron-Gruppe zu erstellen (optional)

Sie können mehrere Benutzer aktivieren, um cron auszuführen, indem Sie diese Benutzer zu Ihrer Kennwortdatei hinzufügen, einschließlich einer Gruppendatei.

So fügen Sie Ihrer Kennwortdatei einen weiteren Benutzer hinzu:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

Um eine autorisierte Gruppe zu erstellen, erstellen Sie eine Gruppendatei an einer beliebigen Stelle außerhalb des Dokumentenstamms des Webservers. Die Gruppendatei gibt den Namen der Gruppe und die Benutzer in der Gruppe an. In diesem Beispiel lautet der Gruppenname `MagentoCronGroup`.

```bash
vim /usr/local/apache/password/group
```

Inhalt der Datei:

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### Sicherer Cron in `.htaccess`

Sichern von Cron in der Datei `.htaccess` :

1. Melden Sie sich bei Ihrem Commerce-Server als Dateisysteminhaber an oder wechseln Sie zu ihm.
1. Öffnen Sie `<magento_root>/pub/.htaccess` in einem Texteditor.

   (Da sich `cron.php` im Verzeichnis `pub` befindet, bearbeiten Sie nur diese `.htaccess`.)

1. _Cron-Zugriff für einen oder mehrere Benutzer._ Ersetzen Sie die vorhandene `<Files cron.php>` -Direktive durch Folgendes:

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _Cron-Zugriff für eine Gruppe._ Ersetzen Sie die vorhandene `<Files cron.php>` -Direktive durch Folgendes:

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. Speichern Sie Ihre Änderungen in `.htaccess` und beenden Sie den Texteditor.
1. Fahren Sie mit [Überprüfen Sie, ob der Cron sicher ist](#verify-cron-is-secure).

## Sicherer Cron mit Nginx

In diesem Abschnitt wird beschrieben, wie Sie Cron mit dem Nginx-Webserver sichern. Sie müssen die folgenden Aufgaben ausführen:

1. Verschlüsselte Kennwortdatei für Nginx einrichten
1. Ändern Sie Ihre nginx-Konfiguration so, dass beim Zugriff auf `pub/cron.php` auf die Kennwortdatei verwiesen wird.

### Kennwortdatei erstellen

Lesen Sie eine der folgenden Ressourcen, um eine Kennwortdatei zu erstellen, bevor Sie fortfahren:

- [Einrichten der Kennwortauthentifizierung mit Nginx auf Ubuntu 14.04 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [Einfache HTTP-Authentifizierung mit Nginx (howtoforge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### Sicherer Cron in `nginx.conf.sample`

Commerce bietet standardmäßig eine optimierte Beispielkonfigurationsdatei für nginx. Es wird empfohlen, ihn zu ändern, um Cron zu schützen.

1. Fügen Sie Ihrer Datei [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) Folgendes hinzu:

   ```conf
   #Securing cron
   location ~ cron\.php$ {
      auth_basic "Cron Authentication";
      auth_basic_user_file /etc/nginx/.htpasswd;
   
      try_files $uri =404;
      fastcgi_pass   fastcgi_backend;
      fastcgi_buffers 1024 4k;
   
      fastcgi_read_timeout 600s;
      fastcgi_connect_timeout 600s;
   
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include        fastcgi_params;
   }
   ```

1. Nginx neu starten:

```bash
systemctl restart nginx
```

1. Fahren Sie mit [Überprüfen Sie, ob der Cron sicher ist](#verify-cron-is-secure).

## Sicherstellen, dass Cron sicher ist

Die einfachste Methode, um sicherzustellen, dass `pub/cron.php` sicher ist, besteht darin, nach der Einrichtung der Kennwortauthentifizierung sicherzustellen, dass Zeilen in der Datenbanktabelle `cron_schedule` erstellt werden. In diesem Beispiel werden SQL-Befehle verwendet, um die Datenbank zu überprüfen. Sie können jedoch jedes beliebige Tool verwenden.

>[!INFO]
>
>Der `default`-Cron, den Sie in diesem Beispiel ausführen, wird gemäß dem in `crontab.xml` definierten Zeitplan ausgeführt. Einige Cron-Aufträge werden nur einmal am Tag ausgeführt. Wenn Sie Cron zum ersten Mal über den Browser ausführen, wird die Tabelle `cron_schedule` aktualisiert, nachfolgende `pub/cron.php` -Anforderungen werden jedoch gemäß dem konfigurierten Zeitplan ausgeführt.

**Überprüfen, ob der Cron sicher ist**:

1. Melden Sie sich bei der Datenbank als Commerce-Datenbankbenutzer oder als `root` an.

   Beispiel:

   ```bash
   mysql -u magento -p
   ```

1. Verwenden Sie die Commerce-Datenbank:

   ```shell
   use <database-name>;
   ```

   Beispiel:

   ```shell
   use magento;
   ```

1. Löschen Sie alle Zeilen aus der `cron_schedule` -Datenbanktabelle:

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. Führen Sie cron über einen Browser aus:

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   Beispiel:

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. Geben Sie bei Aufforderung den Namen und das Kennwort eines autorisierten Benutzers ein. Die folgende Abbildung zeigt ein Beispiel.

   ![Autorisieren von Cron mit HTTP Basic](../../assets/configuration/cron-auth.png)

1. Stellen Sie sicher, dass der Tabelle Zeilen hinzugefügt wurden:

   ```shell
   SELECT * from cron_schedule;
   
   mysql> SELECT * from cron_schedule;
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   | schedule_id | job_code                             | status  | messages | created_at        | scheduled_at      | executed_at | finished_at |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   |         1 | catalog_product_outdated_price_values_cleanup | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         2 | sales_grid_order_async_insert             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         3 | sales_grid_order_invoice_async_insert       | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         4 | sales_grid_order_shipment_async_insert      | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         5 | sales_grid_order_creditmemo_async_insert     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         6 | sales_send_order_emails                  | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         7 | sales_send_order_invoice_emails            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         8 | sales_send_order_shipment_emails           | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         9 | sales_send_order_creditmemo_emails         | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        10 | newsletter_send_all                     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:25:00 | NULL      | NULL      |
   |        11 | captcha_delete_old_attempts               | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        12 | captcha_delete_expired_images             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        13 | outdated_authentication_failures_cleanup     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        14 | magento_newrelicreporting_cron            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   14 rows in set (0.00 sec)
   ```

## Ausführen von Cron über einen Webbrowser

Sie können Cron jederzeit ausführen, z. B. während der Entwicklung, mithilfe eines Webbrowsers.

>[!WARNING]
>
>Führen Sie cron _nicht_ in einem Browser aus, ohne es zuerst zu sichern.

Wenn Sie einen Apache-Webserver verwenden, müssen Sie die Beschränkung aus der Datei &quot;`.htaccess`&quot;entfernen, bevor Sie Cron in einem Browser ausführen können:

1. Melden Sie sich bei Ihrem Commerce-Server als Benutzer mit Schreibberechtigung für das Commerce-Dateisystem an.
1. Öffnen Sie Folgendes in einem Texteditor (je nach Einstiegspunkt in die Magento):

   ```text
   <magento_root>/pub/.htaccess
   <magento_root>/.htaccess
   ```

1. Löschen oder kommentieren Sie Folgendes aus:

   ```conf
   ## Deny access to cron.php
     <Files cron.php>
        order allow,deny
        deny from all
     </Files>
   ```

   Beispiel:

   ```conf
   ## Deny access to cron.php
      #<Files cron.php>
         # order allow,deny
         # deny from all
      #</Files>
   ```

1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.

   Anschließend können Sie Cron wie folgt in einem Webbrowser ausführen:

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

Dabei gilt:

- `<your hostname or IP>` ist der Hostname oder die IP-Adresse Ihrer Commerce-Installation.
- `<Commerce root>` ist das docroot-relative Verzeichnis des Webservers, in dem Sie die Commerce-Software installiert haben

  Die genaue URL, die Sie zum Ausführen der Commerce-Anwendung verwenden, hängt von der Konfiguration Ihres Webservers und virtuellen Hosts ab.

- `<group name>` ist ein beliebiger gültiger Cron-Gruppenname (optional)

Beispiel:

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>Sie müssen Cron zweimal ausführen: zuerst entdecken Sie Aufgaben, die ausgeführt werden sollen, und wieder, um die Aufgaben selbst auszuführen. Weitere Informationen zu Cron-Gruppen finden Sie unter [CRON konfigurieren und ausführen](../cli/configure-cron-jobs.md) .
