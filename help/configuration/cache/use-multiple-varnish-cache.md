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

Commerce bereinigt verschiedene Hosts, nachdem Sie dänische Hosts mithilfe der [`magento setup:config:set`](../../installation/tutorials/deployment.md) Befehl.

Sie sollten die `--http-cache-hosts` -Parameter, um eine kommagetrennte Liste unterschiedlicher Hosts und Listen-Ports anzugeben. (Trennen Sie Hosts nicht durch Leerzeichen.)

Das Parameterformat muss `<hostname or ip>:<listen port>`, wo Sie weglassen können `<listen port>` wenn es Port 80 ist.

Beispiel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Sie können dann alle leeren Hosts löschen, wenn Sie den Commerce-Cache aktualisieren (auch als _Reinigung_ den Cache) im Admin oder über die Befehlszeile verwenden.

Um den Cache mit dem Admin zu aktualisieren, klicken Sie auf **SYSTEM** > Tools > **Cacheverwaltung** Klicken Sie auf **Magento-Cache leeren** oben auf der Seite. (Sie können auch einzelne Cache-Typen aktualisieren.)

Verwenden Sie zum Aktualisieren des Caches mehrerer Varnish-Instanzen von CLI die [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
