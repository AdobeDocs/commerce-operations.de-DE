---
title: Speicherort der Sitzung
description: Erfahren Sie mehr über Sitzungsspeicherorte und Dateiverwaltung in Adobe Commerce. Entdecken Sie Speicherlogik- und Konfigurationsoptionen.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Speicherort der Sitzung

In diesem Thema wird beschrieben, wie Sie den Speicherort für Ihre Sitzungsdateien ermitteln. Das System verwendet die folgende Logik zum Speichern von Sitzungsdateien:

- Wenn Sie memcached konfiguriert haben, werden Sitzungen im RAM gespeichert; siehe [Verwenden von memcached für die Sitzungsspeicherung](memcached.md).
- Wenn Sie Redis konfiguriert haben, werden Sitzungen auf dem Redis-Server gespeichert. Siehe [Verwenden von Redis für die Sitzungsspeicherung](../cache/redis-session.md).
- Wenn Sie den standardmäßigen dateibasierten Sitzungsspeicher verwenden, speichern wir Sitzungen an den folgenden Speicherorten in der angegebenen Reihenfolge:

   1. In [`env.php`](#example-in-envphp) definiertes Verzeichnis
   1. In [`php.ini`](#example-in-phpini) definiertes Verzeichnis
   1. `<magento_root>/var/session`

## Beispiel in `env.php`

Ein Beispiel-Snippet aus `<magento_root>/app/etc/env.php` folgt:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

Im vorherigen Beispiel werden Sitzungsdateien in `/var/www/session` gespeichert

## Beispiel in `php.ini`

Als Benutzer mit `root` Berechtigungen öffnen Sie Ihre `php.ini` und suchen Sie nach dem Wert von `session.save_path`. Dadurch wird angegeben, wo Sitzungen gespeichert werden.

## Sitzungsgröße verwalten

Siehe [Sitzungsverwaltung](https://experienceleague.adobe.com/de/docs/commerce-admin/systems/security/security-session-management) im _Benutzerhandbuch_.

## Konfiguration der automatischen Bereinigung

Um abgelaufene Sitzungen zu bereinigen, ruft das System den `gc`-Handler (_Garbage Collection_) nach dem Zufallsprinzip auf, entsprechend einer Wahrscheinlichkeit, die von der `gc_probability / gc_divisor`-Anweisung berechnet wird. Wenn Sie diese Anweisungen beispielsweise auf `1/100` setzen, bedeutet dies eine Wahrscheinlichkeit von `1%` (_Wahrscheinlichkeit eines Garbage Collection-Aufrufs pro 100 Anfragen_).

Der Garbage Collection-Handler verwendet die `gc_maxlifetime`-Anweisung, d. h. die Anzahl der Sekunden, nach denen die Sitzungen als _Garbage_ angezeigt und möglicherweise bereinigt werden.

Auf einigen Betriebssystemen (Debian/Ubuntu) ist die Standard-`session.gc_probability`-Direktive `0`, die verhindert, dass der Garbage Collection Handler ausgeführt wird.

Sie können die `session.gc_` Anweisungen aus der `php.ini` in der `<magento_root>/app/etc/env.php`-Datei überschreiben:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

Die Konfiguration variiert je nach Traffic und spezifischen Bedürfnissen der Website des Händlers.
