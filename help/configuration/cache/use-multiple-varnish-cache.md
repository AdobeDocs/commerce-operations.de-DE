---
title: Cache-Leerung mit mehreren Lackinstanzen
description: Erfahren Sie, wie das Löschen von Caches mit mehreren Varnish-Instanzen in Adobe Commerce funktioniert. Best Practices für Konfiguration und Verwaltung
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 1%

---

# Cache-Löschen mehrerer Lackinstanzen

Adobe Commerce unterstützt standardmäßig mehrere Varnish-Instanzen.

In diesem Abschnitt werden die Grundlagen zum Konfigurieren mehrerer Varnish-Instanzen mit Commerce erläutert.

## Konfiguration zum Bereinigen mehrerer Lackinstanzen

Commerce löscht Varnish-Hosts, nachdem Sie Varnish-Hosts mit dem Befehl [`magento setup:config:set`](../../installation/tutorials/deployment.md) konfiguriert haben.

Sie sollten den `--http-cache-hosts`-Parameter verwenden, um eine kommagetrennte Liste von Lack-Hosts und Listener-Ports anzugeben. (Hosts dürfen nicht durch Leerzeichen getrennt werden.)

Das Parameterformat muss `<hostname or ip>:<listen port>` sein, wobei Sie `<listen port>` auslassen können, wenn es sich um Port 80 handelt.

Beispiel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Sie können dann alle Varnish-Hosts bereinigen, wenn Sie den Commerce-Cache (auch als _bezeichnet)_ Admin aktualisieren oder die Befehlszeile verwenden.

Um den Cache mithilfe der Admin zu aktualisieren, klicken Sie auf **SYSTEM** > Tools **Cache-Verwaltung** und dann oben auf der Seite **Magento-** leeren). (Sie können auch einzelne Cache-Typen aktualisieren.)

Um den Cache mehrerer Varnish-Instanzen von der CLI zu aktualisieren, verwenden Sie den [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types)-Befehl als [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
