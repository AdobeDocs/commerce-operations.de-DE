---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# Sichere Kommunikation

In diesem Abschnitt werden zwei Möglichkeiten erläutert, um zu überprüfen, ob die HTTP Basic-Authentifizierung funktioniert:

* Verwenden eines `curl` -Befehl, um zu überprüfen, dass Sie einen Benutzernamen und ein Kennwort eingeben müssen, um den Cluster-Status zu erhalten
* Konfigurieren der einfachen HTTP-Authentifizierung im Admin

## Verwenden Sie eine `curl` Befehl zum Überprüfen des Clusterstatus

Geben Sie den folgenden Befehl ein:

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Wenn Sie beispielsweise den Befehl auf dem Suchmaschinenserver eingeben und Ihr Proxy Port 8080 verwendet:

```bash
curl -i http://localhost:8080/_cluster/health
```

Die folgende Meldung zeigt an, dass die Authentifizierung fehlgeschlagen ist:

```terminal
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

Versuchen Sie jetzt den folgenden Befehl:

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Beispiel:

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

Diesmal ist der Befehl erfolgreich mit einer Meldung ähnlich der folgenden:

```terminal
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## Konfigurieren der einfachen HTTP-Authentifizierung in der Admin-Konsole

Führen Sie dieselben Aufgaben wie unter [Suchmaschinenkonfiguration](../configuration/search/configure-search-engine.md) *Ausnahme* click **[!UICONTROL Yes]** von **[!UICONTROL Enable Elasticsearch HTTP Auth]** und geben Sie Ihren Benutzernamen und Ihr Passwort in die entsprechenden Felder ein.

Klicken **[!UICONTROL Test Connection]** , um sicherzustellen, dass sie funktioniert, und klicken Sie dann auf **[!UICONTROL Save Config]**.

Sie müssen den Magento-Cache und die Neuindizierung leeren, bevor Sie fortfahren.
