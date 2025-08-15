---
title: Einrichten von Memcaches auf Ubuntu
description: Installieren und konfigurieren Sie memcached auf Ubuntu.
feature: Configuration, Cache, Storage
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Einrichten von Memcaches auf Ubuntu

Dieser Abschnitt enthält Anweisungen zur Installation von memcached auf Ubuntu.

>[!INFO]
>
>Adobe empfiehlt die Verwendung von Memcached Version 3.0.5 oder höher.

Da PHP keine native Unterstützung für memcache hat, müssen Sie eine Erweiterung für PHP installieren, um es zu verwenden. Es stehen zwei PHP-Erweiterungen zur Verfügung und es ist wichtig zu decodieren welche verwendet werden sollen:

- `memcache` (_kein D_) - eine ältere, aber beliebte Erweiterung, die nicht regelmäßig gepflegt wird.
Die `memcache`-Erweiterung _funktioniert derzeit nicht_ mit PHP 7. Siehe [PHP-Dokumentation für memcache](https://www.php.net/manual/en/book.memcache.php).

  Der genaue Name ist für Ubuntu `php5-memcache`.

- `memcached` (_mit einem`d`_) - eine neuere und gepflegte Erweiterung, die mit PHP 7 kompatibel ist. Siehe [PHP-Dokumentation für memcached](https://www.php.net/manual/en/book.memcached.php).

  Der genaue Name ist für Ubuntu `php5-memcached`.

## Installieren und Konfigurieren von Memcached auf Ubuntu

**So installieren und konfigurieren Sie memcached auf Ubuntu**:

1. Geben Sie als Benutzer mit `root` Berechtigungen den folgenden Befehl ein:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Ändern Sie die memcached-Konfigurationseinstellung für `CACHESIZE` und `-l`:

   1. Öffnen Sie `/etc/memcached.conf` in einem Texteditor.
   1. Suchen Sie den `-m`.
   1. Ändern Sie den Wert in mindestens `1GB`
   1. Suchen Sie den `-l`.
   1. Ändern Sie den Wert in `127.0.0.1` oder `localhost`
   1. Speichern Sie Ihre Änderungen in `memcached.conf` und beenden Sie den Texteditor.
   1. Starten Sie memcached neu.

      ```bash
      service memcached restart
      ```

1. Starten Sie den Webserver neu.

   Für Apache, `service apache2 restart`

1. Fahren Sie mit dem nächsten Abschnitt fort.

## Überprüfen der Funktionsweise von Memcached vor der Installation von Magento

Adobe empfiehlt, Memcached zu testen, um vor der Installation von Commerce sicherzustellen, dass es funktioniert. Dies dauert nur wenige Minuten und kann die Fehlerbehebung später vereinfachen.

### Überprüfen, ob der zwischengespeicherte Inhalt vom Webserver erkannt wird

So überprüfen Sie, ob Memcached vom Webserver erkannt wird:

1. Erstellen Sie eine `phpinfo.php` Datei im Stammverzeichnis des Webservers:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Navigieren Sie zu dieser Seite in Ihrem Webbrowser. Beispiel:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Stellen Sie sicher, dass memcached wie folgt angezeigt wird:

   ![Bestätigen Sie, dass der zwischengespeicherte Ordner vom Webserver erkannt wird](../../assets/configuration/memcache.png)

   Stellen Sie sicher, dass Sie memcached Version 3.0.5 oder höher verwenden.

   Wenn memcached nicht angezeigt wird, starten Sie den Webserver neu und aktualisieren Sie die Browser-Seite. Wenn es immer noch nicht angezeigt wird, überprüfen Sie, ob Sie die `php-pecl-memcached`-Erweiterung installiert haben.

### Überprüfen, ob zwischengespeicherte Daten zwischengespeichert werden können

Dieser Test verwendet ein PHP-Skript, um zu überprüfen, ob memcached Cache-Daten speichern und abrufen kann.

Weitere Informationen zu diesem Test finden Sie im Tutorial [Installieren und Verwenden von Memcache auf Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Erstellen Sie `cache-test.php` im Stammverzeichnis des Webservers mit folgendem Inhalt:

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

Dabei ist `<memcached hostname or ip>` entweder `localhost`, `127.0.0.1` oder der Hostname oder die IP-Adresse des Memcaches. Der `<memcached port>` ist der Listen-Port. Standardmäßig ist dies `11211`.

Wechseln Sie zu dieser Seite in einem Webbrowser. Beispiel

```http
http://192.0.2.1/cache-test.php
```

Wenn Sie das erste Mal zur Seite gehen, wird Folgendes angezeigt: `No matching key found. Refresh the browser to add it!`

Aktualisieren Sie den Browser. Die Nachricht ändert sich in `Successfully retrieved the data!`

Schließlich können Sie die Memcache-Schlüssel mithilfe von Telnet anzeigen:

```bash
telnet localhost <memcache port>
```

Geben Sie bei der Eingabeaufforderung Folgendes ein

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

Leeren des zwischengespeicherten Speichers und Beenden von Telnet:

```shell
flush_all
```

```shell
quit
```

[Zusätzliche Informationen zum Telnet-Test](https://darkcoding.net/software/memcached-list-all-keys/)
