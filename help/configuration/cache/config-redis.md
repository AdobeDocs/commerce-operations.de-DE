---
title: Konfigurieren von Redis
description: Verschaffen Sie sich einen Überblick über die Redis-Funktionen und starten Sie Ihre Redis-Konfiguration.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Konfigurieren von Redis

Zu den Redivfunktionen gehören:

- PHP-Sitzungsspeicher
- Tag-basierte Cache-Bereinigung ohne `foreach` Schleifen
- On-Disk speichert und Übergeordnet-/Slave-Replikation

## Installieren von Redis

Die Installation und Konfiguration der Redis-Software geht über den Rahmen dieses Handbuchs hinaus. Ressourcen abrufen, z. B.:

- [Download-Rediv-Seite](https://redis.io/download)
- [Kurzanleitung Redis](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Dokumentationsseite zu Redis](https://redis.io/docs)

## Redis-Konfiguration einrichten

Abhängig von Ihrer Installation finden Sie Ihre Redis-Konfiguration in der Regel in einer der folgenden Dateien: `/etc/redis/redis.conf` oder `/etc/redis/<port>.conf`

Um die Redis-Instanz für Ihre Anforderungen zu optimieren, erzielen Sie die besten Ergebnisse, indem Sie eine dedizierte Instanz für jede Sitzung, jeden Commerce-Cache und jeden FPC verwenden.

Für Sitzungen empfiehlt Adobe, dass Sie die Persistenz aktivieren, um Redis-Daten mithilfe einer der folgenden Persistenzoptionen auf die Festplatte zu kopieren: reguläre Redis Database Backup (RDB)-Momentaufnahmen oder Persistenzprotokolle &quot;Append Only File&quot;(AOF).

- **Redis Database Backup** (RDB) Momentaufnahmen speichern die gesamte Datenbank nach einer bestimmten Zeit in einer Dump-Datei, wenn sich seit der letzten Speicherung eine Mindestanzahl von Schlüsseln geändert hat. Verwenden Sie die `save` -Einstellung in der `redis.conf` -Datei, um diese Einstellung zu konfigurieren.

- **Nur Datei anhängen** (AOF) speichert jeden Schreibvorgang, der an Redis gesendet wird, in einer Journaldatei. Redis liest diese Datei nur beim Neustart und verwendet sie zum Wiederherstellen des ursprünglichen Datensatzes.

Sie können auch die Optionen RDB und AOF gleichzeitig aktivieren. Weitere Informationen, einschließlich der Vor- und Nachteile der Persistenzoptionen, finden Sie im Abschnitt [Dokumentation zur Redis-Persistenz](https://redis.io/topics/persistence).

Richten Sie die Instanz für die Cacheinstanz so ein, dass sie groß genug ist, um Ihren gesamten Commerce-Cache zu speichern. Die Größenanforderungen hängen von verschiedenen Faktoren ab, wie der Anzahl der Produkte und der Store-Ansichten. Als Ausgangspunkt können Sie die Größe des Cache-Ordners in Ihrem Dateisystem verwenden. Wenn beispielsweise die Variable `var/cache` -Ordner in Ihrem Dateisystem 5 GB beträgt, richten Sie Ihre Redis-Instanz mit mindestens 5 GB ein, um zu starten. Für die Cache-Instanz ist keine Persistenz erforderlich, da der Commerce-Cache wiederhergestellt werden kann. Siehe [Handbuch zum Redis-Cache](https://redis.io/docs/manual/eviction/).

Zur Leistungsoptimierung können Sie die folgenden Einstellungen für das asynchrone Löschen aktivieren. Diese Einstellungen ändern das Verhalten von Redis nicht.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

Unter Redis 6.x und höher können Sie auch den folgenden Wert hinzufügen:

```ini
lazyfree-lazy-user-del yes
```
