---
title: Einrichten einer Remote-MySQL-Datenbankverbindung
description: Führen Sie die folgenden Schritte aus, um eine Remote-Datenbankverbindung für lokale Installationen von Adobe Commerce zu konfigurieren.
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# Einrichten einer Remote-MySQL-Datenbankverbindung

Manchmal empfiehlt es sich, die Datenbank auf einem separaten Server zu hosten, anstatt den Datenbankserver und den Webserver auf demselben Computer auszuführen.

Adobe bietet die Möglichkeit, eine Verbindung zu einem MySQL-Server auf einem anderen Computer herzustellen. Ab Adobe Commerce 2.4.3 können Sie die Anwendung auch so konfigurieren, dass sie eine Amazon Web Services (AWS) Aurora-Datenbank ohne Code-Änderungen verwendet.

Aurora ist ein leistungsstarker, vollständig konformer MySQL-Server, der auf AWS gehostet wird.

## Herstellen einer Verbindung zu einer AWS Aurora-Datenbank

Die Verwendung von Aurora als Datenbank ist so einfach wie die Angabe der Datenbank in der regulären Adobe Commerce-Setup-Konfiguration unter Verwendung des standardmäßigen Datenbank-Connectors.

Verwenden Sie beim Ausführen von `bin/magento setup:install` die Aurora-Informationen in den `db-`:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

Der `db-host` ist die Aurora-URL, wobei die `https://` und die nachfolgenden `:portnumber` entfernt werden.

## Einrichten einer Remote-Datenbankverbindung

>[!NOTE]
>
>Dies ist ein fortgeschrittenes Thema, das nur von erfahrenen Netzwerk- oder Datenbankadministratoren verwendet werden sollte. Sie müssen `root` Zugriff auf das Dateisystem haben und sich `root` bei MySQL anmelden können.

### Voraussetzungen

Bevor Sie beginnen, müssen Sie Folgendes tun:

* [Installieren Sie MySQL Server](mysql.md) auf dem Datenbankserver.
* [Erstellen einer Datenbankinstanz](mysql.md#configuring-the-database-instance) auf dem Datenbankserver
* Installieren Sie den MySQL-Client auf Ihrem Adobe Commerce-Webknoten. Weitere Informationen finden Sie in der MySQL-Dokumentation .

### Hohe Verfügbarkeit

Verwenden Sie die folgenden Richtlinien, um Remotedatenbankverbindungen zu konfigurieren, wenn Ihr Webserver oder Datenbankserver in einem Cluster zusammengefasst sind:

* Sie müssen für jeden Webserverknoten eine Verbindung konfigurieren.
* Normalerweise konfigurieren Sie eine Datenbankverbindung zum Datenbank-Load-Balancer. Das Datenbank-Clustering kann jedoch komplex sein und die Konfiguration liegt bei Ihnen. Adobe gibt keine spezifischen Empfehlungen für das Datenbank-Clustering.

  Weitere Informationen finden Sie unter [MySQL-](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Beheben von Verbindungsproblemen

Wenn Sie Probleme bei der Verbindung mit einem der Hosts haben, pingen Sie zunächst den anderen Host, um sicherzustellen, dass er erreichbar ist. Möglicherweise müssen Sie Verbindungen von einem Host zu einem anderen zulassen, indem Sie Firewall- und SELinux-Regeln ändern (wenn Sie SELinux verwenden).

## Remote-Verbindung erstellen

So erstellen Sie eine Remote-Verbindung:

1. Öffnen Sie auf Ihrem Datenbankserver als Benutzer mit `root` die MySQL-Konfigurationsdatei.

   Geben Sie den folgenden Befehl ein, um es zu finden:

   ```bash
   mysql --help
   ```

   Der Speicherort wird ähnlich wie der folgende angezeigt:

   ```
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >Auf Ubuntu 16 ist der Pfad normalerweise `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Durchsuchen Sie die Konfigurationsdatei nach `bind-address`.

   Falls vorhanden, ändern Sie den Wert wie folgt.

   Wenn es nicht vorhanden ist, fügen Sie es zum Abschnitt `[mysqld]` hinzu.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Siehe [MySQL-Dokumentation](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), insbesondere bei einem geclusterten Webserver.

1. Speichern Sie Ihre Änderungen in der Konfigurationsdatei und beenden Sie den Texteditor.
1. Starten Sie den MySQL-Dienst neu:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`

   >[!NOTE]
   >
   >Wenn MySQL nicht gestartet werden kann, suchen Sie in syslog nach der Ursache des Problems. Lösen Sie das Problem mithilfe von [MySQL-Dokumentation](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) oder einer anderen autorisierenden Quelle.

## Gewähren des Zugriffs für einen Datenbankbenutzer

Damit Ihr Webknoten eine Verbindung zum Datenbankserver herstellen kann, müssen Sie einem Datenbankbenutzer des Webknotens Zugriff auf die Datenbank auf dem Remoteserver gewähren.

In diesem Beispiel erhält der `root` Datenbankbenutzer vollen Zugriff auf die Datenbank auf dem Remote-Host.

So gewähren Sie einem Datenbankbenutzer Zugriff:

1. Melden Sie sich beim Datenbankserver an.
1. Verbinden Sie sich als `root` mit der MySQL-Datenbank.
1. Geben Sie den folgenden Befehl ein:

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   Beispiel:

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >Wenn Ihr Webserver geclustert ist, geben Sie auf jedem Webserver denselben Befehl ein. Sie müssen für jeden Webserver denselben Benutzernamen verwenden.

## Datenbankzugriff überprüfen

Geben Sie auf Ihrem Webknotenhost den folgenden Befehl ein, um zu überprüfen, ob die Verbindung funktioniert:

```bash
mysql -u <local database username> -h <database server ip address> -p
```

Wenn der MySQL-Monitor wie folgt angezeigt wird, ist die Datenbank für Adobe Commerce bereit:

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Wenn Ihr Webserver geclustert ist, geben Sie den Befehl auf jedem Webserverhost ein.

## Installieren von Adobe Commerce

Bei der Installation von Adobe Commerce müssen Sie Folgendes angeben:

* Die Basis-URL (auch als *Store-Adresse* bezeichnet) gibt den Host-Namen oder die IP-Adresse des *Web-Knotens*
* Der Datenbank-Host ist *Remote-Datenbankserver* IP-Adresse (oder Lastenausgleich, wenn der Datenbank-Server in einem Cluster läuft)
* Der Datenbankbenutzername ist der Datenbankbenutzer *lokaler Webknoten*, auf den Sie Zugriff haben
* Das Datenbankkennwort ist das Kennwort des lokalen Webknotenbenutzers.
* Datenbankname ist der Name der Datenbank auf dem Remote-Server
