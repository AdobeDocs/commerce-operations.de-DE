---
title: Konfigurieren von Apache für Ihre Suchmaschine
description: Führen Sie diese Schritte aus, um eine Suchmaschine mit dem Apache-Webserver für lokale Installationen von Adobe Commerce und Magento Open Source zu konfigurieren.
feature: Install, Search
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Konfigurieren von Apache für Ihre Suchmaschine

{{$include /help/_includes/web-server-communication.md}}

## Proxy einrichten

>[!NOTE]
>
>OpenSearch-Unterstützung wurde in Version 2.4.4 hinzugefügt. OpenSearch ist eine kompatible Abspaltung von Elasticsearch. Siehe [Migrieren des Elasticsearchs zu OpenSearch](../../../upgrade/prepare/opensearch-migration.md) für weitere Informationen.

In diesem Abschnitt wird beschrieben, wie Sie Apache als *unsecure* , damit Adobe Commerce eine Suchmaschine verwenden kann, die auf diesem Server ausgeführt wird. In diesem Abschnitt wird die Einrichtung der einfachen HTTP-Authentifizierung nicht besprochen, wie hier beschrieben: [Sichere Kommunikation mit Apache](#secure-communication-with-apache).

>[!NOTE]
>
>Der Grund, warum der Proxy in diesem Beispiel nicht gesichert ist, ist, dass die Einrichtung und Überprüfung einfacher ist. Sie können TLS mit diesem Proxy verwenden. Wenn Sie dies wünschen, stellen Sie sicher, dass Sie die Proxy-Informationen zu Ihrer sicheren Virtual-Host-Konfiguration hinzufügen.

### Proxy für Apache 2.4 einrichten

In diesem Abschnitt wird beschrieben, wie Sie einen Proxy mit einem virtuellen Host konfigurieren.

1. Aktivieren `mod_proxy` wie folgt:

   ```bash
   a2enmod proxy_http
   ```

1. Öffnen Sie mithilfe eines Texteditors `/etc/apache2/sites-available/000-default.conf`
1. Fügen Sie oben in der Datei die folgende Anweisung hinzu:

   ```conf
   Listen 8080
   ```

1. Fügen Sie am Ende der Datei Folgendes hinzu:

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. Starten Sie Apache neu:

   ```bash
   service apache2 restart
   ```

1. Stellen Sie sicher, dass der Proxy funktioniert, indem Sie den folgenden Befehl eingeben:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Wenn Sie beispielsweise Elasticsearch verwenden und Ihr Proxy Port 8080 verwendet:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Meldungen, die der folgenden Anzeige ähneln, zeigen Erfolg an:

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Sichere Kommunikation mit Apache

In diesem Abschnitt wird beschrieben, wie Sie die Kommunikation zwischen Apache und der Suchmaschine mit [HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617) Authentifizierung mit Apache. Weitere Optionen finden Sie in einer der folgenden Ressourcen:

* [Tutorial zur Authentifizierung und Autorisierung von Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

Siehe einen der folgenden Abschnitte:

* [Kennwortdatei erstellen](#create-a-password)
* [Sicheren virtuellen Host konfigurieren](#secure-communication-with-apache)

### Kennwort erstellen

Aus Sicherheitsgründen können Sie die Kennwortdatei an einer beliebigen Stelle außerhalb des Basisverzeichnisses für Ihren Webserver finden. In diesem Beispiel wird gezeigt, wie die Kennwortdatei in einem neuen Verzeichnis gespeichert wird.

#### Installieren Sie bei Bedarf htpasswd

Überprüfen Sie zunächst, ob Sie über den Apache verfügen. `htpasswd` Das Dienstprogramm wird wie folgt installiert:

1. Geben Sie den folgenden Befehl ein, um zu ermitteln, ob `htpasswd` ist bereits installiert:

   ```bash
   which htpasswd
   ```

   Wenn ein Pfad angezeigt wird, wird er installiert. Wenn der Befehl keine Ausgabe zurückgibt, `htpasswd` nicht installiert ist.

1. Installieren Sie bei Bedarf `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### Kennwortdatei erstellen

Geben Sie die folgenden Befehle als Benutzer mit `root` -Berechtigungen:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

Wo

* `<username>` kann sein:

   * Einrichten von Cron: der Webserver-Benutzer oder ein anderer Benutzer.

  In diesem Beispiel verwenden wir den Webserver-Benutzer, aber die Wahl des Benutzers liegt bei Ihnen.

   * Einrichten eines Elasticsearchs: Der Benutzer hat den Namen `magento_elasticsearch` in diesem Beispiel

* `<password file name>` muss eine ausgeblendete Datei sein (beginnt mit `.`) und sollte den Namen des Benutzers widerspiegeln. Weitere Informationen finden Sie in den Beispielen weiter unten in diesem Abschnitt .

Befolgen Sie die Anweisungen auf Ihrem Bildschirm, um ein Kennwort für den Benutzer zu erstellen.

#### Beispiele

**Beispiel 1: cron**
Sie müssen die Authentifizierung nur für einen Benutzer für Cron einrichten. In diesem Beispiel verwenden wir den Webserver-Benutzer. Geben Sie die folgenden Befehle ein, um eine Kennwortdatei für den Webserver-Benutzer zu erstellen:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**Beispiel 2: Elasticsearch**
Sie müssen die Authentifizierung für zwei Benutzer einrichten: einen mit Zugriff auf nginx und einen mit Zugriff auf Elasticsearch. Geben Sie die folgenden Befehle ein, um Kennwortdateien für diese Benutzer zu erstellen:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### Zusätzliche Benutzer hinzufügen

Um Ihrer Kennwortdatei einen weiteren Benutzer hinzuzufügen, geben Sie den folgenden Befehl als Benutzer mit ein: `root` -Berechtigungen:

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Sichere Kommunikation mit Apache

In diesem Abschnitt wird beschrieben, wie Sie [HTTP Basic-Authentifizierung](https://httpd.apache.org/docs/2.2/howto/auth.html). Die Verwendung von TLS und HTTP Basic-Authentifizierung verhindert, dass jeder die Kommunikation mit Elasticsearch oder OpenSearch oder Ihrem Anwendungsserver abfängt.

In diesem Abschnitt wird beschrieben, wie Sie festlegen, wer auf den Apache-Server zugreifen kann.

1. Verwenden Sie einen Texteditor, um Ihrem sicheren virtuellen Host die folgenden Inhalte hinzuzufügen.

   * Apache 2.4: Bearbeiten `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. Wenn Sie den vorherigen zu Ihrem sicheren virtuellen Host hinzugefügt haben, entfernen Sie `Listen 8080` und `<VirtualHost *:8080>` Direktiven, die Sie Ihrem unsicheren virtuellen Host bereits hinzugefügt haben.

1. Speichern Sie Ihre Änderungen, beenden Sie den Texteditor und starten Sie Apache neu:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### Überprüfen

{{$include /help/_includes/verify-secure-communication.md}}
