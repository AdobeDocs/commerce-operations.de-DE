---
title: Installieren von Varnish
description: Siehe Ratschläge zur Installation von Varnish.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Installieren von Varnish

Die Installation der Varnish-Software geht über diesen Leitfaden hinaus. Weitere Informationen zur Installation von Varnish finden Sie unter:

- [Installationshandbuch](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Anleitungen für die Installation mit unterschiedlicher Länge](https://www.varnish-cache.org/docs)
- [Installieren von Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Dieses Thema wurde für Varnish auf CentOS und Apache 2.4 geschrieben. Wenn Sie Varnish in einer anderen Umgebung einrichten, sind einige Befehle wahrscheinlich anders. Weitere Informationen finden Sie in der vorherigen Dokumentation .
>
>Wenn Sie Varnish-Module (vmods) installieren möchten, z. B. den Saint-Modus, sollten Sie Varnish installieren, indem Sie den Code kompilieren, anstatt über ein Paket zu installieren. Weitere Informationen finden Sie unter [Saint-Modus](config-varnish-advanced.md#saint-mode) .

## Validieren Sie Ihre sprachliche Version.

Öffnen Sie ein Terminal und geben Sie den folgenden Befehl ein, um die Version von Varnish anzuzeigen:

```bash
varnishd -V
```

Stellen Sie sicher, dass [Adobe Commerce](../../installation/system-requirements.md) die installierte Version von Varnish unterstützt, bevor Sie den Vorgang fortsetzen. Wenn Sie eine nicht unterstützte Version ausführen, müssen Sie auf eine unterstützte Version aktualisieren. Weitere Informationen finden Sie in der Dokumentation zur Installation von Varnish .
