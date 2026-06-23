---
title: Installieren und Einrichten von Redis
description: Erfahren Sie, wie Sie Redis für Caching und Sitzungsspeicher mit Adobe Commerce installieren und konfigurieren. Entdecken Sie Optionen zur Optimierung und Leistungsoptimierung.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
autotag-review: '2026-06-22T20:26:29.348Z'
TQID: 'https://experienceleague.adobe.com/N61AAy4ihSIlhEjdvpji2XVOdZuHWhytp9zgoAU41K4'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 456
ht-degree: 0%

---

# Installieren und Einrichten von Redis

Redis ist ein In-Memory-Datenspeicher, der als Cache-Backend und zur Sitzungsspeicherung verwendet werden kann. Zu den wichtigsten Funktionen gehören:

- PHP-Sitzungsspeicher
- Tag-basierte Cache-Bereinigung ohne `foreach` Schleifen
- Speicherung auf der Festplatte und Master/Slave-Replikation

{{cloud-cache-config}}

## Installieren von Redis

Die Installation und Konfiguration der Redis-Software sprengt den Rahmen dieses Handbuchs. Anzeige von Ressourcen wie:

- [Redis herunterladen Seite](https://redis.io/download)
- [Redis-Schnellstart](https://redis.io/docs/latest/)
- [Digitaler Ozean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
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
