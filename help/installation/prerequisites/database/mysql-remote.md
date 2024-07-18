---
title: Eine Remote-Verbindung zur MySQL-Datenbank einrichten
description: Führen Sie diese Schritte aus, um eine Remote-Datenbankverbindung für lokale Installationen von Adobe Commerce zu konfigurieren.
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# Eine Remote-Verbindung zur MySQL-Datenbank einrichten

Manchmal möchten Sie die Datenbank auf einem separaten Server hosten, anstatt den Datenbankserver und den Webserver auf demselben Computer auszuführen.

Adobe bietet eine Möglichkeit, eine Verbindung zu einem MySQL-Server auf einem anderen Computer herzustellen. Ab Adobe Commerce 2.4.3 können Sie die Anwendung auch so konfigurieren, dass eine Amazon Web Services (AWS) Aurora-Datenbank ohne Codeänderungen verwendet wird.

Aurora ist ein leistungsstarker, vollständig kompatibler MySQL-Server, der auf AWS gehostet wird.

## Herstellen einer Verbindung zu einer AWS Aurora-Datenbank

Die Verwendung von Aurora als Datenbank ist so einfach wie die Angabe der Datenbank in der regulären Adobe Commerce-Setup-Konfiguration mithilfe des standardmäßigen Datenbank-Connectors.

Verwenden Sie beim Ausführen von `bin/magento setup:install` die Aurora-Informationen in den `db-` -Feldern:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

Der Wert `db-host` ist die Aurora-URL, wobei die `https://` und die nachfolgende `:portnumber` entfernt sind.

## Remote-Datenbankverbindung einrichten

>[!NOTE]
>
>Dies ist ein erweitertes Thema, das nur von einem erfahrenen Netzwerkadministrator oder Datenbankadministrator verwendet werden sollte. Sie benötigen `root` Zugriff auf das Dateisystem und müssen sich als `root` bei MySQL anmelden können.

### Voraussetzungen

Bevor Sie beginnen, müssen Sie:

* [Installieren Sie den MySQL-Server](mysql.md) auf dem Datenbankserver.
* [Erstellen Sie eine Datenbankinstanz](mysql.md#configuring-the-database-instance) auf dem Datenbankserver.
* Installieren Sie den MySQL-Client auf Ihrem Adobe Commerce-Webknoten. Weitere Informationen finden Sie in der MySQL-Dokumentation .

### Hohe Verfügbarkeit

Verwenden Sie die folgenden Richtlinien, um Remote-Datenbankverbindungen zu konfigurieren, wenn Ihr Webserver oder Datenbankserver in Clustern zusammengefasst ist:

* Sie müssen für jeden Webserverknoten eine Verbindung konfigurieren.
* In der Regel konfigurieren Sie eine Datenbankverbindung zum Datenbank-Lastenausgleich. Das Datenbank-Clustering kann jedoch komplex sein und von Ihnen konfiguriert werden. Adobe gibt keine spezifischen Empfehlungen für das Datenbank-Clustering aus.

  Weitere Informationen finden Sie in der [MySQL-Dokumentation](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Beheben von Verbindungsproblemen

Wenn Sie Probleme beim Herstellen einer Verbindung zu einem der Hosts haben, pingen Sie zunächst den anderen Host, um sicherzustellen, dass er erreichbar ist. Möglicherweise müssen Sie Verbindungen von einem Host zum anderen zulassen, indem Sie Firewall- und SELinux-Regeln ändern (wenn Sie SELinux verwenden).

## Remote-Verbindung erstellen

So erstellen Sie eine Remote-Verbindung:

1. Öffnen Sie auf Ihrem Datenbankserver als Benutzer mit `root` -Berechtigungen Ihre MySQL-Konfigurationsdatei.

   Geben Sie den folgenden Befehl ein, um ihn zu finden:

   ```bash
   mysql --help
   ```

   Der Speicherort wird in etwa wie folgt angezeigt:

   ```
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >Auf Ubuntu 16 ist der Pfad normalerweise `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Suchen Sie in der Konfigurationsdatei nach &quot;`bind-address`&quot;.

   Falls vorhanden, ändern Sie den Wert wie folgt.

   Wenn es nicht vorhanden ist, fügen Sie es zum Abschnitt `[mysqld]` hinzu.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Weitere Informationen finden Sie in der [MySQL-Dokumentation](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), insbesondere wenn Sie über einen Webserver mit Clustern verfügen.

1. Speichern Sie Ihre Änderungen in der Konfigurationsdatei und beenden Sie den Texteditor.
1. Starten Sie den MySQL-Dienst neu:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`

   >[!NOTE]
   >
   >Wenn MySQL nicht gestartet werden kann, suchen Sie in syslog nach der Quelle des Problems. Beheben Sie das Problem mit der [MySQL-Dokumentation](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) oder einer anderen autorisierten Quelle.

## Zugriff auf einen Datenbankbenutzer gewähren

Damit Ihr Webknoten eine Verbindung zum Datenbankserver herstellen kann, müssen Sie einem Webknotendatenbankbenutzer Zugriff auf die Datenbank auf dem Remote-Server gewähren.

Mit diesem Beispiel wird dem Datenbankbenutzer `root` uneingeschränkter Zugriff auf die Datenbank auf dem Remote-Host gewährt.

So gewähren Sie Zugriff auf einen Datenbankbenutzer:

1. Melden Sie sich beim Datenbankserver an.
1. Stellen Sie eine Verbindung zur MySQL-Datenbank als `root` Benutzer her.
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

## Überprüfen des Datenbankzugriffs

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

Wenn Ihr Webserver in einem Cluster gespeichert ist, geben Sie den Befehl auf jedem Webserver-Host ein.

## Installieren des Adobe Commerce

Bei der Installation von Adobe Commerce müssen Sie Folgendes angeben:

* Die Basis-URL (auch als *Speicheradresse* bezeichnet) gibt den Hostnamen oder die IP-Adresse des *Webknotens* an
* Der Datenbankhost ist die IP-Adresse des *Remote-Datenbankservers* (oder des Lastenausgleichs, wenn der Datenbankserver geclustert ist).
* Der Datenbankbenutzername ist der Datenbankbenutzer, auf den Sie Zugriff gewährt haben.**
* Das Datenbankkennwort ist das Kennwort des lokalen Webknotenbenutzers
* Datenbankname ist der Name der Datenbank auf dem Remote-Server.
