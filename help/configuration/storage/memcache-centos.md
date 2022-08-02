---
title: In CentOS zwischengespeicherte Einrichtung einrichten
description: Installieren und konfigurieren Sie gecacht auf CentOS.
source-git-commit: 65060d067bbbfe139736df3800688ce897cb17be
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# In CentOS zwischengespeicherte Einrichtung einrichten

In diesem Abschnitt finden Sie Anweisungen zur Installation des gecachten Programms unter CentOS. Weitere Informationen finden Sie im [Wiki zwischengespeichert](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe empfiehlt die Verwendung der neuesten stabilen zwischengespeicherten Version (derzeit 3.1.3 für zwischengespeicherte Version).

Da PHP keine native Unterstützung für Memcache hat, müssen Sie eine Erweiterung für PHP installieren, um sie zu verwenden. Es sind zwei PHP-Erweiterungen verfügbar, und es ist wichtig, zu dekodieren, welche verwendet werden sollen:

- `memcache` (_n d_) - eine ältere, aber beliebte Erweiterung, die nicht regelmäßig gepflegt wird.
Die `memcache` Erweiterung derzeit _nicht_ arbeitet mit PHP 7. Siehe [PHP-Dokumentation für memcache](https://www.php.net/manual/en/book.memcache.php).

   Der genaue Name lautet `php-pecl-memcache` für CentOS.

- `memcached` (_mit`d`_) - eine neuere und gepflegte Erweiterung, die mit PHP 7 kompatibel ist. Siehe [PHP-Dokumentation für zwischengespeicherte](https://www.php.net/manual/en/book.memcached.php).

   Der genaue Name lautet `php-pecl-memcached` für CentOS.

## Installieren und konfigurieren Sie gecacht auf CentOS

Führen Sie die folgenden Aufgaben als Benutzer mit `root` -Berechtigungen:

1. Installieren Sie die zwischengespeicherten Dateien und ihre Abhängigkeiten:

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
   >Die Syntax der vorherigen Befehle hängt möglicherweise davon ab, welche Package-Repositorys Sie verwenden. Wenn Sie beispielsweise WebTatic und PHP 5.6 verwenden, geben Sie `yum install -y php56w-pecl-memcache`. Verwendung `yum search memcache|grep php` , um den entsprechenden Paketnamen zu finden.


1. Ändern Sie die Einstellung der zwischengespeicherten Konfiguration für `CACHESIZE` und `OPTIONS`:

   1. Öffnen `/etc/sysconfig/memcached` in einem Texteditor.
   1. Suchen Sie den Wert für `CACHESIZE` und ändern Sie sie auf mindestens 1 GB. Beispiel:

      ```config
      CACHESIZE="1GB"
      ```

   1. Suchen Sie den Wert für `OPTIONS` und ändern Sie sie in `localhost` oder `127.0.0.1`

1. Speichern Sie Ihre Änderungen in `memcached` und beenden Sie den Texteditor.
1. Starten Sie die Zwischenspeicherung neu.

   ```bash
   service memcached restart
   ```

1. Starten Sie den Webserver neu.

   Für Apache:

   ```bash
   service httpd restart
   ```

1. Fahren Sie mit dem nächsten Abschnitt fort.

## Überprüfen Sie die zwischengespeicherten Vorgänge, bevor Sie Commerce installieren.

Adobe empfiehlt, gecachete Tests durchzuführen, um sicherzustellen, dass sie funktionieren, bevor Sie Commerce installieren. Dies dauert nur wenige Minuten und kann die Fehlerbehebung später vereinfachen.

### Überprüfen, ob die zwischengespeicherten Daten vom Webserver erkannt werden

So überprüfen Sie, ob die zwischengespeicherten Daten vom Webserver erkannt werden:

1. Erstellen Sie eine `phpinfo.php` -Datei im Basisverzeichnis des Webservers:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Rufen Sie diese Seite in Ihrem Webbrowser auf.

   Beispiel: `http://192.0.2.1/phpinfo.php`

1. Stellen Sie sicher, dass Memcache wie folgt angezeigt wird:

![Vergewissern Sie sich, dass der Zwischenspeicher vom Webserver erkannt wird.](../../assets/configuration/memcache.png)

Vergewissern Sie sich, dass Sie die zwischengespeicherte Version 3.0.5 oder höher verwenden.

Wenn memcache nicht angezeigt wird, starten Sie den Webserver neu und aktualisieren Sie die Browserseite. Wenn es immer noch nicht angezeigt wird, überprüfen Sie, ob die `php-pecl-memcache` -Erweiterung.

### Erstellen Sie einen Memcache-Test, der aus einer MySQL-Datenbank und einem PHP-Skript besteht.

Der Test verwendet eine MySQL-Datenbank, eine Tabelle und Daten, um zu überprüfen, ob Sie die Datenbankdaten abrufen und in memcache speichern können. Ein PHP-Skript durchsucht zunächst die [cache](https://glossary.magento.com/cache). Wenn das Ergebnis nicht vorhanden ist, fragt das Skript die Datenbank ab. Nachdem die Abfrage von der ursprünglichen Datenbank erfüllt wurde, speichert das Skript das Ergebnis in memcache, indem es die `set` Befehl.

[Weitere Informationen zu diesem Test](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

Erstellen Sie die MySQL-Datenbank:

```bash
mysql -u root -p
```

Im `mysql` -Eingabeaufforderung die folgenden Befehle eingeben:

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Erstellen `cache-test.php` im Basisverzeichnis Ihres Webservers:

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

Wo `<memcached hostname or ip>` ist `localhost`, `127.0.0.1`oder den Hostnamen oder die IP-Adresse des memcache. Die `<memcached port>` ist der Überwachungsanschluss; standardmäßig `11211`.

Führen Sie das Skript über die Befehlszeile aus.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

Das erste Ergebnis lautet `got result from mysql`. Das bedeutet, dass der Schlüssel nicht im Cache vorhanden war, aber von MySQL abgerufen wurde.

Das zweite Ergebnis lautet `got result from memcached`, wodurch überprüft wird, ob der Wert erfolgreich im Cache gespeichert wurde.

Schließlich können Sie die memcache-Schlüssel mithilfe von Telnet anzeigen:

```bash
telnet localhost <memcache port>
```

Geben Sie an der Eingabeaufforderung ein.

```bash
stats items
```

Das Ergebnis ähnelt dem folgenden:

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

Leeren Sie den Speicher des Memcaches und beenden Sie Telnet:

```bash
flush_all
```

```bash
quit
```

[Zusätzliche Informationen zum Telnet-Test](https://darkcoding.net/software/memcached-list-all-keys/)
