---
title: Konfigurieren von Nginx für Ihre Suchmaschine
description: Führen Sie diese Schritte aus, um eine Suchmaschine mit dem Nginx-Webserver für lokale Installationen von Adobe Commerce und Magento Open Source zu konfigurieren.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---


# Konfigurieren von Nginx für Ihre Suchmaschine

{{$include /help/_includes/web-server-communication.md}}

## Proxy einrichten

>[!NOTE]
>
>OpenSearch-Unterstützung wurde in Version 2.4.4 hinzugefügt. OpenSearch ist eine kompatible Abspaltung von Elasticsearch. Siehe [Migrieren des Elasticsearchs zu OpenSearch](../../../upgrade/prepare/opensearch-migration.md) für weitere Informationen.

In diesem Abschnitt wird beschrieben, wie Sie nginx als *unsecure* , damit Adobe Commerce eine Suchmaschine verwenden kann, die auf diesem Server ausgeführt wird. In diesem Abschnitt wird die Einrichtung der einfachen HTTP-Authentifizierung nicht beschrieben. wird in [Sichere Kommunikation mit nginx](#secure-communication-with-nginx).

>[!NOTE]
>
>Der Grund, warum der Proxy in diesem Beispiel nicht gesichert ist, ist, dass die Einrichtung und Überprüfung einfacher ist. Sie können bei Bedarf TLS mit diesem Proxy verwenden. Stellen Sie dazu sicher, dass Sie die Proxy-Informationen zu Ihrer sicheren Serverblockkonfiguration hinzufügen.

### Geben Sie zusätzliche Konfigurationsdateien in Ihrer globalen Konfiguration an

Sicherstellen der globalen `/etc/nginx/nginx.conf` enthält die folgende Zeile, sodass sie die anderen Konfigurationsdateien lädt, die in den folgenden Abschnitten erläutert werden:

```conf
include /etc/nginx/conf.d/*.conf;
```

### Einrichten von Nginx als Proxy

In diesem Abschnitt wird beschrieben, wie Sie festlegen, wer auf den nginx-Server zugreifen kann.

1. Verwenden eines Texteditors zum Erstellen einer Datei `/etc/nginx/conf.d/magento_es_auth.conf` mit folgendem Inhalt:

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Starten Sie nginx neu:

   ```bash
   service nginx restart
   ```

1. Stellen Sie sicher, dass der Proxy funktioniert, indem Sie den folgenden Befehl eingeben:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Wenn Ihr Proxy beispielsweise Port 8080 verwendet:

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

## Sichere Kommunikation mit nginx

In diesem Abschnitt wird beschrieben, wie Sie [HTTP Basic-Authentifizierung](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) mit Ihrem sicheren Proxy. Die Verwendung von TLS und HTTP Basic-Authentifizierung verhindert, dass jeder die Kommunikation mit Elasticsearch oder OpenSearch oder Ihrem Anwendungsserver abfängt.

Da nginx nativ die HTTP Basic-Authentifizierung unterstützt, empfehlen wir sie beispielsweise [Digest Authentication](https://www.nginx.com/resources/wiki/modules/auth_digest/), was in der Produktion nicht empfohlen wird.

Zusätzliche Ressourcen:

* [Einrichten der Kennwortauthentifizierung mit Nginx auf Ubuntu 14.04 (Digital Ocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Einfache HTTP-Authentifizierung mit Nginx (HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Beispiel-Nginx-Konfigurationen für Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Erstellen von Kennwörtern](#create-a-password)
* [Zugriff auf nginx einrichten](#set-up-access-to-nginx)
* [Einrichten eines eingeschränkten Kontexts für die Suchmaschine](#set-up-a-restricted-context-for-the-search-engine)
* [Sicherstellen, dass die Kommunikation sicher ist](#secure-communication-with-nginx)

### Kennwort erstellen

Es wird empfohlen, den Apache zu verwenden `htpasswd` -Befehl zum Kodieren von Kennwörtern für Benutzer mit Zugriff auf Elasticsearch oder OpenSearch (mit dem Namen `magento_elasticsearch` in diesem Beispiel).

So erstellen Sie ein Kennwort:

1. Geben Sie den folgenden Befehl ein, um zu ermitteln, ob `htpasswd` ist bereits installiert:

   ```bash
   which htpasswd
   ```

   Wenn ein Pfad angezeigt wird, wird er installiert. wenn der Befehl keine Ausgabe zurückgibt, `htpasswd` nicht installiert ist.

1. Installieren Sie bei Bedarf `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. Erstellen Sie eine `/etc/nginx/passwd` Verzeichnis zum Speichern von Kennwörtern:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Aus Sicherheitsgründen `<filename>` sollte ausgeblendet werden; Das heißt, es muss mit einem Punkt beginnen.

1. *(Optional).* Um Ihrer Kennwortdatei einen weiteren Benutzer hinzuzufügen, geben Sie denselben Befehl ohne die `-c` (Erstellen):

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Überprüfen Sie, ob der Inhalt von `/etc/nginx/passwd` korrekt ist.

### Zugriff auf nginx einrichten

In diesem Abschnitt wird beschrieben, wie Sie festlegen, wer auf den nginx-Server zugreifen kann.

>[!WARNING]
>
>Das folgende Beispiel zeigt eine *unsecure* Proxy. Um einen sicheren Proxy zu verwenden, fügen Sie Ihrem sicheren Serverblock den folgenden Inhalt (mit Ausnahme des Überwachungsanschlusses) hinzu.

Verwenden Sie einen Texteditor, um entweder `/etc/nginx/conf.d/magento_es_auth.conf` (unsecure) oder Ihrem sicheren Serverblock mit folgendem Inhalt:

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>Der im vorherigen Beispiel dargestellte Listener-Port der Suchmaschine ist nur ein Beispiel. Aus Sicherheitsgründen empfehlen wir die Verwendung eines nicht standardmäßigen Überwachungsports.

### Einrichten eines eingeschränkten Kontexts für die Suchmaschine

In diesem Abschnitt wird beschrieben, wie Sie festlegen, wer auf den Suchmaschinenserver zugreifen kann.

1. Geben Sie den folgenden Befehl ein, um einen Ordner zum Speichern der Authentifizierungskonfiguration zu erstellen:

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Verwenden eines Texteditors zum Erstellen einer Datei `/etc/nginx/auth/magento_elasticsearch.conf` mit folgendem Inhalt:

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. Wenn Sie einen sicheren Proxy einrichten, löschen Sie `/etc/nginx/conf.d/magento_es_auth.conf`.
1. Starten Sie nginx neu und fahren Sie mit dem nächsten Abschnitt fort:

   ```bash
   service nginx restart
   ```

#### Überprüfen

{{$include /help/_includes/verify-secure-communication.md}}
