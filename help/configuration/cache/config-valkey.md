---
title: Installieren und Einrichten von Valley
description: Erfahren Sie, wie Sie Valkey für das Caching und die Sitzungsspeicherung mit Adobe Commerce installieren und konfigurieren. Entdecken Sie Optionen zur Optimierung und Leistungsoptimierung.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/de/docs/commerce/user-guides/product-solutions" tooltip="Gilt nur für Adobe Commerce On-Premise-Projekte."
TQID: 'https://experienceleague.adobe.com/Ef4WREy0eq0ChsrI5-0FtrjMZWNjwr7l71Pm-RHD1GI'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
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
source-wordcount: 414
ht-degree: 0%

---

# Installieren und Einrichten von Valley

Valley ist ein Open-Source-Redis-kompatibler In-Memory-Datenspeicher, der als Cache-Backend und für die Sitzungsspeicherung verwendet werden kann. Zu den wichtigsten Funktionen gehören:

- PHP-Sitzungsspeicher
- Tag-basierte Cache-Bereinigung ohne `foreach` Schleifen
- Speicherung auf der Festplatte und Master/Slave-Replikation

{{cloud-cache-config}}

## Valley installieren

Informationen zum Installieren und Konfigurieren der Valley-Software finden Sie in den folgenden Ressourcen:

- [Valley-Seite herunterladen](https://valkey.io/download/){target="_blank"}
- [Valley-Schnellstart](https://valkey.io/topics/quickstart/){target="_blank"}
- [Valley-Dokumentationsseite](https://valkey.io/docs){target="_blank"}

## Einrichten der Valley-Konfiguration

Abhängig von Ihrer Installation finden Sie Ihre Valkey-Konfiguration in der Regel entweder in der `/etc/valkey/valkey.conf`-Datei oder in der `/etc/valkey/<port>.conf`-Datei.

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
