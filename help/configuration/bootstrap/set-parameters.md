---
title: Festlegen des Werts von Bootstrap-Parametern
description: Erfahren Sie, wie Sie Bootstrap-Parameter für das Commerce-Programm festlegen.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 1%

---

# Bootstrap-Parameter

Dieses Thema zeigt, wie Sie die Werte der Bootstrap-Parameter von Commerce-Anwendungen festlegen. Siehe [Übersicht über Anwendungsinitialisierung und Bootstrapping](initialization.md).

In der folgenden Tabelle werden die Bootstrap-Parameter erläutert, die Sie festlegen können:

| Bootstrap-Parameter | Beschreibung |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Gibt benutzerdefinierte Verzeichnis- und URL-Pfade an |
| MAGE_PROFILER | Aktiviert Abhängigkeitsdiagramme und HTML-Profilerstellung |

>[!INFO]
>
>- Nicht alle Bootstrap-Parameter sind dokumentiert.
>- Sie können jetzt den Anwendungsmodus (Entwickler, Standard, Produktion) mit dem Befehl [`magento deploy:mode:set {mode}`](../cli/set-mode.md) festlegen.

## Festlegen von Parametern mithilfe einer Umgebungsvariablen

In diesem Abschnitt wird beschrieben, wie Sie die Werte von Bootstrap-Parametern mithilfe von Umgebungsvariablen festlegen.

### Festlegen des Anwendungsmodus

Sie können Bootstrap-Variablen als systemweite Umgebungsvariablen angeben, wodurch alle Prozesse sie verwenden können.

Beispielsweise können Sie mit der `MAGE_PROFILER`-Umgebungsvariablen einen Modus wie folgt angeben:

```
MAGE_PROFILER={firebug|csv|<custom value>}
```

Legen Sie die Variable mithilfe eines Shell-spezifischen Befehls fest. Da Shell unterschiedliche Syntax haben, sollten Sie einen Verweis wie [unix.stackexchange.com][unix-stackx] heranziehen.

Bash-Shell-Beispiel für CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Wenn nach dem Festlegen eines Profilerwerts im Browser ein `PHP Fatal error` angezeigt wird, starten Sie den Webserver neu. Der Grund könnte mit dem PHP Bytecode Caching zusammenhängen, das Bytecodes und PHP-Klassenpfade zwischenspeichert.

## Festlegen von Parametern für Apache oder Nginx

In diesem Abschnitt wird beschrieben, wie Sie den Modus für Apache oder Nginx angeben.

### Nginx-Einstellung

Siehe die [Nginx-Beispielkonfiguration] auf _GitHub_.

### Apache .htaccess-Einstellung

Eine Möglichkeit, den Anwendungsmodus festzulegen, besteht darin, `.htaccess` zu bearbeiten. Auf diese Weise müssen Sie die Apache-Einstellungen nicht ändern.

Je nach Einstiegspunkt für das Commerce-Programm können Sie `.htaccess` an jedem der folgenden Speicherorte ändern:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**So legen Sie eine Variable**:

1. Öffnen Sie eine der zuvor genannten Dateien in einem Texteditor und fügen Sie die gewünschte Einstellung hinzu oder heben Sie die Auskommentierung auf.

   Um beispielsweise einen „Modus[ anzugeben, heben ](application-modes.md) den Kommentar für Folgendes auf:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Legen Sie den Wert von `MAGE_PROFILER` auf einen der folgenden Werte fest:

   ```
   firebug
   csvfile
   <custom value>
   ```

1. Speichern Sie Ihre Änderungen in `.htaccess`. Sie müssen Apache nicht neu starten, damit die Änderungen wirksam werden.

### Apache-Einstellung

Der Apache-Webserver unterstützt das Festlegen des Anwendungsmodus mithilfe von `mod_env`-Anweisungen.

Die Apache `mod_env`-Direktive unterscheidet sich geringfügig von [Apache-Version 2.2] und [Apache-Version 2.4].

Die folgenden Verfahren zeigen, wie Sie den Anwendungsmodus in einem virtuellen Apache-Host festlegen. Dies ist nicht die einzige Möglichkeit, `mod_env` Anweisungen zu verwenden. Weitere Informationen finden Sie in der Apache-Dokumentation .

>[!TIP]
>
>Im folgenden Abschnitt wird davon ausgegangen, dass Sie Ihren virtuellen Host bereits eingerichtet haben. Andernfalls finden Sie weitere Informationen in einer Ressource wie [diesem DigitalOcean-Tutorial](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**So geben Sie eine Bootstrap-Variable für Apache auf Ubuntu an**:

1. Als Benutzer mit `root` Berechtigungen können Sie Ihre Konfigurationsdatei für virtuelle Hosts in einem Texteditor öffnen.

   Wenn Ihr virtueller Host beispielsweise `my.magento` heißt,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. Fügen Sie an einer beliebigen Stelle in der Konfiguration des virtuellen Hosts die folgende Zeile hinzu:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Beispiel:

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.
1. Aktivieren Sie Ihren virtuellen Host, falls noch nicht geschehen:

   ```bash
   a2ensite <virtual host config file name>
   ```

   Beispiel:

   ```bash
   a2ensite my.magento.conf
   ```

1. Starten Sie den Webserver neu, nachdem Sie den Modus festgelegt haben:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>In diesem Abschnitt wird davon ausgegangen, dass Sie Ihren virtuellen Host bereits eingerichtet haben. Andernfalls finden Sie weitere Informationen in einer Ressource wie [diesem DigitalOcean-Tutorial](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**So geben Sie eine Bootstrap-Variable für Apache unter CentOS an**:

1. Wenn Sie ein Benutzer mit `root` Berechtigungen sind, öffnen Sie `/etc/httpd/conf/httpd.conf` in einem Texteditor.

1. Fügen Sie an einer beliebigen Stelle in der Konfiguration des virtuellen Hosts die folgende Zeile hinzu:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Beispiel:

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.

1. Starten Sie den Webserver neu, nachdem Sie den Modus festgelegt haben:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache Version 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache-Version 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx-Beispielkonfiguration]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
