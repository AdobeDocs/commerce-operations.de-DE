---
title: Installieren von Varnish
description: Siehe Ratschläge zur Installation von Varnish.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# Installieren von Varnish

Die Installation der Varnish-Software geht über den Rahmen dieses Handbuchs hinaus. Weitere Informationen zur Installation von Varnish finden Sie unter:

- [Installationshandbuch](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Anleitungen zur Installation von Vars](https://www.varnish-cache.org/docs)
- [Installieren von Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Dieses Thema wurde für Varnish unter CentOS und Apache 2.4 geschrieben. Wenn Sie Varnish in einer anderen Umgebung einrichten, sind einige Befehle wahrscheinlich anders. Weitere Informationen finden Sie in der vorherigen Dokumentation .
>
>Wenn Sie Varnish-Module (vmods) installieren möchten, z. B. den Saint-Modus, sollten Sie Varnish installieren, indem Sie den Code kompilieren, anstatt über ein Paket zu installieren. Siehe [Saint-Modus](config-varnish-advanced.md#saint-mode) für weitere Details.

## Validieren Sie Ihre sprachliche Version.

Öffnen Sie ein Terminal und geben Sie den folgenden Befehl ein, um die Version von Varnish anzuzeigen:

```bash
varnishd -V
```

Beispiel:

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

Stellen Sie sicher, dass die Version 6.x ist, bevor Sie fortfahren. Wenn Sie eine Version unter 6.x ausführen, müssen Sie auf eine unterstützte Version aktualisieren. Weitere Informationen finden Sie in der Dokumentation zur Installation von Varnish .
