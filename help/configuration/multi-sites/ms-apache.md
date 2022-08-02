---
title: Einrichten mehrerer Websites mit Apache
description: In diesem Tutorial erfahren Sie, wie Sie mehrere Websites mit Apache einrichten.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# Einrichten mehrerer Websites mit Apache

Wir gehen davon aus, dass

Falls erforderlich, kopieren Sie die vorhandene `index.php` Einstiegspunktskript für Ihre Website oder [Store-Ansicht](https://glossary.magento.com/store-view) und fügen Sie Folgendes hinzu:

- Sie arbeiten an einer Entwicklungsmaschine (Laptop, virtuelle Maschine usw.)

   Möglicherweise sind zusätzliche Aufgaben erforderlich, um mehrere Websites in einer gehosteten Umgebung bereitzustellen. Weitere Informationen erhalten Sie von Ihrem Hosting-Provider.

   Für die Einrichtung von Adobe Commerce in der Cloud-Infrastruktur sind zusätzliche Aufgaben erforderlich. Nachdem Sie die in diesem Thema behandelten Aufgaben abgeschlossen haben, lesen Sie [Einrichten mehrerer Websites oder Stores](https://devdocs.magento.com/cloud/project/project-multi-sites.html) im _Commerce Cloud-Handbuch_.

- Sie verwenden einen virtuellen Host pro Website. Die Konfigurationsdatei des virtuellen Hosts lautet `/etc/httpd/httpd.conf`

   Verschiedene Versionen von Apache unter verschiedenen Betriebssystemen richten virtuelle Hosts unterschiedlich ein. Lesen Sie die [Apache-Dokumentation](https://httpd.apache.org/docs/2.4/vhosts) oder einem Netzwerkadministrator, wenn Sie nicht sicher sind, wie ein virtueller Host eingerichtet wird.

- Die Commerce-Software ist in `/var/www/html/magento2`
- Sie haben zwei andere Websites als die Standardwebsite:

   - `french.mysite.mg` mit Website-Code `french` und Store-Ansichtscode `fr`
   - `german.mysite.mg` mit Website-Code `german` und Store-Ansichtscode `de`

## Roadmap für die Einrichtung mehrerer Websites mit Apache

Das Einrichten mehrerer Stores umfasst die folgenden Aufgaben:

1. [Einrichten von Websites, Geschäften und Speichern von Ansichten](ms-admin.md) im Admin.
1. Erstellen einer [Apache Virtual Host](#step-2-create-apache-virtual-hosts) per Commerce-Website.

## Schritt 1: Erstellen von Websites, Geschäften und Speichern von Ansichten in der Admin-Konsole

Siehe [Einrichten mehrerer Websites, Stores und Speichern von Ansichten in der Admin-Konsole](ms-admin.md).

## Schritt 2: Erstellen von virtuellen Apache-Hosts

In diesem Abschnitt wird beschrieben, wie Werte für `MAGE_RUN_TYPE` und `MAGE_RUN_CODE` Verwenden der Apache-Servervariable `SetEnvIf` in einem virtuellen Host.

Weitere Informationen finden Sie unter `SetEnvIf`, siehe:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**So erstellen Sie virtuelle Apache-Hosts**:

1. Als Benutzer mit `root` -Berechtigungen, öffnen Sie die Konfigurationsdatei des virtuellen Hosts in einem Texteditor.

   Öffnen Sie beispielsweise `/etc/httpd/conf/httpd.conf`

1. Suchen Sie den Abschnitt, der mit `<VirtualHost *:80>`.
1. Erstellen Sie die folgenden virtuellen Hosts nach vorhandenen virtuellen Hosts:

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. Speichern Sie Ihre Änderungen in `httpd.conf` und beenden Sie den Texteditor.
1. Starten Sie Apache neu:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## Überprüfen der Site

Sofern kein DNS für die URLs Ihrer Stores eingerichtet ist, müssen Sie eine statische Route zum Host in Ihrem `hosts` Datei:

1. Betriebssystem suchen `hosts` -Datei.
1. Fügen Sie die statische Route im Format hinzu:

   ```conf
   <ip address> french.mysite.mg
   <ip address> german.mysite.mg
   ```

1. Rufen Sie eine der folgenden URLs in Ihrem Browser auf:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Möglicherweise sind zusätzliche Aufgaben erforderlich, um mehrere Websites in einer gehosteten Umgebung bereitzustellen. Weitere Informationen erhalten Sie von Ihrem Hosting-Provider.
>- Für die Einrichtung von Adobe Commerce in der Cloud-Infrastruktur sind zusätzliche Aufgaben erforderlich. see [Einrichten mehrerer Cloud-Websites oder -Stores](https://devdocs.magento.com/cloud/project/project-multi-sites.html) im _Commerce Cloud-Handbuch_.


### Fehlerbehebung

- Wenn Ihre französischen und deutschen Sites 404 s zurückgeben, Ihr Admin jedoch geladen wird, stellen Sie sicher, dass Sie [Schritt 6: Fügen Sie den Store-Code zur Basis-URL hinzu.](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Wenn alle URLs 404 s zurückgeben, stellen Sie sicher, dass Sie Ihren Webserver neu starten.
- Wenn der Administrator nicht ordnungsgemäß funktioniert, stellen Sie sicher, dass Sie Ihre virtuellen Hosts ordnungsgemäß eingerichtet haben.
