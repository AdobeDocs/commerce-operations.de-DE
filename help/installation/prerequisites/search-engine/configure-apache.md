---
title: Konfigurieren von Apache für Ihre Suchmaschine
description: Führen Sie diese Schritte aus, um eine Suchmaschine mit dem Apache-Webserver für lokale Installationen von Adobe Commerce zu konfigurieren.
feature: Install, Search
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Konfigurieren von Apache für Ihre Suchmaschine

{{$include /help/_includes/web-server-communication.md}}

## Proxy einrichten

>[!NOTE]
>
>OpenSearch-Unterstützung wurde in 2.4.4 hinzugefügt. OpenSearch ist eine kompatible Abspaltung von Elasticsearch. Weitere [&#x200B; finden Sie unter „Migrieren von Elasticsearch &#x200B;](../../../upgrade/prepare/opensearch-migration.md) OpenSearch“.

In diesem Abschnitt wird beschrieben, wie Sie Apache als *unsicheren* Proxy konfigurieren, sodass Adobe Commerce eine auf diesem Server ausgeführte Suchmaschine verwenden kann. In diesem Abschnitt wird nicht beschrieben, wie Sie die HTTP-Standardauthentifizierung einrichten. Dies wird unter [Sichere Kommunikation mit Apache“ &#x200B;](#secure-communication-with-apache).

>[!NOTE]
>
>Der Grund, warum der Proxy in diesem Beispiel nicht gesichert ist, liegt darin, dass die Einrichtung und Überprüfung einfacher ist. Sie können TLS mit diesem Proxy verwenden. Wenn Sie dies wünschen, stellen Sie sicher, dass Sie die Proxy-Informationen zu Ihrer sicheren virtuellen Host-Konfiguration hinzufügen.

### Proxy für Apache 2.4 einrichten

In diesem Abschnitt wird beschrieben, wie Sie einen Proxy mit einem virtuellen Host konfigurieren.

1. Aktivieren Sie `mod_proxy` wie folgt:

   ```bash
   a2enmod proxy_http
   ```

1. Öffnen von `/etc/apache2/sites-available/000-default.conf` mit einem Texteditor
1. Fügen Sie die folgende -Anweisung am Anfang der Datei hinzu:

   ```conf
   Listen 8080
   ```

1. Fügen Sie unten in der Datei Folgendes hinzu:

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. Apache neu starten:

   ```bash
   service apache2 restart
   ```

1. Überprüfen Sie, ob der Proxy funktioniert, indem Sie den folgenden Befehl eingeben:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Wenn Sie beispielsweise Elasticsearch verwenden und Ihr Proxy Port 8080 verwendet:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Meldungen ähnlich der folgenden werden angezeigt, um auf Erfolg hinzuweisen:

   ```
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Sichere Kommunikation mit Apache

In diesem Abschnitt wird beschrieben, wie Sie die Kommunikation zwischen Apache und der Suchmaschine mithilfe der [HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617)-Authentifizierung mit Apache sichern. Weitere Informationen zu Optionen finden Sie in einer der folgenden Ressourcen:

* [Tutorial zur Authentifizierung und Autorisierung bei Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

Siehe einen der folgenden Abschnitte:

* [Erstellen einer Kennwortdatei](#create-a-password)
* [Konfigurieren des sicheren virtuellen Hosts](#secure-communication-with-apache)

### Passwort erstellen

Aus Sicherheitsgründen können Sie die Kennwortdatei an einer beliebigen Stelle außer dem Stammordner des Webservers finden. In diesem Beispiel zeigen wir, wie die Kennwortdatei in einem neuen Verzeichnis gespeichert wird.

#### Installieren von htpasswd, falls erforderlich

Überprüfen Sie zunächst, ob das Dienstprogramm Apache `htpasswd` wie folgt installiert ist:

1. Geben Sie den folgenden Befehl ein, um festzustellen, ob `htpasswd` bereits installiert ist:

   ```bash
   which htpasswd
   ```

   Wenn ein Pfad angezeigt wird, wird er installiert. Wenn der Befehl keine Ausgabe zurückgibt, wird `htpasswd` nicht installiert.

1. Installieren Sie bei Bedarf `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### Erstellen einer Kennwortdatei

Geben Sie die folgenden Befehle als Benutzer mit `root` Berechtigungen ein:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

Hierbei gilt

* `<username>` können sein:

   * Einrichten von cron: der Webserver-Benutzer oder ein anderer Benutzer.

  In diesem Beispiel verwenden wir den Webserver-Benutzer, aber die Auswahl des Benutzers liegt bei Ihnen.

   * Einrichten von Elasticsearch: Der Benutzer heißt in diesem Beispiel `magento_elasticsearch`

* `<password file name>` muss eine ausgeblendete Datei sein (beginnt mit `.`) und sollte den Namen des Benutzers widerspiegeln. Einzelheiten finden Sie in den Beispielen weiter unten in diesem Abschnitt.

Befolgen Sie die Anweisungen auf Ihrem Bildschirm, um ein Kennwort für den Benutzer zu erstellen.

#### Beispiele

**Beispiel 1: cron**
Für Cron müssen Sie die Authentifizierung nur für einen Benutzer einrichten. In diesem Beispiel verwenden wir den Webserver-Benutzer. Um eine Kennwortdatei für den Webserver-Benutzer zu erstellen, geben Sie die folgenden Befehle ein:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**Beispiel 2: Elasticsearch**
Sie müssen die Authentifizierung für zwei Benutzer einrichten: einen mit Zugriff auf nginx und einen mit Zugriff auf Elasticsearch. Um Kennwortdateien für diese Benutzer zu erstellen, geben Sie die folgenden Befehle ein:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### Zusätzliche Benutzer hinzufügen

Um einen weiteren Benutzer zu Ihrer Kennwortdatei hinzuzufügen, geben Sie den folgenden Befehl als Benutzer mit `root` Berechtigungen ein:

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Sichere Kommunikation mit Apache

In diesem Abschnitt wird beschrieben, wie Sie [HTTP-Standardauthentifizierung](https://httpd.apache.org/docs/2.2/howto/auth.html) einrichten. Durch die gemeinsame Verwendung von TLS und HTTP Basic-Authentifizierung wird verhindert, dass Personen die Kommunikation mit Elasticsearch oder OpenSearch oder Ihrem Anwendungs-Server abfangen.

In diesem Abschnitt wird beschrieben, wie Sie angeben, wer auf den Apache-Server zugreifen kann.

1. Verwenden Sie einen Texteditor, um die folgenden Inhalte zu Ihrem sicheren virtuellen Host hinzuzufügen.

   * Apache 2.4: `/etc/apache2/sites-available/default-ssl.conf` bearbeiten

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

1. Wenn Sie das vorherige zu Ihrem sicheren virtuellen Host hinzugefügt haben, entfernen Sie `Listen 8080` und die `<VirtualHost *:8080>` Anweisungen, die Sie zuvor zu Ihrem unsicheren virtuellen Host hinzugefügt haben.

1. Speichern Sie Ihre Änderungen, beenden Sie den Texteditor und starten Sie Apache neu:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### Überprüfen

{{$include /help/_includes/verify-secure-communication.md}}

<!-- Last updated from includes: 2024-07-18 15:50:54 -->
