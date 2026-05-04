---
title: Voraussetzungen für die lokale Installation
description: Erfahren Sie mehr über die Softwareabhängigkeiten, die für lokale Installationen von Adobe Commerce erforderlich sind.
exl-id: dd4694e7-5437-440c-bb67-804ae36149de
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 1%

---

# Voraussetzungen für die lokale Installation

Vor der Installation von Adobe Commerce müssen Sie folgende Schritte ausführen:

* Richten Sie einen oder mehrere Hosts ein, die die [Systemanforderungen](../system-requirements.md) erfüllen, die auf der Registerkarte *Commerce On-Premise* aufgeführt sind.
* Wenn Sie mehr als einen Webknoten mit Lastenausgleich einrichten, richten Sie diesen Teil Ihres Systems ein und testen Sie ihn (_)_ Sie die Anwendung.
* Stellen Sie sicher, dass Sie Ihr gesamtes System an verschiedenen Stellen während der Installation sichern können, damit Sie es bei Problemen zurücksetzen können.

>[!NOTE]
>
>Wir gehen davon aus, dass Sie die Adobe Commerce in einer **Entwicklungsumgebung** installieren, dass Sie einen Root-Benutzerzugriff auf den Computer haben **und** dass der Computer nicht hochsicher sein muss. Wenn Sie einen sichereren Computer einrichten, empfehlen wir dringend, sich an einen Netzwerkadministrator zu wenden, um weitere Unterstützung zu erhalten.

Es wird dringend empfohlen, die Betriebssystemsoftware zu aktualisieren und zu aktualisieren. Diese Upgrades können Sicherheits- und Softwarekorrekturen bereitstellen, die zukünftige Probleme verhindern können. Wissen Sie nicht, was das bedeutet? Schauen Sie sich unsere [Installationsübersichtsseite](../overview.md) an.

Geben Sie die folgenden Befehle als Benutzer mit `root` Berechtigungen ein:

* Ubuntu

  ```shell
  apt-get update
  ```

  ```shell
  apt-get upgrade
  ```

* CentOS

  ```shell
  yum -y update
  ```

  ```shell
  yum -y upgrade
  ```

## Voraussetzungsprüfung

Geben Sie die folgenden Befehle ein, um Ihr System auf Voraussetzungen zu überprüfen:

### Apache

CentOS: `httpd -v`

Ubuntu: `apache2 -v`

Adobe Commerce unterstützt Apache Version 2.4, da das folgende Ergebnis anzeigt:

```text
Server version: Apache/2.4.0 (Unix)
Server built:   Jul 23 2017 14:17:29
```

Informationen zum Installieren oder Aktualisieren von Apache finden Sie unter [Apache](web-server/apache.md).

### PHP

Auf der Registerkarte *Commerce On-Premises* in [Systemanforderungen](../system-requirements.md) finden Sie unterstützte Versionen von PHP und [PHP](../system-requirements.md#php-settings) für PHP-Anforderungen.

### MySQL

Vergewissern Sie sich, dass Sie über eine kompatible MySQL-Version für die Adobe Commerce-Version verfügen, die Sie installieren. Unterstützte Versionen finden Sie auf der ** Commerce On-Premise[ in ](../system-requirements.md)Systemanforderungen.

```shell
mysql -u <database root user or database owner name> -p
```

Beispiel:

```shell
mysql -u magento -p
```

In der Befehlsausgabe gibt die `Server version` die Version an, die Sie ausführen. Vergewissern Sie sich, dass es mit einer Version übereinstimmt, die für die Adobe Commerce-Version unterstützt wird, die Sie installieren.

```text
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 871
Server version: <supported MySQL version> MySQL Community Server (GPL)

Copyright (c) 2000, 2019, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
```

Geben Sie `help` oder `\h` ein, um Hilfe zu erhalten. Geben Sie `\c` ein, um die aktuelle Eingabeanweisung zu löschen.

Geben Sie `exit` an der `mysql>` ein, um den Vorgang zu beenden.

Informationen zum Installieren oder Aktualisieren von MySQL finden Sie unter [MySQL](database/mysql.md).

### Suchmaschine

So überprüfen Sie Ihre OpenSearch-Installation:

```shell
curl -XGET '<opensearch-hostname>:<opensearch-port>'
```

So überprüfen Sie Ihre Elasticsearch-Installation:

```shell
curl -XGET '<elasticsearch-hostname>:<elasticsearch-port>'
```

Beispiel:

```shell
curl -XGET 'localhost:9200'
```

```json
{
  "name" : "Z0S2B05",
  "cluster_name" : "elasticsearch_myname",
  "cluster_uuid" : "V-kpikRJQHudN-Wzdt-IrQ",
  "version" : {
    "number" : "6.8.7",
    "build_flavor" : "oss",
    "build_type" : "tar",
    "build_hash" : "c63e621",
    "build_date" : "2020-02-26T14:38:01.193138Z",
    "build_snapshot" : false,
    "lucene_version" : "7.7.2",
    "minimum_wire_compatibility_version" : "5.6.0",
    "minimum_index_compatibility_version" : "5.0.0"
  },
  "tagline" : "You Know, for Search"
```
