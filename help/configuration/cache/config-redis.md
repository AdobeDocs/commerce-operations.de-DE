---
title: Konfigurieren von Redis
description: Verschaffen Sie sich einen Überblick über die Redis-Funktionen und starten Sie Ihre Redis-Konfiguration.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Konfigurieren von Redis

Zu den Redis-Funktionen gehören:

- PHP-Sitzungsspeicher
- Tag-basierte Cache-Bereinigung ohne `foreach` Schleifen
- Speicherung auf der Festplatte und Master/Slave-Replikation

## Installieren von Redis

Die Installation und Konfiguration der Redis-Software sprengt den Rahmen dieses Handbuchs. Anzeige von Ressourcen wie:

- [Redis-Seite herunterladen](https://redis.io/download)
- [Redis-Schnellstart](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Redis-Dokumentationsseite](https://redis.io/docs)

## Einrichten der Redis-Konfiguration

Abhängig von Ihrer Installation finden Sie Ihre Redis-Konfiguration in der Regel in einer der folgenden Dateien: `/etc/redis/redis.conf` oder `/etc/redis/<port>.conf`

Um die Redis-Instanz für Ihre Anforderungen zu optimieren, erzielen Sie die besten Ergebnisse, indem Sie für jede Sitzung eine dedizierte Instanz, Commerce-Cache und FPC verwenden.

Für -Sitzungen empfiehlt Adobe, die Persistenz zu aktivieren, um Redis-Daten mithilfe einer der folgenden Persistenzoptionen auf die Festplatte zu kopieren: reguläre Redis-Datenbank-Backup-Snapshots (RDB) oder Nur-Datei-Persistenzprotokolle (AOF).

- **Redis Database Backup** (RDB)-Snapshots speichern die vollständige Datenbank nach einer bestimmten Zeit, wenn sich eine Mindestanzahl von Schlüsseln seit dem letzten Speichern geändert hat, in einer Dump-Datei. Verwenden Sie die `save` in der `redis.conf`, um diese Einstellung zu konfigurieren.

- **Nur angehängte Datei** (AOF) speichert jeden Schreibvorgang, der an Redis gesendet wird, in einer Journaldatei. Redis liest diese Datei nur beim Neustart und verwendet sie zum Wiederherstellen des ursprünglichen Datensatzes.

Sie können auch die Optionen RDB und AOF gleichzeitig aktivieren. Weitere Informationen einschließlich der Vor- und Nachteile der Persistenzoptionen finden Sie in der [Redis-Persistenz-Dokumentation](https://redis.io/topics/persistence).

Richten Sie für die Cache-Instanz die -Instanz so ein, dass sie groß genug ist, um den gesamten Commerce-Cache zu speichern. Die Größenanforderungen hängen von verschiedenen Faktoren ab, z. B. der Anzahl der Produkte und den Ansichten des Geschäfts. Als Ausgangspunkt können Sie die Größe des Cache-Ordners in Ihrem Dateisystem verwenden. Wenn der `var/cache` Ordner auf Ihrem Dateisystem beispielsweise 5 GB beträgt, richten Sie Ihre Redis-Instanz mit mindestens 5 GB ein, um zu starten. Persistenz ist für die Cache-Instanz nicht erforderlich, da der Commerce-Cache wiederhergestellt werden kann. Siehe [Handbuch zum Redis-Cache](https://redis.io/docs/latest/develop/use/).

Zur Leistungsoptimierung können Sie die folgenden Einstellungen für das asynchrone Löschen aktivieren. Diese Einstellungen ändern das Verhalten von Redis nicht.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

In Redis 6.x und höher können Sie auch den folgenden Wert hinzufügen:

```ini
lazyfree-lazy-user-del yes
```
