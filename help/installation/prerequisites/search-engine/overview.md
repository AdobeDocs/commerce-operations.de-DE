---
title: Voraussetzungen für Suchmaschinen
description: Führen Sie diese Schritte aus, um unterstützte Suchmaschinensoftware für lokale Installationen von Adobe Commerce zu installieren und zu konfigurieren.
feature: Install, Search
exl-id: 44ea638a-7200-4269-be1b-b0851de2c4f4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Voraussetzungen für Suchmaschinen

Ab Adobe Commerce 2.4 müssen alle Installationen so konfiguriert sein, dass [Elasticsearch](https://www.elastic.co) oder [OpenSearch](https://opensearch.org/) als Lösung für die Katalogsuche verwendet wird.

>[!NOTE]
>
>OpenSearch-Unterstützung wurde in 2.4.4 hinzugefügt. OpenSearch ist eine kompatible Form of Elasticsearch. Alle Anweisungen zum Konfigurieren von Elasticsearch 7 gelten für OpenSearch. [Migration von Elasticsearch zu OpenSearch](../../../upgrade/prepare/opensearch-migration.md) bietet Anleitungen zum Wechsel zu OpenSearch.

## Unterstützte Versionen

Vor der Installation von Adobe Commerce 2.4.4 und höher müssen Sie entweder Elasticsearch oder OpenSearch installieren und konfigurieren.

Spezifische Versionsinformationen finden [ in den ](../../system-requirements.md)Systemanforderungen“.

## Empfohlene Konfiguration

Wir empfehlen Folgendes:

* [Konfigurieren von nginx für Ihre Suchmaschine](configure-nginx.md)
* [Konfigurieren von Apache für Ihre Suchmaschine](configure-apache.md)

## Einbauort

Bei den folgenden Aufgaben wird davon ausgegangen, dass Sie Ihr System gemäß der folgenden Abbildung konfiguriert haben:

![Suchmaschinendiagramm](../../../assets/installation/search-engine-config.svg)

Das vorhergehende Diagramm zeigt:

* Die Commerce-Anwendung und die Suchmaschine werden auf verschiedenen Hosts installiert.

  Für die Ausführung auf separaten Hosts ist ein Proxy erforderlich. (Das Clustern der Suchmaschine sprengt den Rahmen dieses Handbuchs, weitere Informationen finden Sie jedoch in der Dokumentation zum [Elasticsearch-Clustering](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* Jeder Host verfügt über einen eigenen Webserver. Die Webserver müssen nicht identisch sein.

  Beispielsweise kann das Commerce-Programm Apache ausführen und die Suchmaschine nginx.

* Beide Webserver verwenden Transport Layer Security (TLS).

  Die Einrichtung von TLS sprengt den Rahmen unserer Dokumentation.

Suchanfragen werden wie folgt verarbeitet:

1. Eine Suchanfrage eines Benutzers wird vom Commerce-Webserver empfangen, der sie an den Suchmaschinenserver weiterleitet.

   Sie konfigurieren die Suchmaschine so, dass sie eine Verbindung zum Host und Port des Proxys herstellt. Wir empfehlen den SSL-Port des Webservers (standardmäßig 443).

1. Der Suchmaschinen-Webserver (der auf Port 443 wartet) leitet die Anfrage an den Suchmaschinenserver weiter (standardmäßig lauscht er auf Port 9200).

1. Der Zugriff auf die Suchmaschine ist außerdem durch die HTTP-Standardauthentifizierung geschützt. Damit eine Anfrage die Suchmaschine erreichen kann, muss sie über SSL gesendet werden *und* einen gültigen Benutzernamen und ein gültiges Kennwort angeben.

1. Die Suchmaschine verarbeitet die Anfrage.

1. Die Kommunikation wird auf derselben Route zurückgegeben, wobei der Elasticsearch-Webserver als sicherer Reverse-Proxy fungiert.

## Voraussetzungen

Die in diesem Abschnitt besprochenen Aufgaben erfordern Folgendes:

* [Firewall und SELinux](#firewall-and-selinux)
* [Installieren des Java Software Development Kit (JDK)](#install-the-java-software-development-kit)
* [Installieren der Suchmaschine](#install-the-search-engine)
* [Upgrade von Elasticsearch](#upgrading-elasticsearch)

### Firewall und SELinux

Sicherheitsbezogene Software (iptables, SELinux, AppArmor) kann standardmäßig so konfiguriert werden, dass sie die Kommunikation zwischen Subsystemen blockiert. Es kann eine gute Idee sein, sie zu überprüfen, wenn es Probleme gibt.

#### Regeln für iptables und SELinux einrichten

Informationen zum Einrichten von Regeln für die Kommunikation mit der Firewall oder SELinux aktiviert, finden Sie in den folgenden Ressourcen:

* [iptables - Anleitung](https://help.ubuntu.com/community/IptablesHowTo)
* [Bearbeiten von iptables-Regeln (Fedora-Projekt)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [Einführung in SELinux (CentOS.org)](https://www.centos.org)
* [SELinux-Anleitungswiki (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Installieren des Java Software Development Kits

Um festzustellen, ob Java bereits installiert ist, geben Sie den folgenden Befehl ein:

```bash
java -version
```

Wenn die Meldung `java: command not found` angezeigt wird, müssen Sie die Java-SDK wie im nächsten Abschnitt beschrieben installieren.

Siehe einen der folgenden Abschnitte:

* [Installieren des neuesten JDK auf CentOS](#install-the-jdk-on-centos)
* [Installieren des neuesten JDK auf Ubuntu](#install-the-jdk-on-ubuntu)

#### Installieren des JDK auf CentOS

Siehe dieses [Tutorial zum digitalen Ozean](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

Stellen Sie sicher, dass Sie das JDK und *nicht* JRE installieren.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java Version 8 ist möglicherweise nicht für alle Betriebssysteme verfügbar. Sie können beispielsweise [die Liste der verfügbaren Pakete nach Ubuntu durchsuchen](https://packages.ubuntu.com/).

#### Installieren des JDK auf Ubuntu

Um JDK 1.8 auf Ubuntu zu installieren, geben Sie die folgenden Befehle als Benutzer mit `root` ein:

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

Weitere Optionen finden Sie in der [Oracle-Dokumentation](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### Installieren der Suchmaschine

Befolgen Sie [Elasticsearch installieren](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) oder [Installieren und konfigurieren Sie OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) für Ihre plattformspezifischen Schritte.

Um sicherzustellen, dass das Elasticsearch funktioniert, geben Sie den folgenden Befehl auf dem Server ein, auf dem es ausgeführt wird:

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

Es wird eine Meldung ähnlich der folgenden angezeigt:

```
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

Um zu überprüfen, ob OpenSearch funktioniert, geben Sie die folgenden Befehle ein:

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## Upgrade von Elasticsearch

Unter [Elasticsearch aktualisieren](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) finden Sie vollständige Anweisungen zum Sichern Ihrer Daten, Erkennen potenzieller Migrationsprobleme und Testen von Upgrades vor der Bereitstellung in der Produktion. Abhängig von Ihrer aktuellen Version des Elasticsearchs kann ein vollständiger Neustart des Clusters erforderlich sein oder nicht.

Elasticsearch erfordert JDK 1.8 oder höher. Unter [Installieren des Java Software Development Kit](#install-the-java-software-development-kit) können Sie überprüfen, welche Version von JDK installiert ist.

## Zusätzliche Ressourcen

Weitere Informationen finden Sie in der Dokumentation [&#128279;](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html)Elasticsearch&quot; oder [OpenSearch](https://opensearch.org/docs/latest/).
