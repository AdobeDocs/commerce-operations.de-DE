---
title: Nginx
description: Führen Sie diese Schritte aus, um den Nginx-Webserver für lokale Installationen von Adobe Commerce zu installieren und zu konfigurieren.
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---

# Nginx

Adobe Commerce unterstützt Nginx 1.x (oder die [neueste Hauptversion](https://nginx.org/en/linux_packages.html#mainline)). Sie müssen auch die neueste Version von `php-fpm` installieren.

Die Installationsanweisungen hängen vom verwendeten Betriebssystem ab. Siehe [PHP](../php-settings.md) für weitere Informationen.

## Ubuntu

Im folgenden Abschnitt wird beschrieben, wie Sie Adobe Commerce 2.x mit nginx, PHP und MySQL auf Ubuntu installieren.

### Installieren von nginx

```bash
sudo apt -y install nginx
```

Sie können auch [aus der Quelle erstellen](https://www.armanism.com/blog/install-nginx-on-ubuntu)

Nachdem wir die folgenden Abschnitte ausgeführt und die Anwendung installiert haben, verwenden wir eine Beispielkonfigurationsdatei zum [Konfigurieren von nginx](#configure-nginx).

### Installieren und Konfigurieren von php-fpm

Adobe Commerce benötigt mehrere [PHP Extensions](../php-settings.md) um ordnungsgemäß zu funktionieren. Zusätzlich zu diesen Erweiterungen müssen Sie auch die `php-fpm`-Erweiterung installieren und konfigurieren, wenn Sie nginx verwenden.

So installieren und konfigurieren Sie `php-fpm`:

1. Installieren von `php-fpm` und `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >Dieser Befehl installiert die neueste verfügbare Version von PHP 7.2.X. Siehe [Systemanforderungen](../../system-requirements.md) für unterstützte PHP-Versionen.

1. Öffnen Sie die `php.ini` Dateien in einem Editor:

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. Bearbeiten Sie beide Dateien so, dass sie den folgenden Zeilen entsprechen:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Beim Testen von Adobe Commerce wird empfohlen, die Speicherbegrenzung auf 2 G festzulegen. Weitere Informationen finden Sie [Erforderliche PHP](../php-settings.md)Einstellungen).

1. Speichern und Beenden des Editors.

1. Starten Sie den `php-fpm` neu:

   ```bash
   systemctl restart php7.2-fpm
   ```

### Installieren und Konfigurieren von MySQL

Weitere Informationen finden Sie [MySQL](../database/mysql.md).

### Installieren und Konfigurieren

Es gibt verschiedene Möglichkeiten, Adobe Commerce herunterzuladen:

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

1. Installieren Sie über [Befehlszeile](../../advanced.md). In diesem Beispiel wird davon ausgegangen, dass der Installationsordner `magento2ee` heißt, sich der `db-host` auf demselben Computer befindet (`localhost`) und dass die `db-name`, `db-user` und `db-password` alle `magento` sind:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. Wechseln Sie in den Entwicklermodus:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Konfigurieren von nginx

Es wird empfohlen, nginx mithilfe der im Installationsverzeichnis und virtuellen nginx-Host bereitgestellten `nginx.conf.sample`-Konfigurationsdatei zu konfigurieren.

In diesen Anweisungen wird davon ausgegangen, dass Sie den Ubuntu-Standardspeicherort für den virtuellen nginx-Host (z. B. `/etc/nginx/sites-available`) und den Ubuntu-Standardstammordner (z. B. `/var/www/html`) verwenden. Sie können diese Speicherorte jedoch an Ihre Umgebung anpassen.

1. Erstellen Sie einen neuen virtuellen Host für Ihre Site:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Fügen Sie die folgende Konfiguration hinzu:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
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

Öffnen Sie einen Webbrowser und navigieren Sie zur Basis-URL Ihrer Site, um [Installation zu überprüfen](../../next-steps/verify.md).

## CentOS 7

Im folgenden Abschnitt wird beschrieben, wie Sie Adobe Commerce 2.x unter CentOS 7 mit nginx, PHP und MySQL installieren.

### Installieren von nginx

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

Nachdem wir die folgenden Abschnitte ausgeführt und die Anwendung installiert haben, verwenden wir eine Beispielkonfigurationsdatei für die Konfiguration von nginx.

### Installieren und Konfigurieren von php-fpm

Adobe Commerce benötigt mehrere [PHP](../php-settings.md)-Erweiterungen, um ordnungsgemäß zu funktionieren. Zusätzlich zu diesen Erweiterungen müssen Sie auch die `php-fpm`-Erweiterung installieren und konfigurieren, wenn Sie nginx verwenden.

1. Installieren Sie `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. Öffnen Sie die `/etc/php.ini` in einem Editor.

1. Entfernen Sie den Kommentar für die `cgi.fix_pathinfo` und ändern Sie den Wert in `0`.

1. Bearbeiten Sie die Datei so, dass sie mit den folgenden Zeilen übereinstimmt:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Beim Testen von Adobe Commerce wird empfohlen, die Speicherbegrenzung auf 2 G festzulegen. Weitere Informationen finden Sie [Erforderliche PHP](../php-settings.md)Einstellungen).

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

1. Erstellen Sie ein Verzeichnis für den PHP-Sitzungspfad und ändern Sie den Besitzer in den `apache` Benutzer und die Gruppe:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. Erstellen Sie ein Verzeichnis für den PHP-Sitzungspfad und ändern Sie den Besitzer in den `apache` Benutzer und die Gruppe:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
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

Weitere Informationen finden Sie [MySQL](..//database/mysql.md).

### Installieren und Konfigurieren

Es gibt verschiedene Möglichkeiten, die Adobe Commerce herunterzuladen, darunter:

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

1. Installieren Sie über [Befehlszeile](../../advanced.md). In diesem Beispiel wird davon ausgegangen, dass der Installationsordner `magento2ee` heißt, sich der `db-host` auf demselben Computer befindet (`localhost`) und dass die `db-name`, `db-user` und `db-password` alle `magento` sind:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Wechseln Sie in den Entwicklermodus:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Konfigurieren von nginx

Es wird empfohlen, nginx mithilfe der im Installationsverzeichnis und virtuellen nginx-Host bereitgestellten `nginx.conf.sample`-Konfigurationsdatei zu konfigurieren.

In diesen Anweisungen wird davon ausgegangen, dass Sie den CentOS-Standardspeicherort für den virtuellen nginx-Host (z. B. `/etc/nginx/conf.d`) und den standardmäßigen docroot-Speicherort (z. B. `/usr/share/nginx/html`) verwenden. Sie können diese Speicherorte jedoch an Ihre Umgebung anpassen.

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

### Konfigurieren von SELinux und Firewalls

SELinux ist standardmäßig unter CentOS 7 aktiviert. Verwenden Sie den folgenden Befehl, um zu überprüfen, ob er ausgeführt wird:

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

Öffnen Sie einen Webbrowser und navigieren Sie zur Basis-URL Ihrer Site, um [Installation zu überprüfen](../../next-steps/verify.md).
