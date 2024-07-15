---
title: Cache-Leerung mit mehreren Varnish-Instanzen
description: Erfahren Sie, wie das Löschen des Caches mit mehreren Instanzen vom Typ "Varnish"funktioniert.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# Cache-Leeren mehrerer verschiedener Instanzen

Adobe Commerce unterstützt standardmäßig mehrere verschiedene Instanzen.

In diesem Thema werden die Grundlagen zum Konfigurieren mehrerer verschiedener Instanzen mit Commerce erläutert.

## Konfiguration zum Bereinigen mehrerer verschiedener Instanzen

Commerce löscht verschiedene Hosts, nachdem Sie mit dem Befehl [`magento setup:config:set`](../../installation/tutorials/deployment.md) verschiedene Hosts konfiguriert haben.

Verwenden Sie den Parameter `--http-cache-hosts` , um eine kommagetrennte Liste von &quot;Varnish Hosts&quot;und &quot;Listen Ports&quot;anzugeben. (Trennen Sie Hosts nicht durch Leerzeichen.)

Das Parameterformat muss `<hostname or ip>:<listen port>` sein, wobei Sie `<listen port>` weglassen können, wenn es Port 80 ist.

Beispiel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Sie können dann alle entfernten Hosts löschen, wenn Sie den Commerce-Cache (auch als _Bereinigen_ des Caches bezeichnet) im Admin oder über die Befehlszeile aktualisieren.

Um den Cache mit Admin zu aktualisieren, klicken Sie auf **SYSTEM** > Tools > **Cache-Verwaltung** und dann oben auf der Seite auf **Magento-Cache leeren** . (Sie können auch einzelne Cache-Typen aktualisieren.)

Verwenden Sie den Befehl [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) als den [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md), um den Cache mehrerer Varnish-Instanzen von cli zu aktualisieren.
