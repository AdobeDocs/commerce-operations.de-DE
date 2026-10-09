---
title: Memcached für Sitzungsspeicherung verwenden
description: Erfahren Sie, wie Sie Adobe Commerce für die Verwendung von memcached für die Sitzungsspeicherung in env.php konfigurieren und wann Sie Redis oder Varnish für andere Caching-Ebenen bevorzugen.
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%
---
# Memcached für Sitzungsspeicherung verwenden

Memcached ist ein universelles, verteiltes Speicher-Caching-System. Es wird häufig verwendet, um dynamische datenbankgesteuerte Websites zu beschleunigen, indem Daten und Objekte im RAM zwischengespeichert werden, um die Anzahl der Lesevorgänge für eine externe Datenquelle (z. B. eine Datenbank oder API) zu reduzieren.

Memcached bietet eine große Hash-Tabelle, die auf mehrere Computer verteilt werden kann. Wenn die Tabelle voll ist, führen nachfolgende Einfügungen dazu, dass ältere Daten in der Reihenfolge der am wenigsten verwendeten (LRU) bereinigt werden. Die Größe dieser Hash-Tabelle ist häufig sehr groß. (Source: [memcached.org](https://www.memcached.org/))

Commerce verwendet memcached für die Sitzungsspeicherung, aber nicht für die Seitenzwischenspeicherung. Für das Zwischenspeichern von Seiten empfehlen wir [Redis](../cache/redis-pg-cache.md) oder [Varnish](../cache/config-varnish.md).

**So konfigurieren Sie Commerce für die Verwendung von memcached**:

1. Öffnen Sie `<your install dir>/app/etc/env.php` in einem Texteditor.
1. Suchen Sie Folgendes:

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. Ändern Sie sie wie folgt:

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   Memcached verfügt über optionale Startparameter, die den Rahmen dieses Handbuchs sprengen. Weitere Informationen dazu finden Sie in der [memcached](https://www.php.net/manual/en/memcached.sessions.php)-Dokumentation, im Quell-Code und in den Änderungsprotokollen.

1. Fahren Sie mit dem nächsten Abschnitt fort.

**So überprüfen Sie, ob memcached mit Commerce funktioniert**:

1. Löschen Sie den Inhalt der folgenden Ordner unter Ihrem Commerce-Installationsverzeichnis:

   ```shell
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Zu einer beliebigen Seite der Storefront gehen.

1. Melden Sie sich bei Admin an und navigieren Sie zu mehreren Seiten.

   Wenn keine Fehler angezeigt werden, herzlichen Glückwunsch! Memcached funktioniert! Optional können Sie sich den memcached-Speicher ansehen, wie im nächsten Schritt beschrieben.

   Wenn Fehler angezeigt werden (z. B. HTTP 500 (Interner Server-Fehler), aktivieren Sie den Entwicklermodus und diagnostizieren Sie das Problem. Stellen Sie sicher, dass memcached ausgeführt und ordnungsgemäß konfiguriert wird und dass `env.php` keine Syntaxfehler aufweist.

1. (Optional) Verwenden Sie Telnet, um einen Blick auf den Memcached-Speicher zu werfen.

   ```shell
   telnet <memcached host or ip> <memcached port>
   ```

   ```shell
   stats items
   ```

   Die Ergebnisse werden in etwa wie folgt angezeigt:

   ```text
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
