---
title: Einrichten von Memcached unter CentOS
description: Installieren und konfigurieren Sie memcached auf CentOS.
feature: Configuration, Cache, Storage
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Einrichten von Memcached unter CentOS

Dieser Abschnitt enthält Anweisungen zur Installation von memcached unter CentOS. Weitere Informationen finden Sie im [memcached-Wiki](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe empfiehlt, die neueste stabile Version von Memcached zu verwenden (derzeit 3.1.3 für Memcached).

Da PHP keine native Unterstützung für memcache hat, müssen Sie eine Erweiterung für PHP installieren, um es zu verwenden. Es stehen zwei PHP-Erweiterungen zur Verfügung und es ist wichtig zu decodieren welche verwendet werden sollen:

- `memcache` (_kein D_) - eine ältere, aber beliebte Erweiterung, die nicht regelmäßig gepflegt wird.
Die `memcache`-Erweiterung _funktioniert derzeit nicht_ mit PHP 7. Siehe [PHP-Dokumentation für memcache](https://www.php.net/manual/en/book.memcache.php).

  Der genaue Name ist für CentOS `php-pecl-memcache`.

- `memcached` (_mit einem`d`_) - eine neuere und gepflegte Erweiterung, die mit PHP 7 kompatibel ist. Siehe [PHP-Dokumentation für memcached](https://www.php.net/manual/en/book.memcached.php).

  Der genaue Name ist für CentOS `php-pecl-memcached`.

## Installieren und Konfigurieren von Memcached unter CentOS

Um memcached unter CentOS zu installieren, führen Sie die folgenden Aufgaben als Benutzer mit `root` Berechtigungen aus:

1. Installieren Sie memcached und seine Abhängigkeiten:

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >Die Syntax der vorherigen Befehle hängt möglicherweise davon ab, welche Paket-Repositorys Sie verwenden. Wenn Sie beispielsweise webtatic und PHP 5.6 verwenden, geben Sie `yum install -y php56w-pecl-memcache` ein. Verwenden Sie `yum search memcache|grep php` , um den entsprechenden Paketnamen zu finden.


1. Ändern Sie die memcached-Konfigurationseinstellung für `CACHESIZE` und `OPTIONS`:

   1. Öffnen Sie `/etc/sysconfig/memcached` in einem Texteditor.
   1. Suchen Sie den Wert für `CACHESIZE` und ändern Sie ihn auf mindestens 1 GB. Beispiel:

      ```config
      CACHESIZE="1GB"
      ```

   1. Suchen Sie den Wert für `OPTIONS` und ändern Sie ihn in `localhost` oder `127.0.0.1`

1. Speichern Sie Ihre Änderungen in `memcached` und beenden Sie den Texteditor.
1. Starten Sie memcached neu.

   ```bash
   service memcached restart
   ```

1. Starten Sie den Webserver neu.

   Für Apache:

   ```bash
   service httpd restart
   ```

1. Fahren Sie mit dem nächsten Abschnitt fort.

## Überprüfen der Funktionsweise von Memcached vor der Installation von Commerce

Adobe empfiehlt, memcached zu testen, um sicherzustellen, dass es funktioniert, bevor Sie Commerce installieren. Dies dauert nur wenige Minuten und kann die Fehlerbehebung später vereinfachen.

### Überprüfen, ob der zwischengespeicherte Inhalt vom Webserver erkannt wird

So überprüfen Sie, ob Memcached vom Webserver erkannt wird:

1. Erstellen Sie eine `phpinfo.php` Datei im Stammverzeichnis des Webservers:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Navigieren Sie zu dieser Seite in Ihrem Webbrowser.

   Beispiel: `http://192.0.2.1/phpinfo.php`

1. Stellen Sie sicher, dass memcache wie folgt angezeigt wird:

![Bestätigung, dass der memcache vom Webserver erkannt wird](../../assets/configuration/memcache.png)

Stellen Sie sicher, dass Sie memcached Version 3.0.5 oder höher verwenden.

Wenn der memcache nicht angezeigt wird, starten Sie den Webserver neu und aktualisieren Sie die Browser-Seite. Wenn es immer noch nicht angezeigt wird, überprüfen Sie, ob Sie die `php-pecl-memcache`-Erweiterung installiert haben.

### Erstellen Sie einen Memcache-Test, der aus einer MySQL-Datenbank und einem PHP-Skript besteht

Der Test verwendet eine MySQL-Datenbank, -Tabelle und -Daten, um zu überprüfen, ob Sie die Datenbankdaten abrufen und im Memcache speichern können. Ein PHP-Skript durchsucht zunächst den Cache. Wenn das Ergebnis nicht vorhanden ist, fragt das Skript die Datenbank ab. Nachdem die Abfrage von der ursprünglichen Datenbank erfüllt wurde, speichert das Skript das Ergebnis mithilfe des `set`-Befehls im memcache.

[Weitere Details zu diesem Test](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

MySQL-Datenbank erstellen:

```bash
mysql -u root -p
```

Geben Sie an der `mysql` Eingabeaufforderung die folgenden Befehle ein:

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Erstellen Sie `cache-test.php` im Stammverzeichnis Ihres Webservers:

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

Dabei ist `<memcached hostname or ip>` entweder `localhost`, `127.0.0.1` oder der Hostname oder die IP-Adresse des Memcaches. Der `<memcached port>` ist der Listen-Port. Standardmäßig ist dies `11211`.

Führen Sie das Skript über die Befehlszeile aus.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

Das erste Ergebnis ist `got result from mysql`. Das bedeutet, dass der Schlüssel nicht in memcached vorhanden war, sondern von MySQL abgerufen wurde.

Das zweite Ergebnis ist `got result from memcached`, das überprüft, ob der Wert erfolgreich in memcached gespeichert wurde.

Schließlich können Sie die Memcache-Schlüssel mithilfe von Telnet anzeigen:

```bash
telnet localhost <memcache port>
```

Geben Sie bei der Eingabeaufforderung Folgendes ein

```bash
stats items
```

Das Ergebnis ähnelt dem folgenden:

```
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

Leeren Sie den Memcache-Speicher und beenden Sie Telnet:

```bash
flush_all
```

```bash
quit
```

[Zusätzliche Informationen zum Telnet-Test](https://darkcoding.net/software/memcached-list-all-keys/)
