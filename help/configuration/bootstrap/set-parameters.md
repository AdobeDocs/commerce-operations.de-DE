---
title: Wert der Bootstrap-Parameter festlegen
description: Erfahren Sie, wie Sie Bootstrap-Parameter für die Commerce-Anwendung festlegen.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---


# Bootstrap-Parameter

In diesem Thema wird gezeigt, wie die Werte von Commerce-Anwendungs-Bootstrap-Parametern festgelegt werden. Siehe [Übersicht über die Anwendungsinitialisierung und das Bootstrapping](initialization.md).

In der folgenden Tabelle werden die Bootstrap-Parameter erläutert, die Sie festlegen können:

| Bootstrap-Parameter | Beschreibung |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Gibt benutzerdefinierte Ordner- und URL-Pfade an |
| MAGE_PROFILER | Ermöglicht Abhängigkeitsdiagramme und HTML-Profiling |

>[!INFO]
>
>- Nicht alle Bootstrap-Parameter werden dokumentiert.
>- Sie legen nun den Anwendungsmodus (Entwickler, Standard, Produktion) mithilfe der [`magento deploy:mode:set {mode}`](../cli/set-mode.md) Befehl.


## Festlegen von Parametern mithilfe einer Umgebungsvariablen

In diesem Abschnitt wird beschrieben, wie Sie die Werte von Bootstrap-Parametern mithilfe von Umgebungsvariablen festlegen.

### Anwendungsmodus festlegen

Sie können Bootstrap-Variablen als systemweite Umgebungsvariablen angeben, die es allen Prozessen ermöglichen, sie zu verwenden.

Sie können beispielsweise die `MAGE_PROFILER` Systemumgebungsvariable, um einen Modus wie folgt anzugeben:

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

Legen Sie die -Variable mithilfe eines Shell-spezifischen Befehls fest. Da Muscheln eine andere Syntax haben, sollten Sie einen Verweis wie [unix.stackexchange.com][unix-stackx].

Bash-Shell-Beispiel für CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Wenn eine `PHP Fatal error` im Browser angezeigt wird, nachdem Sie einen Profiler-Wert festgelegt haben, starten Sie Ihren Webserver neu. Der Grund könnte mit dem PHP Bytecode-Caching zusammenhängen, das Bytecodes und PHP-Klassenbilder zwischenspeichert.

## Parameter für Apache oder Nginx festlegen

In diesem Abschnitt wird beschrieben, wie Sie den Modus für Apache oder Nginx festlegen.

### Nginx-Einstellung

Siehe [Nginx-Beispielkonfiguration] on _GitHub_.

### Zugriffseinstellung für Apache .html

Eine Möglichkeit, den Anwendungsmodus festzulegen, besteht darin, `.htaccess`. Auf diese Weise müssen Sie keine Apache-Einstellungen ändern.

Sie können `.htaccess` an einem der folgenden Speicherorte, je nach Einstiegspunkt in die Commerce-Anwendung:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**So legen Sie eine Variable fest**:

1. Öffnen Sie eine der vorangehenden Dateien in einem Texteditor und fügen Sie die gewünschte Einstellung hinzu oder heben Sie den Kommentar auf.

   Um beispielsweise eine [mode](application-modes.md), heben Sie den Kommentar für Folgendes auf:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Legen Sie den Wert von `MAGE_PROFILER` auf einen der folgenden Werte:

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. Speichern Sie Ihre Änderungen in `.htaccess`; Sie müssen Apache nicht neu starten, damit die Änderung wirksam wird.

### Apache-Einstellung

Der Apache-Webserver unterstützt das Festlegen des Anwendungsmodus mithilfe von `mod_env` Richtlinien.

Der Apache `mod_env` -Direktive unterscheidet sich geringfügig von [Apache-Version 2.2] und [Apache-Version 2.4].

Die folgenden Verfahren zeigen, wie der Anwendungsmodus in einem virtuellen Apache-Host festgelegt wird. Dies ist nicht die einzige Möglichkeit, `mod_env` Richtlinien; Weitere Informationen finden Sie in der Apache-Dokumentation .

>[!TIP]
>
>Im folgenden Abschnitt wird davon ausgegangen, dass Sie Ihren virtuellen Host bereits eingerichtet haben. Wenn nicht, konsultieren Sie eine Ressource wie [dieses DigitalOcean-Tutorial](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**So legen Sie eine Bootstrap-Variable für Apache auf Ubuntu fest**:

1. Als Benutzer mit `root` -Berechtigungen verwenden, öffnen Sie die Konfigurationsdatei des virtuellen Hosts in einem Texteditor.

   Wenn Ihr virtueller Host beispielsweise `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. Fügen Sie an beliebiger Stelle in der Konfiguration des virtuellen Hosts die folgende Zeile hinzu:

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

1. Starten Sie nach dem Festlegen des Modus den Webserver neu:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>In diesem Abschnitt wird davon ausgegangen, dass Sie Ihren virtuellen Host bereits eingerichtet haben. Wenn nicht, konsultieren Sie eine Ressource wie [dieses DigitalOcean-Tutorial](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**So legen Sie eine Bootstrap-Variable für Apache unter CentOS fest**:

1. Als Benutzer mit `root` Berechtigungen, öffnen `/etc/httpd/conf/httpd.conf` in einem Texteditor.

1. Fügen Sie an beliebiger Stelle in der Konfiguration des virtuellen Hosts die folgende Zeile hinzu:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Beispiel:

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Speichern Sie Ihre Änderungen und beenden Sie den Texteditor.

1. Starten Sie nach dem Festlegen des Modus den Webserver neu:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

<!-- link definitions -->

[Apache-Version 2.2]: http://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache-Version 2.4]: http://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx-Beispielkonfiguration]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
