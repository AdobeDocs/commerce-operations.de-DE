---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 1%

---
# Überprüfen der Kommunikationssicherheit

In diesem Abschnitt werden zwei Möglichkeiten erläutert, um zu überprüfen, ob die HTTP-Standardauthentifizierung funktioniert:

* Verwenden eines `curl`-Befehls zur Überprüfung, ob Sie einen Benutzernamen und ein Kennwort eingeben müssen, um den Cluster-Status zu erhalten
* Konfigurieren der HTTP-Standardauthentifizierung in der Admin Console

## Verwenden eines `curl` Befehls zum Überprüfen des Cluster-Status

Geben Sie den folgenden Befehl ein:

```shell
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Wenn Sie beispielsweise den Befehl auf dem Suchmaschinenserver eingeben und Ihr Proxy Port 8080 verwendet:

```shell
curl -i http://localhost:8080/_cluster/health
```

Die folgende Meldung wird angezeigt, um auf fehlgeschlagene Authentifizierung hinzuweisen:

```text
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

Versuchen Sie nun den folgenden Befehl:

```shell
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Beispiel:

```shell
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

Diesmal ist der Befehl erfolgreich mit einer Meldung ähnlich der folgenden:

```text
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## Konfigurieren der HTTP-Standardauthentifizierung in der Admin Console

Führen Sie dieselben Aufgaben aus wie unter [Suchmaschinenkonfiguration](../configuration/search/configure-search-engine.md) *außer* klicken Sie **[!UICONTROL Yes]** in der **[!UICONTROL Enable HTTP Auth]** Liste und geben Sie Ihren Benutzernamen und Ihr Kennwort in die entsprechenden Felder ein.

Klicken Sie auf **[!UICONTROL Test Connection]** , um sicherzustellen, dass es funktioniert, und klicken Sie dann auf **[!UICONTROL Save Config]**.

Sie müssen den Cache leeren und neu indizieren, bevor Sie fortfahren.
