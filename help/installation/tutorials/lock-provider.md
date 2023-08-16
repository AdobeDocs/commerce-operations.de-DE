---
title: Sperranbieter konfigurieren
description: Führen Sie diese Schritte aus, um zu verhindern, dass die doppelten Cron-Aufträge und Cron-Gruppen auf Ihrer Adobe Commerce- oder Magento Open Source-Bereitstellung ausgeführt werden.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Sperranbieter konfigurieren

Bevor Sie diesen Befehl ausführen, müssen Sie Folgendes tun: *oder* Sie müssen [Installieren des Programms](../advanced.md):

* [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md)
* [Datenbankschema erstellen](database.md)

## Sichere Installation

{{$include /help/_includes/secure-install.md}}

## Schloss konfigurieren

Konfigurieren Sie einen Sperranbieter, um zu verhindern, dass doppelte Cron-Aufträge und Cron-Gruppen gestartet werden. (Erfordert Adobe Commerce oder Magento Open Source 2.2.x, 2.2.5 und höher sowie 2.3.3 und höher.)

Adobe Commerce und Magento Open Source verwenden die Datenbank, um Sperren standardmäßig zu speichern. Wenn sich auf Ihren Servern mehrere Knoten befinden, empfehlen wir die Verwendung von Zookeeper als Sperranbieter.

Wenn Sie Adobe Commerce in einer Cloud-Infrastruktur ausführen, müssen Sie keine Einstellungen des Sperranbieters konfigurieren. Die Anwendung konfiguriert den Dateisperranbieter für Pro-Projekte während des Bereitstellungsprozesses. Siehe [Cloud-Variablen](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### Befehlsverwendung

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschreibungen

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--lock-provider` | Anbietername sperren: `db`, `zookeeper`oder `file`.<br><br>Der standardmäßige Sperranbieter: `db` | Nein |
| `--lock-db-prefix` | Das spezifische db-Präfix zur Vermeidung von Sperrkonflikten bei der Verwendung von `db` Sperranbieter.<br><br>Der Standardwert: `NULL` | Nein |
| `--lock-zookeeper-host` | Hosten und Anschluss für die Verbindung mit dem Zookeeper-Cluster bei Verwendung der `zookeeper` Sperranbieter.<br><br>Beispiel: `127.0.0.1:2181` | Ja, wenn Sie `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Der Pfad, in dem Zookeeper Sperren speichert.<br><br>Der Standardpfad lautet: `/magento/locks` | Nein |
| `--lock-file-path` | Der Pfad, in dem Dateisperren gespeichert werden. | Ja, wenn Sie `--lock-provider=file` |
