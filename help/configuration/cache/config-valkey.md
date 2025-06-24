---
title: Konfigurieren von Valley
description: Verschaffen Sie sich einen Überblick über die Funktionen von Valley und starten Sie Ihre Valley-Konfiguration.
feature: Configuration, Cache
source-git-commit: 1850301e0b7f1abbc54613209940dd63d16ef145
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Konfigurieren von Valley

Zu den wichtigsten Funktionen von Valley gehören:

- PHP-Sitzungsspeicher
- Tag-basierte Cache-Bereinigung ohne `foreach` Schleifen
- Speicherung auf der Festplatte und Master/Slave-Replikation

## Valley installieren

Informationen zum Installieren und Konfigurieren der Valley-Software finden Sie in den folgenden Ressourcen:

- [Valkey-Seite herunterladen](https://valkey.io/download/)
- [Valkey-Schnellstart](https://valkey.io/topics/quickstart/)
- [Valkey-Dokumentationsseite](https://valkey.io/docs)

## Einrichten der Valley-Konfiguration

Abhängig von Ihrer Installation finden Sie Ihre Valkey-Konfiguration in der Regel entweder in `/etc/valkey/valkey.conf` oder `/etc/valkey/<port>.conf`.

Um die Valkey-Instanz für Ihre Anforderungen zu optimieren, können Sie die besten Ergebnisse erzielen, indem Sie für jede Sitzung eine dedizierte Instanz, Commerce-Cache und FPC verwenden.

Adobe empfiehlt, Persistenz für Sitzungen zu aktivieren, um Valkey-Daten auf die Festplatte zu kopieren. Sie können entweder Snapshots von Valley Database Backup (RDB) oder Persistenzprotokolle für Nur-Datei-Append (AOF) verwenden.

- **RDB**-Snapshots (Valkey-Datenbank) speichern die vollständige Datenbank nach einer bestimmten Zeit, wenn sich eine Mindestanzahl von Schlüsseln seit dem letzten Speichern geändert hat, in einer Dump-Datei. Verwenden Sie die `save` in der `valkey.conf`, um diese Einstellung zu konfigurieren.

- **Append Only File** (AOF) speichert jeden Schreibvorgang, der an Valkey gesendet wird, in einer Journaldatei. Valley liest diese Datei nur beim Neustart und verwendet sie zum Wiederherstellen des ursprünglichen Datensatzes.

Sie können auch die Optionen RDB und AOF gleichzeitig aktivieren. Weitere Informationen einschließlich der Vor- und Nachteile der Persistenzoptionen finden Sie in der [Valkey Persistence-Dokumentation](https://valkey.io/topics/persistence/).

Richten Sie für die Cache-Instanz die -Instanz so ein, dass sie groß genug ist, um den gesamten Commerce-Cache zu speichern. Die Größenanforderungen hängen von verschiedenen Faktoren ab, z. B. der Anzahl der Produkte und den Ansichten des Geschäfts. Als Ausgangspunkt können Sie die Größe des Cache-Ordners in Ihrem Dateisystem verwenden. Wenn der `var/cache` Ordner auf Ihrem Dateisystem beispielsweise 5 GB beträgt, richten Sie Ihre Valkey-Instanz mit mindestens 5 GB ein, um zu starten. Persistenz ist für die Cache-Instanz nicht erforderlich, da der Commerce-Cache wiederhergestellt werden kann.

Zur Leistungsoptimierung können Sie die folgenden Einstellungen für das asynchrone Löschen aktivieren. Diese Einstellungen ändern das Verhalten von Valley nicht.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
