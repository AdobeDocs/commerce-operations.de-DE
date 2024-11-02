---
title: Sperranbieter konfigurieren
description: Führen Sie diese Schritte aus, um zu verhindern, dass die doppelten Cron-Aufträge und Cron-Gruppen in Ihrer Adobe Commerce-Bereitstellung ausgeführt werden.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Sperranbieter konfigurieren

Bevor Sie diesen Befehl ausführen, müssen Sie die folgenden *oder* ausführen, die Anwendung [installieren](../advanced.md):

* [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](deployment.md)
* [Datenbankschema erstellen](database.md)

## Sichere Installation

{{$include /help/_includes/secure-install.md}}

## Schloss konfigurieren

Konfigurieren Sie einen Sperranbieter, um zu verhindern, dass doppelte Cron-Aufträge und Cron-Gruppen gestartet werden. (Erfordert Adobe Commerce 2.2.x, 2.2.5 und höher sowie 2.3.3 und höher.)

Adobe Commerce verwendet die Datenbank, um Sperren standardmäßig zu speichern. Wenn sich auf Ihren Servern mehrere Knoten befinden, empfehlen wir die Verwendung von Zookeeper als Sperranbieter.

Wenn Sie Adobe Commerce in einer Cloud-Infrastruktur ausführen, müssen Sie keine Einstellungen des Sperranbieters konfigurieren. Die Anwendung konfiguriert den Dateisperranbieter für Pro-Projekte während des Bereitstellungsprozesses. Siehe [Cloud-Variablen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud).

### Befehlsverwendung

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschreibungen

| Name | Wert | Erforderlich? |
|--- |--- |--- |
| `--lock-provider` | Name des Sperranbieters: `db`, `zookeeper` oder `file`.<br><br>Der standardmäßige Sperranbieter: `db` | Nein |
| `--lock-db-prefix` | Das spezifische db-Präfix, um Sperrkonflikte bei der Verwendung des `db` -Sperranbieters zu vermeiden.<br><br>Der Standardwert: `NULL` | Nein |
| `--lock-zookeeper-host` | Hosten und Anschluss für die Verbindung mit dem Zookeeper-Cluster bei Verwendung des `zookeeper`-Sperranbieters.<br><br>Beispiel: `127.0.0.1:2181` | Ja, wenn Sie `--lock-provider=zookeeper` festlegen |
| `--lock-zookeeper-path` | Der Pfad, in dem Zookeeper Sperren speichert.<br><br>Der Standardpfad lautet: `/magento/locks` | Nein |
| `--lock-file-path` | Der Pfad, in dem Dateisperren gespeichert werden. | Ja, wenn Sie `--lock-provider=file` festlegen |
