---
title: Eine Remote-Verbindung zur MySQL-Datenbank einrichten
description: Führen Sie diese Schritte aus, um eine Remote-Datenbankverbindung für lokale Installationen von Adobe Commerce zu konfigurieren.
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
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

Beim Ausführen `bin/magento setup:install`, verwenden Sie die Aurora-Informationen im `db-` -Felder:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

Die `db-host` Wert ist die Aurora-URL mit der `https://` und am Ende `:portnumber`  entfernt.

## Remote-Datenbankverbindung einrichten

>[!NOTE]
>
>Dies ist ein erweitertes Thema, das nur von einem erfahrenen Netzwerkadministrator oder Datenbankadministrator verwendet werden sollte. Sie müssen `root` Zugriff auf das Dateisystem und Sie müssen sich bei MySQL als `root`.

### Voraussetzungen

Bevor Sie beginnen, müssen Sie:

* [MySQL-Server installieren](mysql.md) auf dem Datenbankserver.
* [Erstellen einer Datenbankinstanz](mysql.md#configuring-the-database-instance) auf dem Datenbankserver.
* Installieren Sie den MySQL-Client auf Ihrem Adobe Commerce-Webknoten. Weitere Informationen finden Sie in der MySQL-Dokumentation .

### Hohe Verfügbarkeit

Verwenden Sie die folgenden Richtlinien, um Remote-Datenbankverbindungen zu konfigurieren, wenn Ihr Webserver oder Datenbankserver in Clustern zusammengefasst ist:

* Sie müssen für jeden Webserverknoten eine Verbindung konfigurieren.
* In der Regel konfigurieren Sie eine Datenbankverbindung zum Datenbank-Lastenausgleich. Das Datenbank-Clustering kann jedoch komplex sein und von Ihnen konfiguriert werden. Adobe gibt keine spezifischen Empfehlungen für das Datenbank-Clustering aus.

  Weitere Informationen finden Sie unter [MySQL-Dokumentation](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Beheben von Verbindungsproblemen

Wenn Sie Probleme beim Herstellen einer Verbindung zu einem der Hosts haben, pingen Sie zunächst den anderen Host, um sicherzustellen, dass er erreichbar ist. Möglicherweise müssen Sie Verbindungen von einem Host zum anderen zulassen, indem Sie Firewall- und SELinux-Regeln ändern (wenn Sie SELinux verwenden).

## Remote-Verbindung erstellen

So erstellen Sie eine Remote-Verbindung:

1. Auf Ihrem Datenbankserver als Benutzer mit `root` -Berechtigungen, öffnen Sie Ihre MySQL-Konfigurationsdatei.

   Geben Sie den folgenden Befehl ein, um ihn zu finden:

   ```bash
   mysql --help
   ```

   Der Speicherort wird in etwa wie folgt angezeigt:

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >Auf Ubuntu 16 lautet der Pfad normalerweise `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Suchen Sie die Konfigurationsdatei nach `bind-address`.

   Falls vorhanden, ändern Sie den Wert wie folgt.

   Wenn sie nicht vorhanden ist, fügen Sie sie dem `[mysqld]` Abschnitt.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Siehe [MySQL-Dokumentation](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), insbesondere wenn Sie über einen Webserver mit Clustern verfügen.

1. Speichern Sie Ihre Änderungen in der Konfigurationsdatei und beenden Sie den Texteditor.
1. Starten Sie den MySQL-Dienst neu:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`

   >[!NOTE]
   >
   >Wenn MySQL nicht gestartet werden kann, suchen Sie in syslog nach der Quelle des Problems. Beheben Sie das Problem mit [MySQL-Dokumentation](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) oder einer anderen maßgeblichen Quelle.

## Zugriff auf einen Datenbankbenutzer gewähren

Damit Ihr Webknoten eine Verbindung zum Datenbankserver herstellen kann, müssen Sie einem Webknotendatenbankbenutzer Zugriff auf die Datenbank auf dem Remote-Server gewähren.

Dieses Beispiel gewährt dem `root` Datenbankbenutzer vollen Zugriff auf die Datenbank auf dem Remote-Host.

So gewähren Sie Zugriff auf einen Datenbankbenutzer:

1. Melden Sie sich beim Datenbankserver an.
1. Verbindung zur MySQL-Datenbank als `root` Benutzer.
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

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Wenn Ihr Webserver in einem Cluster gespeichert ist, geben Sie den Befehl auf jedem Webserver-Host ein.

## Installieren des Adobe Commerce

Bei der Installation von Adobe Commerce müssen Sie Folgendes angeben:

* Die Basis-URL (auch als *Store-Adresse*) gibt den Hostnamen oder die IP-Adresse der *Webknoten*
* Der Datenbankhost ist der *Remote-Datenbankserver* IP-Adresse (oder Lastenausgleich, wenn der Datenbankserver im Cluster ist)
* Der Benutzername der Datenbank ist *lokaler Webknoten* Datenbankbenutzer, dem Sie Zugriff gewährt haben
* Das Datenbankkennwort ist das Kennwort des lokalen Webknotenbenutzers
* Datenbankname ist der Name der Datenbank auf dem Remote-Server.
