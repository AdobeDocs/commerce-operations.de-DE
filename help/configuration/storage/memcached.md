---
title: Verwenden Sie gecacht für die Sitzungsspeicherung
description: Erfahren Sie mehr über die Verwendung von Memcached für die Commerce-Sitzungsspeicherung.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Verwenden Sie gecacht für die Sitzungsspeicherung

Das gecachete Speichersystem ist ein allgemeines Speicherzwischenspeichersystem. Es wird häufig verwendet, um dynamische datenbankbasierte Websites zu beschleunigen, indem Daten und Objekte im RAM zwischengespeichert werden, um die Häufigkeit zu reduzieren, mit der eine externe Datenquelle (z. B. eine Datenbank oder API) gelesen werden muss.

Die zwischengespeicherten Dateien bieten eine große Hash-Tabelle, die auf mehrere Computer verteilt werden kann. Wenn die Tabelle voll ist, führen nachfolgende Einfügungen dazu, dass ältere Daten in der zuletzt verwendeten Reihenfolge (LRU) gelöscht werden. Dieser Hash-Tisch ist oft sehr groß. (Quelle: [memcached.org](https://www.memcached.org/))

Commerce verwendet die Zwischenspeicherung für die Sitzungsspeicherung, nicht aber für die Seiten-Zwischenspeicherung. Für die Zwischenspeicherung von Seiten wird empfohlen [Redis](../cache/redis-pg-cache.md) oder [Varnisch](../cache/config-varnish.md).

**So konfigurieren Sie Commerce für die Verwendung zwischengespeicherter Inhalte**:

1. Öffnen `<your install dir>/app/etc/env.php` in einem Texteditor.
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

   gecacht hat optionale Startparameter, die über den Rahmen dieses Handbuchs hinausgehen. Weitere Informationen finden Sie im Abschnitt [zwischengespeichert](https://www.php.net/manual/en/memcached.sessions.php) Dokumentation, Quellcode und Änderungen.

1. Fahren Sie mit dem nächsten Abschnitt fort.

**Überprüfen der zwischengespeicherten Funktionsweise mit Commerce**:

1. Löschen Sie den Inhalt der folgenden Ordner unter Ihrem Commerce-Installationsordner:

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Navigieren Sie zu einer beliebigen Seite in der Storefront.

1. Melden Sie sich beim Administrator an und navigieren Sie zu mehreren Seiten.

   Wenn keine Fehler angezeigt werden, gratulieren! Memcached funktioniert! Sie können sich optional den zwischengespeicherten Speicher ansehen, wie im nächsten Schritt beschrieben wird.

   Wenn Fehler angezeigt werden (z. B. HTTP 500 (Interner Server-Fehler), aktivieren Sie den Entwicklermodus und diagnostizieren Sie das Problem. Vergewissern Sie sich, dass die zwischengespeicherten Dateien ausgeführt und ordnungsgemäß konfiguriert werden und dass `env.php` hat keine Syntaxfehler.

1. (Optional.) Verwenden Sie Telnet, um sich den zwischengespeicherten Speicher anzusehen.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   Die Ergebnisse weisen folgendes Format auf:

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
