---
title: Speicherort der Sitzung
description: Erfahren Sie, wo die Sitzungsdateien gespeichert sind.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Speicherort der Sitzung

In diesem Thema wird erläutert, wie Sie ermitteln können, wo Ihre Sitzungsdateien gespeichert sind. Das System verwendet die folgende Logik zum Speichern von Sitzungsdateien:

- Wenn Sie die Zwischenspeicherung konfiguriert haben, werden Sitzungen im RAM gespeichert; siehe [Verwenden Sie gecacht für die Sitzungsspeicherung](memcached.md).
- Wenn Sie Redis konfiguriert haben, werden Sitzungen auf dem Redis-Server gespeichert, siehe [Verwenden von Redizes für die Sitzungsspeicherung](../cache/redis-session.md).
- Wenn Sie den standardmäßigen dateibasierten Sitzungsspeicher verwenden, werden Sitzungen an den folgenden Speicherorten in der angegebenen Reihenfolge gespeichert:

   1. Verzeichnis definiert in [`env.php`](#example-in-envphp)
   1. Verzeichnis definiert in [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directory

## Beispiel in `env.php`

Ein Beispielausschnitt aus `<magento_root>/app/etc/env.php` folgt:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

Das obige Beispiel speichert Sitzungsdateien in `/var/www/session`

## Beispiel in `php.ini`

Als Benutzer mit `root` Berechtigungen, öffnen Sie Ihre `php.ini` Datei und suchen Sie nach dem Wert von `session.save_path`. Dadurch wird ermittelt, wo Sitzungen gespeichert werden.

## Sitzungsgröße verwalten

Siehe [Sitzungsverwaltung](https://docs.magento.com/user-guide/stores/security-session-management.html) im _Benutzerhandbuch_.

## Speicherbereinigungskonfiguration

Um abgelaufene Sitzungen zu bereinigen, ruft das System die `gc` (_Abfallsammlung_)-Handler zufällig nach einer Wahrscheinlichkeit, die von der `gc_probability / gc_divisor` Richtlinie. Wenn Sie diese Anweisungen beispielsweise auf `1/100` bzw. bedeutet dies eine Wahrscheinlichkeit von `1%` (_Wahrscheinlichkeit eines Speicherbereinigungsaufrufs pro 100 Anforderungen_).

Der Bereinigungs-Handler verwendet die `gc_maxlifetime` -Anweisung - die Anzahl der Sekunden, nach denen die Sitzungen als _Müll_ und möglicherweise bereinigt.

Auf einigen Betriebssystemen (Debian/Ubuntu) ist die Standardeinstellung `session.gc_probability` Richtlinie `0`, wodurch verhindert wird, dass der Bereinigungs-Handler ausgeführt wird.

Sie können die `session.gc_` Richtlinien der `php.ini` in der Datei `<magento_root>/app/etc/env.php` Datei:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

Die Konfiguration variiert je nach Traffic und den spezifischen Bedürfnissen der Website des Händlers.
