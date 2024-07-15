---
title: Konfigurieren und Ausführen von Cron-Aufträgen
description: Erfahren Sie, wie Sie Cron-Aufträge verwalten.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---

# Konfigurieren von Cron-Aufträgen

{{file-system-owner}}

Für mehrere Commerce-Funktionen ist mindestens ein Cron-Auftrag erforderlich, mit dem zukünftige Aktivitäten geplant werden. Eine teilweise Liste dieser Aktivitäten folgt:

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
>Sie können `dev/tools/cron.sh` nicht mehr ausführen, da das Skript entfernt wurde.

>[!INFO]
>
>Commerce ist für viele wichtige Systemfunktionen, einschließlich Indizierung, von einer ordnungsgemäßen Cron-Auftragskonfiguration abhängig. Wird sie nicht ordnungsgemäß eingerichtet, funktioniert Commerce nicht erwartungsgemäß.

UNIX-Systeme planen Aufgaben, die von bestimmten Benutzern mit einer _crontab_ ausgeführt werden sollen. Dies ist eine Datei, die Anweisungen für den Cron-Daemon enthält, der dem Daemon anweist, &quot;diesen Befehl zu diesem Zeitpunkt an diesem Datum auszuführen&quot;. Jeder Benutzer verfügt über eine eigene Registerkarte und Befehle in jeder beliebigen Registerkarte werden als der Benutzer ausgeführt, dem die Registerkarte gehört.

Informationen zum Ausführen von cron in einem Webbrowser finden Sie unter [Sichere cron.php für die Ausführung in einem Browser](../security/secure-cron-php.md).

## Erstellen oder Entfernen der Commerce-Registerkarte

In diesem Abschnitt wird beschrieben, wie Sie Ihre Commerce-Crontab (d. h. die Konfiguration für Commerce-Cron-Aufträge) erstellen oder entfernen.

Die _crontab_ ist die Konfiguration, die zum Ausführen von Cron-Aufträgen verwendet wird.

Die Commerce-Anwendung verwendet Cron-Aufgaben, die mit verschiedenen Konfigurationen ausgeführt werden können. Die PHP-Befehlszeilenkonfiguration steuert den allgemeinen Cron-Auftrag, der Indexer neu indiziert, E-Mails generiert, die Sitemap generiert und so weiter.

>[!WARNING]
>
>- Um Probleme während der Installation und Aktualisierung zu vermeiden, empfehlen wir dringend, die gleichen PHP-Einstellungen sowohl auf die PHP-Befehlszeilenkonfiguration als auch auf die Konfiguration des PHP-Webserver-Plug-ins anzuwenden. Weitere Informationen finden Sie unter [Erforderliche PHP-Einstellungen](../../installation/prerequisites/php-settings.md).
>- In einem System mit mehreren Knoten kann crontab nur auf einem Knoten ausgeführt werden. Dies gilt nur für Sie, wenn Sie aus Gründen der Leistung oder Skalierbarkeit mehr als einen Webknoten einrichten.

### Commerce-Registerkarte erstellen

Ab Version 2.2 erstellt Commerce eine Registerkarte mit der Kronen. Wir fügen die Commerce-Crontab zu jeder konfigurierten Registerkarte für das Commerce-Dateisysteminhaber hinzu. Wenn Sie also bereits Registerkarten für andere Erweiterungen oder Anwendungen eingerichtet haben, fügen wir die Commerce-Kronen hinzu.

Die Commerce-Crontab befindet sich in den Kommentaren `#~ MAGENTO START` und `#~ MAGENTO END` in Ihrer Crontab.

So erstellen Sie die Commerce-Registerkarte:

1. Melden Sie sich als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) an oder wechseln Sie zu ihm.
1. Wechseln Sie zum Installationsverzeichnis von Commerce.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   bin/magento cron:install [--force]
   ```

Verwenden Sie `--force`, um eine vorhandene Registerkarte neu zu schreiben.

>[!INFO]
>
>- `magento cron:install` schreibt keine vorhandene Kronregisterkarte in `#~ MAGENTO START` - und `#~ MAGENTO END` -Kommentaren in Ihrer Kronregisterkarte um.
>- `magento cron:install --force` wirkt sich nicht auf Cron-Aufträge außerhalb der Commerce-Kommentare aus.

Um die Registerkarte &quot;crontab&quot;anzuzeigen, geben Sie den folgenden Befehl als Dateisysteminhaber ein:

```bash
crontab -l
```

Ein Beispiel:

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>Die Datei &quot;`update/cron.php`&quot; wurde in Commerce 2.4.0 entfernt. Wenn diese Datei in Ihrer Installation vorhanden ist, kann sie sicher entfernt werden.
>
>Jeder Verweis auf `update/cron.php` und `bin/magento setup:cron:run` sollte ebenfalls aus der Registerkarte &quot;Crontab&quot;entfernt werden.

### Entfernen der Commerce-Registerkarte

Sie sollten die Commerce-Registerkarte nur entfernen, bevor Sie die Commerce-Anwendung deinstallieren.

So entfernen Sie die Commerce-Kronregisterkarte:

1. Melden Sie sich als an oder wechseln Sie zum [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie zum Installationsordner von Commerce.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Dieser Befehl hat keine Auswirkungen auf Cron-Aufträge außerhalb der Kommentare `#~ MAGENTO START` und `#~ MAGENTO END` in Ihrer Crontab.

## Ausführen von cron über die Befehlszeile

Befehlsoptionen:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

wobei `--group` die auszuführende Cron-Gruppe angibt (diese Option zum Ausführen von Cron für alle Gruppen auslassen)

Geben Sie Folgendes ein, um den Indexierungscron-Auftrag auszuführen:

```bash
bin/magento cron:run --group index
```

Geben Sie Folgendes ein, um den standardmäßigen Cron-Auftrag auszuführen:

```bash
bin/magento cron:run --group default
```

Informationen zum Einrichten von benutzerdefinierten Cron-Aufträgen und -Gruppen finden Sie unter [Konfigurieren von benutzerdefinierten Cron-Aufträgen und Cron-Gruppen](../cron/custom-cron.md).

>[!INFO]
>
>Sie müssen Cron zweimal ausführen: das erste Mal, um Aufgaben zu entdecken, und das zweite Mal, um die Aufgaben selbst auszuführen. Die zweite Cron-Ausführung muss für jede Aufgabe an oder nach der `scheduled_at`-Zeit erfolgen.

## Protokollierung

Alle `cron` Auftragsinformationen wurden von `system.log` in eine separate `cron.log` verschoben.
Standardmäßig befinden sich die Cron-Informationen unter `<install_directory>/var/log/cron.log`.
Alle Ausnahmen von Cron-Aufträgen werden von `\Magento\Cron\Observer\ProcessCronQueueObserver::execute` protokolliert.

Zusätzlich zur Anmeldung in `cron.log`:

- Fehlgeschlagene Aufträge mit den Status `ERROR` und `MISSED` werden bei der `<install_directory>/var/log/support_report.log` protokolliert.

- Aufträge mit dem Status `ERROR` werden immer als `CRITICAL` in `<install_directory>/var/log/exception.log` protokolliert.

- Aufträge mit dem Status `MISSED` werden als `INFO` im Verzeichnis `<install_directory>/var/log/debug.log` protokolliert (nur Entwicklermodus).

>[!INFO]
>
>Alle Cron-Daten werden auch in die Tabelle `cron_schedule` in der Commerce-Datenbank geschrieben. Die Tabelle enthält einen Verlauf der Cron-Aufträge, einschließlich:
>
>- Auftrags-ID und -Code
>- Status
>- Erstellungsdatum
>- Geplantes Datum
>- Ausgeführtes Datum
>- Enddatum
>
>Um Datensätze in der Tabelle anzuzeigen, melden Sie sich in der Befehlszeile bei der Commerce-Datenbank an und geben Sie `SELECT * from cron_schedule;` ein.
