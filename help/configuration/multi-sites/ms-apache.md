---
title: Einrichten mehrerer Websites mit Apache
description: In diesem Tutorial erfahren Sie, wie Sie mehrere Websites mit Apache einrichten.
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Einrichten mehrerer Websites mit Apache

Wir gehen davon aus, dass

Kopieren Sie bei Bedarf das vorhandene Einstiegspunktskript `index.php` für Ihre Website- oder Store-Ansicht und fügen Sie Folgendes hinzu:

- Sie arbeiten an einer Entwicklungsmaschine (Laptop, virtuelle Maschine usw.)

  Möglicherweise sind zusätzliche Aufgaben erforderlich, um mehrere Websites in einer gehosteten Umgebung bereitzustellen. Wenden Sie sich diesbezüglich an Ihren Hosting-Provider.

  Für die Einrichtung von Adobe Commerce in der Cloud-Infrastruktur sind zusätzliche Aufgaben erforderlich. Nachdem Sie die in diesem Thema behandelten Aufgaben abgeschlossen haben, finden Sie weitere Informationen unter [Einrichten mehrerer Websites oder Stores](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) im Leitfaden _Commerce on Cloud Infrastructure_.

- Sie verwenden einen virtuellen Host pro Website. Die Konfigurationsdatei des virtuellen Hosts ist `/etc/httpd/httpd.conf`

  Verschiedene Versionen von Apache unter verschiedenen Betriebssystemen richten virtuelle Hosts unterschiedlich ein. Lesen Sie die [Apache-Dokumentation](https://httpd.apache.org/docs/2.4/vhosts) oder einen Netzwerkadministrator, wenn Sie nicht sicher sind, wie Sie einen virtuellen Host einrichten.

- Die Commerce-Software ist in `/var/www/html/magento2` installiert.
- Sie haben zwei andere Websites als die Standardwebsite:

   - `french.mysite.mg` mit Website-Code `french` und Store-Ansichtscode `fr`
   - `german.mysite.mg` mit Website-Code `german` und Store-Ansichtscode `de`

## Roadmap für die Einrichtung mehrerer Websites mit Apache

Das Einrichten mehrerer Stores umfasst die folgenden Aufgaben:

1. [ Richten Sie Websites, Stores und speichern Sie Ansichten](ms-admin.md) im Admin ein.
1. Erstellen Sie einen [Apache Virtual Host](#step-2-create-apache-virtual-hosts) pro Commerce-Website.

## Schritt 1: Erstellen von Websites, Geschäften und Speichern von Ansichten in der Admin-Konsole

Siehe [Einrichten mehrerer Websites, Stores und Speichern von Ansichten in der Admin-Konsole](ms-admin.md).

## Schritt 2: Erstellen von virtuellen Apache-Hosts

In diesem Abschnitt wird beschrieben, wie Sie Werte für `MAGE_RUN_TYPE` und `MAGE_RUN_CODE` mithilfe der Apache-Server-Variablen `SetEnvIf` in einem virtuellen Host festlegen.

Weitere Informationen zu `SetEnvIf` finden Sie unter:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**So erstellen Sie Apache Virtual Hosts**:

1. Als Benutzer mit `root` -Berechtigungen öffnen Sie die Konfigurationsdatei des virtuellen Hosts in einem Texteditor.

   Öffnen Sie beispielsweise `/etc/httpd/conf/httpd.conf`

1. Suchen Sie den Abschnitt, der mit `<VirtualHost *:80>` beginnt.
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

Sofern kein DNS für die URLs Ihrer Stores eingerichtet ist, müssen Sie in Ihrer `hosts` -Datei eine statische Route zum Host hinzufügen:

1. Suchen Sie die Datei des Betriebssystems `hosts` .
1. Fügen Sie die statische Route im Format hinzu:

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. Rufen Sie eine der folgenden URLs in Ihrem Browser auf:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Möglicherweise sind zusätzliche Aufgaben erforderlich, um mehrere Websites in einer gehosteten Umgebung bereitzustellen. Wenden Sie sich diesbezüglich an Ihren Hosting-Provider.
>- Weitere Aufgaben sind erforderlich, um Adobe Commerce in der Cloud-Infrastruktur einzurichten. Weitere Informationen finden Sie unter [Einrichten mehrerer Cloud-Websites oder -Stores](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) im Handbuch _Commerce on Cloud Infrastructure_.

### Fehlerbehebung

- Wenn Ihre französischen und deutschen Sites 404 s zurückgeben, Ihr Admin jedoch geladen wird, stellen Sie sicher, dass Sie [Schritt 6: Hinzufügen des Store-Codes zur Basis-URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url) abgeschlossen haben.
- Wenn alle URLs 404 s zurückgeben, stellen Sie sicher, dass Sie Ihren Webserver neu starten.
- Wenn der Administrator nicht ordnungsgemäß funktioniert, stellen Sie sicher, dass Sie Ihre virtuellen Hosts ordnungsgemäß eingerichtet haben.
