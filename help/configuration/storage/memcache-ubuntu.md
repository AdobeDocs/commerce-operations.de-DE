---
title: In Ubuntu zwischengespeicherte Einrichtung einrichten
description: Installieren und konfigurieren Sie gecacht auf Ubuntu.
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# In Ubuntu zwischengespeicherte Einrichtung einrichten

In diesem Abschnitt finden Sie Anweisungen zur Installation von gecacht auf Ubuntu.

>[!INFO]
>
>Adobe empfiehlt die Verwendung der gespeicherten Version 3.0.5 oder neuer.

Da PHP keine native Unterstützung für Memcache hat, müssen Sie eine Erweiterung für PHP installieren, um sie zu verwenden. Es sind zwei PHP-Erweiterungen verfügbar, und es ist wichtig, zu dekodieren, welche verwendet werden sollen:

- `memcache` (_no d_) - eine ältere, aber beliebte Erweiterung, die nicht regelmäßig gepflegt wird.
Die Erweiterung `memcache` funktioniert derzeit _nicht_ mit PHP 7. Siehe [PHP-Dokumentation für memcache](https://www.php.net/manual/en/book.memcache.php).

  Der genaue Name ist `php5-memcache` für Ubuntu.

- `memcached` (_mit einem`d`_) - eine neuere und gepflegte Erweiterung, die mit PHP 7 kompatibel ist. Siehe die [PHP-Dokumentation für zwischengespeichert](https://www.php.net/manual/en/book.memcached.php).

  Der genaue Name ist `php5-memcached` für Ubuntu.

## Installieren und konfigurieren Sie gecached auf Ubuntu

**So installieren und konfigurieren Sie gecached auf Ubuntu**:

1. Geben Sie als Benutzer mit `root` -Berechtigungen den folgenden Befehl ein:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Ändern Sie die zwischengespeicherte Konfigurationseinstellung für `CACHESIZE` und `-l`:

   1. Öffnen Sie `/etc/memcached.conf` in einem Texteditor.
   1. Suchen Sie den Parameter `-m` .
   1. Wert auf mindestens `1GB` ändern
   1. Suchen Sie den Parameter `-l` .
   1. Ändern Sie den Wert in `127.0.0.1` oder `localhost`
   1. Speichern Sie Ihre Änderungen in `memcached.conf` und beenden Sie den Texteditor.
   1. Starten Sie die Zwischenspeicherung neu.

      ```bash
      service memcached restart
      ```

1. Starten Sie den Webserver neu.

   Für Apache: `service apache2 restart`

1. Fahren Sie mit dem nächsten Abschnitt fort.

## Überprüfen Sie die zwischengespeicherten Vorgänge vor der Installation von Magento

Adobe empfiehlt, gecachete Tests durchzuführen, um sicherzustellen, dass sie funktionieren, bevor Sie Commerce installieren. Dies dauert nur wenige Minuten und kann die Fehlerbehebung später vereinfachen.

### Überprüfen, ob die zwischengespeicherten Daten vom Webserver erkannt werden

So überprüfen Sie, ob die zwischengespeicherten Daten vom Webserver erkannt werden:

1. Erstellen Sie im Basisverzeichnis des Webservers eine Datei &quot;`phpinfo.php`&quot;:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Rufen Sie diese Seite in Ihrem Webbrowser auf. Beispiel:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Stellen Sie sicher, dass die zwischengespeicherten Anzeigen wie folgt angezeigt werden:

   ![Vergewissern Sie sich, dass die zwischengespeicherten Daten vom Webserver erkannt werden](../../assets/configuration/memcache.png)

   Vergewissern Sie sich, dass Sie die zwischengespeicherte Version 3.0.5 oder höher verwenden.

   Wenn die zwischengespeicherte Seite nicht angezeigt wird, starten Sie den Webserver neu und aktualisieren Sie die Browserseite. Wenn die Erweiterung weiterhin nicht angezeigt wird, überprüfen Sie, ob Sie die Erweiterung `php-pecl-memcached` installiert haben.

### Überprüfen, ob zwischengespeicherte Daten zwischengespeichert werden können

Dieser Test verwendet ein PHP-Skript, um zu überprüfen, ob zwischengespeicherte Cachedaten speichern und abrufen können.

Weitere Informationen zu diesem Test finden Sie im Tutorial [Installieren und Verwenden von Memcache auf Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Erstellen Sie `cache-test.php` im Basisverzeichnis des Webservers mit folgendem Inhalt:

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

Wobei `<memcached hostname or ip>` entweder `localhost`, `127.0.0.1` oder der Memcache-Hostname oder die IP-Adresse ist. Der `<memcached port>` ist der Überwachungsanschluss, standardmäßig `11211`.

Rufen Sie diese Seite in einem Webbrowser auf. Beispiel

```http
http://192.0.2.1/cache-test.php
```

Wenn Sie die Seite zum ersten Mal aufrufen, wird Folgendes angezeigt: `No matching key found. Refresh the browser to add it!`

Aktualisieren Sie den Browser. Die Nachricht ändert sich in `Successfully retrieved the data!`

Schließlich können Sie die memcache-Schlüssel mithilfe von Telnet anzeigen:

```bash
telnet localhost <memcache port>
```

Geben Sie an der Eingabeaufforderung ein.

```shell
stats items
```

Das Ergebnis ähnelt dem folgenden:

```
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

Speicherkapazität leeren und Telnet beenden:

```shell
flush_all
```

```shell
quit
```

[Zusätzliche Informationen zum Telnet-Test](https://darkcoding.net/software/memcached-list-all-keys/)
