---
title: Speicherort der Sitzung
description: Erfahren Sie, wo die Sitzungsdateien gespeichert sind.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Speicherort der Sitzung

In diesem Thema wird erläutert, wie Sie ermitteln können, wo Ihre Sitzungsdateien gespeichert sind. Das System verwendet die folgende Logik zum Speichern von Sitzungsdateien:

- Wenn Sie die Zwischenspeicherung konfiguriert haben, werden Sitzungen im RAM gespeichert. Siehe [Speicherinformationen für Sitzungen verwenden](memcached.md).
- Wenn Sie Redis konfiguriert haben, werden Sitzungen auf dem Redis-Server gespeichert. Siehe [Verwenden von Redis für die Sitzungsspeicherung](../cache/redis-session.md).
- Wenn Sie den standardmäßigen dateibasierten Sitzungsspeicher verwenden, werden Sitzungen an den folgenden Speicherorten in der angegebenen Reihenfolge gespeichert:

   1. Verzeichnis definiert in [`env.php`](#example-in-envphp)
   1. Verzeichnis definiert in [`php.ini`](#example-in-phpini)
   1. Verzeichnis `<magento_root>/var/session`

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

Als Benutzer mit `root` -Berechtigungen öffnen Sie Ihre `php.ini` -Datei und suchen Sie nach dem Wert von `session.save_path`. Dadurch wird ermittelt, wo Sitzungen gespeichert werden.

## Sitzungsgröße verwalten

Weitere Informationen finden Sie unter [Sitzungsverwaltung](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management) im _Benutzerhandbuch_.

## Speicherbereinigungskonfiguration

Um abgelaufene Sitzungen zu bereinigen, ruft das System den Handler `gc` (_Garbage Collection_) zufällig gemäß einer Wahrscheinlichkeit auf, die von der Anweisung `gc_probability / gc_divisor` berechnet wird. Wenn Sie diese Anweisungen beispielsweise auf `1/100` setzen, bedeutet dies eine Wahrscheinlichkeit von `1%` (_Wahrscheinlichkeit eines Speicherbereinigungsaufrufs pro 100 Anforderungen_).

Der Bereinigungs-Handler verwendet die `gc_maxlifetime` -Direktive, d. h. die Anzahl der Sekunden, nach denen die Sitzungen als _Müll_ betrachtet und möglicherweise bereinigt werden.

Auf einigen Betriebssystemen (Debian/Ubuntu) ist die standardmäßige `session.gc_probability` -Direktive `0`, was verhindert, dass der Garbage Collection Handler ausgeführt wird.

Sie können die `session.gc_`-Anweisungen aus der `php.ini`-Datei in der `<magento_root>/app/etc/env.php`-Datei überschreiben:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

Die Konfiguration variiert je nach Traffic und den spezifischen Bedürfnissen der Website des Händlers.
