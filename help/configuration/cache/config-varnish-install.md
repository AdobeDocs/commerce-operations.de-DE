---
title: Lack installieren
description: Erfahren Sie mehr über die Installationsanforderungen für Lacke für das Caching in Adobe Commerce. Entdecken Sie Installationsressourcen und Einrichtungshandbücher.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Lack installieren

Die Installation der Lacksoftware sprengt den Rahmen dieses Handbuchs. Weitere Informationen zum Installieren von Varnish finden Sie unter:

- [Installationshandbuch](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Installationsanleitungen für Lacke](https://www.varnish-cache.org/docs)
- [So installieren Sie Lack (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Dieses Thema wurde für Varnish unter CentOS und Apache 2.4 geschrieben. Wenn Sie Varnish in einer anderen Umgebung einrichten, unterscheiden sich einige Befehle wahrscheinlich. Weitere Informationen finden Sie in der vorherigen Dokumentation .
>
>Wenn Sie beabsichtigen, Varnish-Module (vmods) zu installieren, z. B. saint-Modus, sollten Sie Varnish installieren, indem Sie den Code kompilieren, anstatt von einem Paket aus zu installieren. Siehe [Heiliger Modus](config-varnish-advanced.md#saint-mode) für weitere Details.

## Bestätigen der Lackversion

Öffnen Sie ein Terminal und geben Sie den folgenden Befehl ein, um die Version von Varnish anzuzeigen:

```bash
varnishd -V
```

Stellen Sie sicher, dass [Adobe Commerce](../../installation/system-requirements.md) die installierte Version von Varnish unterstützt, bevor Sie fortfahren. Wenn Sie eine nicht unterstützte Version ausführen, müssen Sie auf eine unterstützte Version aktualisieren. Weitere Informationen finden Sie in der Dokumentation zur Lackinstallation .
