---
title: Installieren von Nginx für On-Premise-Bereitstellungen
description: Erfahren Sie, wie Sie den Nginx-Webserver für lokale Adobe Commerce-Bereitstellungen installieren und konfigurieren. Richten Sie PHP-FPM und Ihren virtuellen Host ein.
feature: Install, Configuration
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# Installieren von Nginx für lokale Bereitstellungen {#nginx}

Dieses Handbuch führt Sie durch die Installation von Nginx für lokale Adobe Commerce-Bereitstellungen und die Konfiguration der Nginx-Einstellungen, die für Commerce erforderlich sind. Es enthält betriebssystemspezifische Verfahren für Ubuntu und CentOS sowie Anleitungen zur Konfiguration von PHP-FPM. Adobe empfiehlt, die Konfigurationsanweisungen in diesem Handbuch zu befolgen, um sowohl die Funktionalität als auch die Sicherheit des Commerce-Programms zu wahren.

Adobe unterstützt die Nginx-Versionen, die in den [Systemanforderungen](../../system-requirements.md) für Ihre Adobe Commerce-Version aufgeführt sind. Unterstützte Versionen variieren je nach Version. Nginx benötigt außerdem eine unterstützte PHP-FPM-Konfiguration. Weitere Informationen zu PHP-Anforderungen finden Sie unter [PHP](../php-settings.md).

## Auf Ubuntu installieren

Verwenden Sie diesen Abschnitt, um Adobe Commerce auf Ubuntu mit Nginx, PHP und MySQL zu installieren.

### Installieren von Nginx

```bash
sudo apt -y install nginx
```

Sie können auch [Nginx aus der Quelle erstellen](https://www.armanism.com/blog/install-nginx-on-ubuntu).

Nachdem Sie die folgenden Abschnitte ausgeführt und die Anwendung installiert haben, verwenden Sie die Beispielkonfigurationsdatei zum [&#x200B; von Nginx](#configure-nginx). Diese empfohlene Konfiguration behält sowohl die Funktionalität als auch die Sicherheit des Commerce-Programms bei.

### Installieren und Konfigurieren von PHP-FPM

Adobe Commerce benötigt mehrere [PHP Extensions](../php-settings.md) um ordnungsgemäß zu funktionieren. Zusätzlich zu diesen Erweiterungen müssen Sie auch die `php-fpm`-Erweiterung installieren und konfigurieren, wenn Sie Nginx verwenden.

So installieren und konfigurieren Sie `php-fpm`:

1. Installieren Sie die `php-fpm`- und `php-cli`-Pakete für die PHP-Version, die von Ihrer Adobe Commerce-Version unterstützt wird. Auf Ubuntu folgen Paketnamen normalerweise diesem Muster:

   ```bash
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >Ersetzen Sie `<php-version>` durch die unterstützte PHP-Nebenversion, [&#x200B; unter „Systemanforderungen](../../system-requirements.md) für die Adobe Commerce-Version aufgeführt ist, die Sie installieren. Verwenden Sie denselben Wert in den Dateipfaden, dem Service-Namen und dem Socket-Pfad in den folgenden Schritten.

1. Öffnen Sie die `php.ini` Dateien in einem Editor:

   ```bash
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```bash
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. Bearbeiten Sie beide Dateien so, dass sie den folgenden Zeilen entsprechen:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe empfiehlt, beim Testen von Adobe Commerce die Speicherbegrenzung auf 2 GB festzulegen. Weitere Informationen finden Sie [Erforderliche PHP](../php-settings.md)Einstellungen).

1. Speichern und Beenden des Editors.

1. Starten Sie den `php-fpm` neu:

   ```bash
   systemctl restart php<php-version>-fpm
   ```

### Installieren und Konfigurieren von MySQL

Weitere Informationen finden Sie [MySQL](../database/mysql.md).

### Installieren von Adobe Commerce

Sie haben verschiedene Möglichkeiten, Adobe Commerce herunterzuladen:

* [Abrufen des Composer-Metapakets](../../composer.md)

* [Klonen Sie das Git-Repository](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

Dieses Beispiel zeigt eine Composer-basierte Installation über die Befehlszeile.

1. Melden Sie [&#x200B; als „Dateisystemeigentümer](../file-system/overview.md) bei Ihrem Anwendungs-Server an.

1. Wechseln Sie in das Verzeichnis des Webservers docroot oder in ein Verzeichnis, das Sie als virtuellen Host docroot konfiguriert haben. Für dieses Beispiel verwenden wir den Ubuntu-`/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installieren Sie Composer global. Composer ist erforderlich, um Abhängigkeiten vor der Installation von Adobe Commerce zu aktualisieren:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Erstellen Sie ein Composer-Projekt mit dem Adobe Commerce-Metapaket.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Geben Sie nach Aufforderung Ihre [Authentifizierungsschlüssel](../authentication-keys.md) ein. Ihr _öffentlicher Schlüssel_ ist Ihr Benutzername; Ihr _privater Schlüssel_ ist Ihr Kennwort.

1. Legen Sie vor der Installation der Anwendung Lese- und Schreibberechtigungen für die Webservergruppe fest. Dies ist erforderlich, damit die Befehlszeile Dateien in das Dateisystem schreiben kann.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installieren Sie über [Befehlszeile](../../advanced.md). In diesem Beispiel wird davon ausgegangen, dass das Installationsverzeichnis `magento2ee` heißt und sich der Datenbank-Host auf demselben Computer befindet (`localhost`):

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >Verwenden Sie den `--search-engine` und die entsprechenden Host-/Port-Optionen für die Adobe Commerce-Version, die Sie installieren. Bei Versionen vor 2.4.6 verwenden Sie `elasticsearch7` mit den `--elasticsearch-*` Optionen für Elasticsearch 7 oder OpenSearch. Verwenden Sie für Version 2.4.6 und höher den Suchmaschinenwert und die entsprechenden CLI-Optionen, die von dieser Version unterstützt werden.

1. Wechseln Sie in den Entwicklermodus:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Konfigurieren von nginx

Adobe empfiehlt, Nginx mithilfe der im Installationsverzeichnis bereitgestellten `nginx.conf.sample`-Konfigurationsdatei und Ihrer virtuellen Nginx-Host-Konfiguration zu konfigurieren, um sowohl die Funktionalität als auch die Sicherheit der Commerce-Anwendung zu wahren.

>[!IMPORTANT]
>
>Die `nginx.conf.sample`-Datei bietet das erforderliche Anwendungs-Routing sowie Regeln zum Härten der Sicherheit. Zum Beispiel schränkt es die Ausführung schädlicher Skripte ein, die auf den Server hochgeladen werden. Wenn Sie diese Datei nicht verwenden oder ihre Regeln ändern, sind Sie für die Implementierung gleichwertiger Sicherheitskontrollen in Ihrer benutzerdefinierten Nginx-Konfiguration verantwortlich.

Bei diesen Anweisungen wird davon ausgegangen, dass Sie den Ubuntu-Standardspeicherort für den virtuellen Nginx-Host wie `/etc/nginx/sites-available` und den Ubuntu-Standardstammordner wie `/var/www/html` verwenden. Sie können diese Speicherorte an Ihre Umgebung anpassen.

1. Erstellen Sie einen neuen virtuellen Host für Ihre Site:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Fügen Sie die folgende Konfiguration hinzu:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >Die `include`-Anweisung muss auf die Beispielkonfigurationsdatei nginx in Ihrem Installationsverzeichnis verweisen.

1. Ersetzen Sie `www.magento-dev.com` durch Ihren Domain-Namen. Dieser muss mit der Basis-URL übereinstimmen, die Sie bei der Installation von Adobe Commerce angegeben haben.

1. Speichern und Beenden des Editors.

1. Aktivieren Sie den neu erstellten virtuellen Host, indem Sie einen Symlink zu ihm im `/etc/nginx/sites-enabled` erstellen:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Überprüfen Sie, ob die Syntax korrekt ist:

   ```bash
   nginx -t
   ```

1. Nginx neu starten:

   ```bash
   systemctl restart nginx
   ```

### Überprüfen der Installation

Um die Installation zu überprüfen, öffnen Sie einen Webbrowser und navigieren Sie zur Basis-URL Ihrer Site. Weitere Informationen finden Sie unter [Überprüfen der Installation](../../next-steps/verify.md).

## Installieren auf CentOS 7

Verwenden Sie diesen Abschnitt, um Adobe Commerce auf CentOS 7 mit Nginx, PHP und MySQL zu installieren.

### Installieren von Nginx

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

Nachdem die Installation abgeschlossen ist, starten Sie nginx und konfigurieren Sie es so, dass es beim Booten startet:

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

Nachdem Sie die folgenden Abschnitte ausgeführt und die Anwendung installiert haben, verwenden Sie eine Beispielkonfigurationsdatei für Nginx.

### Installieren und Konfigurieren von PHP-FPM

Adobe Commerce benötigt mehrere [PHP](../php-settings.md)-Erweiterungen, um ordnungsgemäß zu funktionieren. Zusätzlich zu diesen Erweiterungen müssen Sie auch die `php-fpm`-Erweiterung installieren und konfigurieren, wenn Sie Nginx verwenden.

1. Installieren Sie `php-fpm`:

   ```bash
   yum -y install <php-fpm-package>
   ```

1. Öffnen Sie die `/etc/php.ini` in einem Editor.

   >[!NOTE]
   >
   >Installieren Sie das Paket, das `php-fpm` für die PHP-Version bereitstellt, die von der Adobe Commerce-Version unterstützt wird, die Sie installieren. Paketnamen variieren je nach Repository und Betriebssystem. Siehe [Systemanforderungen](../../system-requirements.md).

1. Entfernen Sie den Kommentar für die `cgi.fix_pathinfo` und ändern Sie den Wert in `0`.

1. Bearbeiten Sie die Datei so, dass sie mit den folgenden Zeilen übereinstimmt:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe empfiehlt, beim Testen von Adobe Commerce die Speicherbegrenzung auf 2 GB festzulegen. Weitere Informationen finden Sie [Erforderliche PHP](../php-settings.md)Einstellungen).

1. Entfernen Sie den Kommentar für den Sitzungspfadordner und legen Sie den Pfad fest:

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Speichern und Beenden des Editors.

1. Öffnen Sie `/etc/php-fpm.d/www.conf` in einem Editor.

1. Bearbeiten Sie die Datei so, dass sie mit den folgenden Zeilen übereinstimmt:

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Entfernen Sie den Kommentar für die Umgebungszeilen:

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Speichern und Beenden des Editors.

1. Erstellen Sie ein Verzeichnis für den PHP-Sitzungspfad und ändern Sie den Besitzer in den `nginx` Benutzer und die Gruppe:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R nginx:nginx /var/lib/php/
   ```

1. Erstellen Sie ein Verzeichnis für den PHP-FPM-Socket und ändern Sie den Besitzer in den `nginx` Benutzer und die Gruppe:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R nginx:nginx /run/php-fpm/
   ```

1. Starten Sie den `php-fpm`-Service und konfigurieren Sie ihn so, dass er beim Starten gestartet wird:

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Stellen Sie sicher, dass der `php-fpm` Dienst ausgeführt wird:

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Installieren und Konfigurieren von MySQL

Weitere Informationen finden Sie [MySQL](../database/mysql.md).

### Installieren von Adobe Commerce

Sie haben verschiedene Möglichkeiten, Adobe Commerce herunterzuladen:

* [Abrufen des Composer-Metapakets](../../composer.md)

* [Klonen Sie das Git-Repository](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

Dieses Beispiel zeigt eine Composer-basierte Installation über die Befehlszeile.

1. Melden Sie [&#x200B; als „Dateisystemeigentümer](../file-system/overview.md) bei Ihrem Anwendungs-Server an.

1. Wechseln Sie in das Verzeichnis des Webservers docroot oder in ein Verzeichnis, das Sie als virtuellen Host docroot konfiguriert haben. Verwenden Sie für dieses Beispiel die CentOS-`/usr/share/nginx/html`.

   ```bash
   cd /usr/share/nginx/html
   ```

1. Installieren Sie Composer global. Composer ist erforderlich, um Abhängigkeiten vor der Installation von Adobe Commerce zu aktualisieren:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Erstellen Sie ein Composer-Projekt mit dem Adobe Commerce-Metapaket.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Geben Sie nach Aufforderung Ihre [Authentifizierungsschlüssel](../authentication-keys.md) ein. Ihr _öffentlicher Schlüssel_ ist Ihr Benutzername; Ihr _privater Schlüssel_ ist Ihr Kennwort.

1. Legen Sie vor der Installation der Anwendung Lese- und Schreibberechtigungen für die Webservergruppe fest. Dies ist erforderlich, damit die Befehlszeile Dateien in das Dateisystem schreiben kann.

   ```bash
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :nginx . # CentOS
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installieren Sie über [Befehlszeile](../../advanced.md). In diesem Beispiel wird davon ausgegangen, dass das Installationsverzeichnis `magento2ee` heißt und sich der Datenbank-Host auf demselben Computer befindet (`localhost`):

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Wechseln Sie in den Entwicklermodus:

   ```bash
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Konfigurieren von nginx

Es wird empfohlen, Nginx mithilfe der `nginx.conf.sample`-Datei im Installationsverzeichnis und Ihrer virtuellen Nginx-Host-Konfiguration zu konfigurieren.

>[!IMPORTANT]
>
>Die `nginx.conf.sample`-Datei bietet das erforderliche Anwendungs-Routing sowie Regeln zum Härten der Sicherheit. Zum Beispiel schränkt es die Ausführung schädlicher Skripte ein, die auf den Server hochgeladen werden. Wenn Sie diese Datei nicht verwenden oder ihre Regeln ändern, sind Sie für die Implementierung gleichwertiger Sicherheitskontrollen in Ihrer benutzerdefinierten Nginx-Konfiguration verantwortlich.

Bei diesen Anweisungen wird davon ausgegangen, dass Sie den CentOS-Standardspeicherort für den virtuellen Nginx-Host wie `/etc/nginx/conf.d` und den standardmäßigen Docroot wie `/usr/share/nginx/html` verwenden. Sie können diese Speicherorte an Ihre Umgebung anpassen.

1. Erstellen Sie einen neuen virtuellen Host für Ihre Site:

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. Fügen Sie die folgende Konfiguration hinzu:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >Die `include`-Anweisung muss auf die Beispielkonfigurationsdatei nginx in Ihrem Installationsverzeichnis verweisen.

1. Ersetzen Sie `www.magento-dev.com` durch Ihren Domain-Namen.

1. Speichern und Beenden des Editors.

1. Überprüfen Sie, ob die Syntax korrekt ist:

   ```bash
   nginx -t
   ```

1. Nginx neu starten:

   ```bash
   systemctl restart nginx
   ```

### Konfigurieren von SELinux und Firewall

SELinux ist standardmäßig unter CentOS 7 aktiviert. Verwenden Sie den folgenden Befehl, um die Ausführung zu bestätigen:

```bash
sestatus
```

So konfigurieren Sie SELinux und Firewall:

1. Installieren der SELinux-Verwaltungstools:

   ```bash
   yum -y install policycoreutils-python
   ```

1. Führen Sie die folgenden Befehle aus, um den Sicherheitskontext für das Installationsverzeichnis zu ändern:

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. Installieren Sie das Firewall-Paket:

   ```bash
   yum -y install firewalld
   ```

1. Starten Sie den Firewall-Dienst, und konfigurieren Sie ihn so, dass er beim Starten gestartet wird:

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. Führen Sie die folgenden Befehle aus, um Ports für HTTP und HTTPS zu öffnen, damit Sie über einen Webbrowser auf die Basis-URL zugreifen können:

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### Überprüfen der Installation

Um die Installation zu überprüfen, öffnen Sie einen Webbrowser und navigieren Sie zur Basis-URL Ihrer Site. Weitere Informationen finden Sie unter [Überprüfen der Installation](../../next-steps/verify.md).
