---
title: Cache-Leerung mit mehreren Varnish-Instanzen
description: Erfahren Sie, wie das Löschen des Caches mit mehreren Instanzen vom Typ "Varnish"funktioniert.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---


# Cache-Leeren mehrerer verschiedener Instanzen

Adobe Commerce und Magento Open Source unterstützen standardmäßig mehrere verschiedene Instanzen.

In diesem Thema werden die Grundlagen zum Konfigurieren mehrerer verschiedener Instanzen mit Commerce erläutert.

## Konfiguration zum Bereinigen mehrerer verschiedener Instanzen

Commerce bereinigt verschiedene Hosts, nachdem Sie verschiedene Hosts mithilfe der [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html) Befehl.

Sie sollten die `--http-cache-hosts` -Parameter, um eine kommagetrennte Liste unterschiedlicher Hosts und Listen-Ports anzugeben. (Trennen Sie Hosts nicht durch Leerzeichen.)

Das Parameterformat muss `<hostname or ip>:<listen port>`, wo Sie weglassen können `<listen port>` wenn es Port 80 ist.

Beispiel:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

Sie können dann alle leeren Hosts löschen, wenn Sie den Commerce-Cache aktualisieren (auch als _Reinigung_ den Cache) im Admin oder über die Befehlszeile verwenden.

Um den Cache mit dem Admin zu aktualisieren, klicken Sie auf **SYSTEM** > Tools > **Cacheverwaltung** Klicken Sie auf **Magento-Cache leeren** oben auf der Seite. (Sie können auch einzelne Cache-Typen aktualisieren.)

Verwenden Sie zum Aktualisieren des Caches mehrerer Varnish-Instanzen von CLI die [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) als [Dateisysteminhaber](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
