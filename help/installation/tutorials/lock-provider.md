---
title: Konfigurieren des Sperranbieters
description: Führen Sie diese Schritte aus, um zu verhindern, dass doppelte Cron-Aufträge und Cron-Gruppen in Ihrer Adobe Commerce-Bereitstellung ausgeführt werden.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Konfigurieren des Sperranbieters

Bevor Sie diesen Befehl ausführen, müssen Sie Folgendes tun *oder* Sie müssen [die Anwendung installieren](../advanced.md):

* [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md)
* [Erstellen des Datenbankschemas](database.md)

## Sichere Installation

{{$include /help/_includes/secure-install.md}}

## Konfigurieren der Sperre

Konfigurieren Sie einen Sperranbieter, um den Start doppelter Cron-Aufträge und Cron-Gruppen zu verhindern. (Erfordert Adobe Commerce 2.2.x, 2.2.5 und höher sowie 2.3.3 und höher.)

Adobe Commerce verwendet die -Datenbank, um Sperren standardmäßig zu speichern. Wenn Sie mehrere Knoten auf Ihren Servern haben, empfehlen wir die Verwendung von ZooKeeper als Sperranbieter.

Wenn Sie Adobe Commerce in der Cloud-Infrastruktur ausführen, müssen Sie keine Sperranbietereinstellungen konfigurieren. Die Anwendung konfiguriert den Dateisperranbieter für Pro-Projekte während des Bereitstellungsprozesses. Siehe [Cloud-](https://experienceleague.adobe.com/de/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud).

### Befehlsverwendung

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschreibungen

| -Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--lock-provider` | Anbieternamen sperren: `db`, `zookeeper` oder `file`.<br><br>Der standardmäßige Sperranbieter: `db` | Nein |
| `--lock-db-prefix` | Das spezifische DB-Präfix, um Sperrkonflikte bei Verwendung des `db`-Anbieters zu vermeiden.<br><br>Der Standardwert: `NULL` | Nein |
| `--lock-zookeeper-host` | Host und Port für die Verbindung mit dem ZooKeeper-Cluster bei Verwendung des `zookeeper`.<br><br>Beispiel: `127.0.0.1:2181` | Ja, wenn Sie `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Der Pfad, in dem ZooKeeper Sperren speichert.<br><br>Der Standardpfad lautet: `/magento/locks` | Nein |
| `--lock-file-path` | Der Pfad, in dem Dateisperren gespeichert werden. | Ja, wenn Sie `--lock-provider=file` |

<!-- Last updated from includes: 2022-09-08 11:33:05 -->
