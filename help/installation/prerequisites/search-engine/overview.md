---
title: Voraussetzungen für Suchmaschinen
description: Führen Sie diese Schritte aus, um unterstützte Suchmaschinensoftware für lokale Installationen von Adobe Commerce und Magento Open Source zu installieren und zu konfigurieren.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---


# Voraussetzungen für Suchmaschinen

Ab Adobe Commerce und Magento Open Source 2.4 müssen alle Installationen für die Verwendung von [Elasticsearch](https://www.elastic.co) oder [OpenSearch](https://opensearch.org/) als [Katalog](https://glossary.magento.com/catalog) Suchlösung.

>[!NOTE]
>
>OpenSearch-Unterstützung wurde in Version 2.4.4 hinzugefügt. OpenSearch ist eine kompatible Abspaltung von Elasticsearch. Alle Anweisungen zum Konfigurieren von Elasticsearch 7 gelten für OpenSearch. [Migration von Elasticsearch zu OpenSearch](../../../upgrade/prepare/opensearch-migration.md) bietet Anleitungen zum Wechseln zu OpenSearch.

## Unterstützte Versionen

Sie müssen entweder Elasticsearch oder OpenSearch installieren und konfigurieren, bevor Sie Adobe Commerce oder Magento Open Source 2.4.4 installieren.

Siehe Abschnitt [Systemanforderungen](../../system-requirements.md) für spezifische Versionsinformationen.

## Empfohlene Konfiguration

Wir empfehlen Folgendes:

* [Konfigurieren von nginx für Ihre Suchmaschine](configure-nginx.md)
* [Konfigurieren von Apache für Ihre Suchmaschine](configure-apache.md)

## Installationsspeicherort

Bei den folgenden Aufgaben wird davon ausgegangen, dass Sie Ihr System gemäß folgendem Diagramm konfiguriert haben:

![Suchmaschinendiagramm](../../../assets/installation/search-engine-config.svg)

Das vorhergehende Diagramm zeigt Folgendes:

* Die Commerce-Anwendung und die Suchmaschine werden auf verschiedenen Hosts installiert.

   Für das Ausführen auf separaten Hosts muss die Proxy-Funktion ausgeführt werden. (Das Clustering der Suchmaschine geht über den Rahmen dieses Handbuchs hinaus, Sie finden jedoch weitere Informationen im Abschnitt [Dokumentation zu Elasticsearch-Clustering](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).

* Jeder Host verfügt über einen eigenen Webserver. die Webserver müssen nicht identisch sein.

   Beispielsweise kann die Commerce-Anwendung Apache ausführen und die Suchmaschine nginx ausführen.

* Beide Webserver verwenden Transport Layer Security (TLS).

   Die Einrichtung von TLS geht über den Rahmen unserer Dokumentation hinaus.

Suchanforderungen werden wie folgt verarbeitet:

1. Eine Suchanfrage eines Benutzers wird vom Commerce-Webserver empfangen, der sie an den Suchmaschinenserver weiterleitet.

   Sie konfigurieren die Suchmaschine so, dass eine Verbindung zum Host und Port des Proxys hergestellt wird. Wir empfehlen den SSL-Anschluss des Webservers (standardmäßig 443).

1. Der Webserver der Suchmaschine (Listening auf Port 443) sendet die Anforderung an den Suchmaschinenserver (standardmäßig wird Port 9200 überwacht).

1. Der Zugriff auf die Suchmaschine wird durch die HTTP Basic-Authentifizierung weiter geschützt. Eine Anfrage an die Suchmaschine muss über SSL gesendet werden *und* Geben Sie einen gültigen Benutzernamen und ein gültiges Kennwort ein.

1. Die Suchmaschine verarbeitet die Anforderung.

1. Die Kommunikation erfolgt entlang derselben Route, wobei der Elasticsearch-Webserver als sicherer Reverse-Proxy fungiert.

## Voraussetzungen

Die in diesem Abschnitt behandelten Aufgaben erfordern Folgendes:

* [Firewall und SELinux](#firewall-and-selinux)
* [Java Software Development Kit (JDK) installieren](#install-the-java-software-development-kit)
* [Suchmaschine installieren](#install-the-search-engine)
* [Upgrade von Elasticsearch](#upgrading-elasticsearch)

### Firewall und SELinux

Sicherheitsbezogene Software (iptables, SELinux, AppArmor) kann standardmäßig konfiguriert werden, um die Kommunikation zwischen Subsystemen zu blockieren. Es kann sinnvoll sein, sie auf Probleme hin zu überprüfen.

#### Einrichten von Regeln für iptables und SELinux

Um Regeln einzurichten, die die Kommunikation mit der Firewall oder SELinux ermöglichen, konsultieren Sie die folgenden Ressourcen:

* [iptables how-to](https://help.ubuntu.com/community/IptablesHowTo)
* [Bearbeiten von iptables rules (fedora-Projekt)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [Einführung in SELinux (CentOS.org)](https://www.centos.org)
* [SELinux-Anleitungswiki (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Installieren des Java Software Development Kits

Geben Sie den folgenden Befehl ein, um festzustellen, ob Java bereits installiert ist:

```bash
java -version
```

Wenn die Nachricht `java: command not found` angezeigt, müssen Sie das Java-SDK installieren, wie im nächsten Abschnitt beschrieben.

Siehe einen der folgenden Abschnitte:

* [Installieren Sie das neueste JDK auf CentOS](#install-the-jdk-on-centos)
* [Installieren Sie das neueste JDK auf Ubuntu](#install-the-jdk-on-ubuntu)

#### JDK auf CentOS installieren

Siehe dies [Digital Ocean-Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

Installieren Sie unbedingt das JDK und *not* die JRE.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Java Version 8 ist möglicherweise nicht für alle Betriebssysteme verfügbar. Sie können beispielsweise [die Liste der verfügbaren Pakete für Ubuntu durchsuchen](https://packages.ubuntu.com/).

#### JDK auf Ubuntu installieren

Um JDK 1.8 auf Ubuntu zu installieren, geben Sie die folgenden Befehle als Benutzer mit ein `root` -Berechtigungen:

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

Weitere Optionen finden Sie unter [Oracle-Dokumentation](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### Suchmaschine installieren

Folgen [Installieren von Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) oder [Installieren und Konfigurieren von OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) für Ihre plattformspezifischen Schritte.

Um zu überprüfen, ob das Elasticsearch funktioniert, geben Sie den folgenden Befehl auf dem Server ein, auf dem es ausgeführt wird:

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

Es wird eine Meldung ähnlich der folgenden angezeigt:

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

Geben Sie die folgenden Befehle ein, um zu überprüfen, ob OpenSearch funktioniert:

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## Upgrade von Elasticsearch

Siehe [Upgrade von Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) umfassende Anweisungen zum Sichern Ihrer Daten, zur Erkennung potenzieller Migrationsprobleme und zum Testen von Upgrades vor der Bereitstellung in der Produktion. Abhängig von Ihrer aktuellen Version von Elasticsearch ist möglicherweise ein vollständiger Neustart des Clusters erforderlich.

Elasticsearch erfordert JDK 1.8 oder höher. Siehe [Installieren des Java Software Development Kits](#install-the-java-software-development-kit) um zu überprüfen, welche Version von JDK installiert ist.

## Zusätzliche Ressourcen

Weitere Informationen finden Sie unter [Dokumentation zu Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html).
