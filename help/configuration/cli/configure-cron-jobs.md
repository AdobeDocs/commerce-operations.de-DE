---
title: Konfigurieren und Ausführen von Cron-Aufträgen
description: Erfahren Sie, wie Sie Cron-Aufträge verwalten.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 0%

---


# Konfigurieren von Cron-Aufträgen

{{file-system-owner}}

Mehrere Commerce-Funktionen erfordern mindestens einen Cron-Auftrag, der Aktivitäten für die Zukunft plant. Eine teilweise Liste dieser Aktivitäten folgt:

- Katalogpreisregeln
- Newsletter
- Erstellen von Google Sitemaps
- Kundenwarnungen/Benachrichtigungen (Produktpreisänderung, Produkt wieder auf Lager)
- Neuindizierung
- Private Verkäufe (nur Adobe Commerce)
- Automatische Aktualisierung der Währungskurse
- Alle Commerce-E-Mails (einschließlich Bestellbestätigung und -transaktionen)

>[!WARNING]
>
>Sie können `dev/tools/cron.sh` weil das Skript entfernt wurde.

>[!INFO]
>
>Für viele wichtige Systemfunktionen, einschließlich Indizierung, hängt der Handel von der richtigen Cron-Auftragskonfiguration ab. Wird sie nicht ordnungsgemäß eingerichtet, funktioniert Commerce nicht erwartungsgemäß.

UNIX-Systeme planen Aufgaben, die von bestimmten Benutzern mit einer _crontab_, eine Datei, die Anweisungen für den Cron-Daemon enthält, der dem Daemon tatsächlich anweist, diesen Befehl zu diesem Zeitpunkt an diesem Datum auszuführen. Jeder Benutzer verfügt über eine eigene Registerkarte und Befehle in jeder beliebigen Registerkarte werden als der Benutzer ausgeführt, dem die Registerkarte gehört.

Informationen zum Ausführen von Cron in einem Webbrowser finden Sie unter [Sichere cron.php für die Ausführung im Browser](../security/secure-cron-php.md).

## Erstellen oder Entfernen der Registerkarte &quot;Commerce&quot;

In diesem Abschnitt wird beschrieben, wie Sie Ihre Commerce-Crontab (d. h. die Konfiguration für Commerce-Cron-Aufträge) erstellen oder entfernen.

Die _crontab_ ist die Konfiguration, die zum Ausführen von Cron-Aufträgen verwendet wird.

Die Commerce-Anwendung verwendet Cron-Aufgaben, die mit verschiedenen Konfigurationen ausgeführt werden können. Die PHP-Befehlszeilenkonfiguration steuert den allgemeinen Cron-Auftrag, der Indexer neu indiziert, E-Mails generiert, die Sitemap generiert und so weiter.

>[!WARNING]
>
>- Um Probleme während der Installation und Aktualisierung zu vermeiden, empfehlen wir dringend, die gleichen PHP-Einstellungen sowohl auf die PHP-Befehlszeilenkonfiguration als auch auf die Konfiguration des PHP-Webserver-Plug-ins anzuwenden. Weitere Informationen finden Sie unter [Erforderliche PHP-Einstellungen](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html).
>- In einem System mit mehreren Knoten kann crontab nur auf einem Knoten ausgeführt werden. Dies gilt nur für Sie, wenn Sie aus Gründen der Leistung oder Skalierbarkeit mehr als einen Webknoten einrichten.


### Erstellen der Commerce-Registerkarte

Ab Version 2.2 erstellt Commerce eine Crontab für Sie. Wir fügen die Commerce-Crontab zu jedem konfigurierten Crontab für den Eigentümer des Commerce-Dateisystems hinzu. Wenn Sie also bereits Registerkarten für andere Erweiterungen oder Anwendungen eingerichtet haben, fügen wir die Registerkarte &quot;Commerce&quot;hinzu.

Die Registerkarte &quot;Commerce&quot;befindet sich in `#~ MAGENTO START` und `#~ MAGENTO END` Kommentare in der Registerkarte &quot;Kronen&quot;.

So erstellen Sie die Registerkarte &quot;Commerce&quot;:

1. Melden Sie sich bei der [Dateisysteminhaber](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Wechseln Sie zum Installationsverzeichnis für Commerce.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   bin/magento cron:install [--force]
   ```

Verwendung `--force` , um eine vorhandene Registerkarte neu zu schreiben.

>[!INFO]
>
>- `magento cron:install` schreibt keine vorhandene Registerkarte in `#~ MAGENTO START` und `#~ MAGENTO END` Kommentare in der Registerkarte &quot;Kronen&quot;.
>- `magento cron:install --force` hat keine Auswirkungen auf Cron-Aufträge außerhalb der Commerce-Kommentare.


Um die Registerkarte &quot;crontab&quot;anzuzeigen, geben Sie den folgenden Befehl als Dateisysteminhaber ein:

```bash
crontab -l
```

Beispiel:

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>Die `update/cron.php` -Datei in Commerce 2.4.0 entfernt wurde. Wenn diese Datei in Ihrer Installation vorhanden ist, kann sie sicher entfernt werden.
>
>Jeder Verweis auf `update/cron.php` und `bin/magento setup:cron:run` sollte auch aus dem Crontab entfernt werden.&quot;

### Entfernen Sie die Registerkarte &quot;Commerce&quot;

Sie sollten die Registerkarte &quot;Commerce&quot;nur entfernen, bevor Sie die Commerce-Anwendung deinstallieren.

So entfernen Sie die Commerce-Registerkarte:

1. Melden Sie sich als an oder wechseln Sie zu [Dateisysteminhaber](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Wechseln Sie zum Installationsverzeichnis für Commerce.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Dieser Befehl hat keine Auswirkungen auf Cron-Aufträge außerhalb der `#~ MAGENTO START` und `#~ MAGENTO END` Kommentare in der Registerkarte &quot;Kronen&quot;.

## Ausführen von cron über die Befehlszeile

Befehlsoptionen:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

where `--group` gibt die auszuführende Cron-Gruppe an (diese Option zum Ausführen von Cron für alle Gruppen auslassen)

Geben Sie Folgendes ein, um den Indexierungscron-Auftrag auszuführen:

```bash
bin/magento cron:run --group index
```

Geben Sie Folgendes ein, um den standardmäßigen Cron-Auftrag auszuführen:

```bash
bin/magento cron:run --group default
```

Informationen zum Einrichten von benutzerdefinierten Cron-Aufträgen und -Gruppen finden Sie unter [Benutzerdefinierte Cron-Aufträge und Cron-Gruppen konfigurieren](../cron/custom-cron.md).

>[!INFO]
>
>Sie müssen cron zweimal ausführen: das erste Mal, um Aufgaben zu entdecken und das zweite Mal, um die Aufgaben selbst auszuführen. Der zweite Cron-Run muss auf oder nach der `scheduled_at` Zeit für jede Aufgabe.

## Protokollierung

Alle `cron` Auftragsinformationen wurden verschoben von `system.log` in eine separate `cron.log`.
Standardmäßig finden Sie die Cron-Informationen unter `<install_directory>/var/log/cron.log`.
Alle Ausnahmen von Cron-Aufträgen werden von `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Zusätzlich zur Anmeldung `cron.log`:

- Fehlgeschlagene Aufträge mit `ERROR` und `MISSED` -Status in der `<install_directory>/var/log/support_report.log`.

- Aufträge mit einer `ERROR` Status immer protokolliert werden als `CRITICAL` in `<install_directory>/var/log/exception.log`.

- Aufträge mit einer `MISSED` Status werden protokolliert als `INFO` im `<install_directory>/var/log/debug.log` Verzeichnis (nur Entwicklermodus).

>[!INFO]
>
>Alle Cron-Daten werden auch in die `cron_schedule` in der Commerce-Datenbank. Die Tabelle enthält einen Verlauf der Cron-Aufträge, einschließlich:
>
>- Auftrags-ID und -Code
>- Status
>- Erstellungsdatum
>- Geplantes Datum
>- Ausgeführtes Datum
>- Enddatum
>
>Um Datensätze in der Tabelle anzuzeigen, melden Sie sich in der Befehlszeile bei der Commerce-Datenbank an und geben Sie `SELECT * from cron_schedule;`.
