---
title: Einrichten mehrerer Websites mit Apache
description: In diesem Tutorial können Sie mehrere Websites mit Apache einrichten.
exl-id: 4c6890b3-f15a-46f2-a3e8-6f2a9b57a6ad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Einrichten mehrerer Websites mit Apache

Wir gehen davon aus, dass

Kopieren Sie ggf. das vorhandene Einstiegspunktskript für `index.php` Website- oder Store-Ansicht und fügen Sie Folgendes hinzu:

- Sie arbeiten an einer Entwicklungsmaschine (Laptop, virtuelle Maschine usw.),

  Möglicherweise sind zusätzliche Aufgaben erforderlich, um mehrere Websites in einer gehosteten Umgebung bereitzustellen. Weitere Informationen erhalten Sie bei Ihrem Hosting-Anbieter.

  Zum Einrichten von Adobe Commerce in der Cloud-Infrastruktur sind zusätzliche Aufgaben erforderlich. Nachdem Sie die in diesem Thema besprochenen Aufgaben abgeschlossen haben, finden Sie weitere Informationen unter [Einrichten mehrerer Websites oder Stores](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=de) im Handbuch zu _Commerce in Cloud-Infrastruktur_.

- Pro Website verwenden Sie einen virtuellen Host. Die Konfigurationsdatei für den virtuellen Host ist `/etc/httpd/httpd.conf`

  Verschiedene Versionen von Apache auf verschiedenen Betriebssystemen richten virtuelle Hosts unterschiedlich ein. Konsultieren Sie die [Apache-Dokumentation](https://httpd.apache.org/docs/2.4/vhosts) oder einen Netzwerkadministrator, wenn Sie sich nicht sicher sind, wie ein virtueller Host eingerichtet werden soll.

- Die Commerce-Software ist in `/var/www/html/magento2` installiert
- Neben der Standardeinstellung gibt es zwei weitere Websites:

   - `french.mysite.mg` mit Website-Code-`french` und Store-Ansicht-Code-`fr`
   - `german.mysite.mg` mit Website-Code-`german` und Store-Ansicht-Code-`de`

## Roadmap für das Einrichten mehrerer Websites mit Apache

Das Einrichten mehrerer Stores umfasst die folgenden Aufgaben:

1. [Einrichten von Websites, Stores und Store-Ansichten](ms-admin.md) im Admin-Bereich.
1. Erstellen Sie einen [virtuellen Apache-Host](#step-2-create-apache-virtual-hosts) pro Commerce-Website.

## Schritt 1: Erstellen von Websites, Stores und Store-Ansichten im Admin-Bereich

Siehe [Einrichten mehrerer Websites, Stores und Store-Ansichten im Admin](ms-admin.md).

## Schritt 2: Apache Virtual Hosts erstellen

In diesem Abschnitt wird beschrieben, wie Sie Werte für `MAGE_RUN_TYPE` und `MAGE_RUN_CODE` mithilfe der Apache-Server-Variable `SetEnvIf` in einem virtuellen Host festlegen.

Weitere Informationen zu `SetEnvIf` finden Sie unter:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**So erstellen Sie virtuelle Apache-Hosts**:

1. Wenn Sie ein Benutzer mit `root` Berechtigungen sind, öffnen Sie die Konfigurationsdatei für den virtuellen Host in einem Texteditor.

   Beispiel: `/etc/httpd/conf/httpd.conf` öffnen

1. Suchen Sie den Abschnitt, der mit `<VirtualHost *:80>` beginnt.
1. Erstellen Sie die folgenden virtuellen Hosts nach allen vorhandenen virtuellen Hosts:

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
1. Apache neu starten:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

## Überprüfen der Site

Sofern Sie kein DNS für die URLs Ihrer Stores eingerichtet haben, müssen Sie eine statische Route zum Host in Ihrer `hosts`-Datei hinzufügen:

1. Suchen Sie die `hosts` Ihres Betriebssystems.
1. Fügen Sie die statische Route im folgenden Format hinzu:

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
>- Möglicherweise sind zusätzliche Aufgaben erforderlich, um mehrere Websites in einer gehosteten Umgebung bereitzustellen. Weitere Informationen erhalten Sie bei Ihrem Hosting-Anbieter.
>- Zum Einrichten von Adobe Commerce in der Cloud-Infrastruktur sind zusätzliche Aufgaben erforderlich. Siehe [Einrichten mehrerer Cloud-Websites oder -Stores](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=de) im Handbuch zu _Commerce in der Cloud-Infrastruktur_.

### Fehlerbehebung

- Wenn Ihre französischen und deutschen Websites 404 s zurückgeben, aber Ihr Administrator geladen wird, stellen Sie sicher, dass Sie [ abgeschlossen haben (Schritt 6: Hinzufügen des Store-Codes zur Basis-URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Wenn alle URLs den Wert 404 zurückgeben, stellen Sie sicher, dass Sie Ihren Webserver neu gestartet haben.
- Wenn der Administrator nicht ordnungsgemäß funktioniert, stellen Sie sicher, dass Sie die virtuellen Hosts ordnungsgemäß einrichten.
