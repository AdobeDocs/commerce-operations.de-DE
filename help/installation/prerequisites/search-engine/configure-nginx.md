---
title: Konfigurieren von Nginx für Ihre Suchmaschine
description: Führen Sie diese Schritte aus, um eine Suchmaschine mit dem Nginx-Webserver für lokale Installationen von Adobe Commerce zu konfigurieren.
feature: Install, Search
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# Konfigurieren von Nginx für Ihre Suchmaschine

{{$include /help/_includes/web-server-communication.md}}

## Proxy einrichten

>[!NOTE]
>
>OpenSearch-Unterstützung wurde in 2.4.4 hinzugefügt. OpenSearch ist eine kompatible Abspaltung von Elasticsearch. Weitere [ finden Sie unter „Migrieren von Elasticsearch ](../../../upgrade/prepare/opensearch-migration.md) OpenSearch“.

In diesem Abschnitt wird beschrieben, wie Sie Nginx als *unsicheren*-Proxy konfigurieren, damit Adobe Commerce eine auf diesem Server ausgeführte Suchmaschine verwenden kann. In diesem Abschnitt wird nicht beschrieben, wie Sie die HTTP-Standardauthentifizierung einrichten. Dies wird unter [Sichere Kommunikation mit nginx](#secure-communication-with-nginx) erläutert.

>[!NOTE]
>
>Der Grund, warum der Proxy in diesem Beispiel nicht gesichert ist, liegt darin, dass die Einrichtung und Überprüfung einfacher ist. Sie können bei Bedarf TLS mit diesem Proxy verwenden. Stellen Sie sicher, dass Sie die Proxy-Informationen zu Ihrer Konfiguration des sicheren Serverblocks hinzufügen.

### Angeben zusätzlicher Konfigurationsdateien in Ihrer globalen Konfiguration

Stellen Sie sicher, dass die globale `/etc/nginx/nginx.conf` die folgende Zeile enthält, damit die anderen Konfigurationsdateien geladen werden, die in den folgenden Abschnitten beschrieben werden:

```conf
include /etc/nginx/conf.d/*.conf;
```

### Einrichten von nginx als Proxy

In diesem Abschnitt wird beschrieben, wie Sie angeben, wer auf den nginx-Server zugreifen kann.

1. Verwenden Sie einen Texteditor, um eine `/etc/nginx/conf.d/magento_es_auth.conf` mit folgendem Inhalt zu erstellen:

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Nginx neu starten:

   ```bash
   service nginx restart
   ```

1. Überprüfen Sie, ob der Proxy funktioniert, indem Sie den folgenden Befehl eingeben:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Wenn Ihr Proxy beispielsweise Port 8080 verwendet:

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

## Sichere Kommunikation mit nginx

In diesem Abschnitt wird beschrieben, wie Sie [HTTP-Standardauthentifizierung](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) mit Ihrem sicheren Proxy einrichten. Durch die gemeinsame Verwendung von TLS und HTTP Basic-Authentifizierung wird verhindert, dass Personen die Kommunikation mit Elasticsearch oder OpenSearch oder Ihrem Anwendungs-Server abfangen.

Da nginx nativ die HTTP-Standardauthentifizierung unterstützt, empfehlen wir diese über z. B. [Digest-Authentifizierung](https://www.nginx.com/resources/wiki/modules/auth_digest/), was in der Produktion nicht empfohlen wird.

Zusätzliche Ressourcen:

* [Einrichten der Passwortauthentifizierung mit Nginx auf Ubuntu 14.04 (Digital Ocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Einfache HTTP-Authentifizierung mit Nginx (howtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Nginx-Beispielkonfigurationen für Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Weitere Informationen finden Sie in den folgenden Abschnitten:

* [Kennwörter erstellen](#create-a-password)
* [Einrichten des Zugriffs auf nginx](#set-up-access-to-nginx)
* [Einrichten eines eingeschränkten Kontexts für die Suchmaschine](#set-up-a-restricted-context-for-the-search-engine)
* [Sicherstellen, dass Kommunikation sicher ist](#secure-communication-with-nginx)

### Passwort erstellen

Es wird empfohlen, den Apache `htpasswd`-Befehl zu verwenden, um Kennwörter für Benutzende mit Zugriff auf Elasticsearch oder OpenSearch zu kodieren (in diesem Beispiel `magento_elasticsearch` genannt).

So erstellen Sie ein Kennwort:

1. Geben Sie den folgenden Befehl ein, um festzustellen, ob `htpasswd` bereits installiert ist:

   ```bash
   which htpasswd
   ```

   Wenn ein Pfad angezeigt wird, wird er installiert. Wenn der Befehl keine Ausgabe zurückgibt, wird `htpasswd` nicht installiert.

1. Installieren Sie bei Bedarf `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. Erstellen Sie ein `/etc/nginx/passwd` Verzeichnis zum Speichern von Kennwörtern:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Aus Sicherheitsgründen sollten `<filename>` ausgeblendet sein. Das heißt, sie müssen mit einem Punkt beginnen.

1. *(optional).* Um einen weiteren Benutzer zu Ihrer Kennwortdatei hinzuzufügen, geben Sie denselben Befehl ohne die Option `-c` (Erstellen) ein:

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Überprüfen Sie, ob der Inhalt von `/etc/nginx/passwd` korrekt ist.

### Einrichten des Zugriffs auf nginx

In diesem Abschnitt wird beschrieben, wie Sie angeben, wer auf den nginx-Server zugreifen kann.

>[!WARNING]
>
>Das folgende Beispiel bezieht sich auf einen *unsicheren* Proxy. Um einen sicheren Proxy zu verwenden, fügen Sie die folgenden Inhalte (mit Ausnahme des Listen-Ports) zu Ihrem sicheren Serverblock hinzu.

Verwenden Sie einen Texteditor, um entweder `/etc/nginx/conf.d/magento_es_auth.conf` (unsicher) oder Ihren sicheren Serverblock mit den folgenden Inhalten zu ändern:

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
>Der im vorherigen Beispiel dargestellte Listen-Port für Suchmaschinen ist nur ein Beispiel. Aus Sicherheitsgründen empfehlen wir die Verwendung eines nicht standardmäßigen Listen-Ports.

### Einrichten eines eingeschränkten Kontexts für die Suchmaschine

In diesem Abschnitt wird beschrieben, wie Sie angeben, wer auf den Suchmaschinenserver zugreifen kann.

1. Geben Sie den folgenden Befehl ein, um ein Verzeichnis zu erstellen, in dem die Authentifizierungskonfiguration gespeichert wird:

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Verwenden Sie einen Texteditor, um eine `/etc/nginx/auth/magento_elasticsearch.conf` mit folgendem Inhalt zu erstellen:

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

1. Wenn Sie einen sicheren Proxy eingerichtet haben, löschen Sie `/etc/nginx/conf.d/magento_es_auth.conf`.
1. Starten Sie nginx neu und fahren Sie mit dem nächsten Abschnitt fort:

   ```bash
   service nginx restart
   ```

#### Überprüfen

{{$include /help/_includes/verify-secure-communication.md}}
