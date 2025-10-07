---
title: Konfigurieren und Ausführen von Cron-Aufträgen
description: Erfahren Sie, wie Sie Cron-Aufträge in Adobe Commerce konfigurieren und verwalten. Entdecken Sie Techniken zur Planung, Konfiguration und Fehlerbehebung.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Konfigurieren von Cron-Aufträgen

{{file-system-owner}}

Einige Commerce-Funktionen erfordern mindestens einen Cron-Auftrag, der die Aktivitäten für die Zukunft plant. Im Folgenden finden Sie eine Teilliste dieser Aktivitäten:

- Katalogpreisregeln
- Newsletter
- Generieren von Google Sitemaps
- Kundenbenachrichtigungen/Benachrichtigungen (Produktpreisänderung, Produkt wieder auf Lager)
- Neuindizierung
- Privater Vertrieb (nur Adobe Commerce)
- Automatische Aktualisierung der Wechselkurse
- Alle E-Mails von Commerce (einschließlich Auftragsbestätigungen und Transaktionen)

>[!WARNING]
>
>Sie können `dev/tools/cron.sh` nicht mehr ausführen, da das Skript entfernt wurde.

>[!INFO]
>
>Commerce hängt von der richtigen Cron-Auftragskonfiguration für viele wichtige Systemfunktionen ab, einschließlich der Indizierung. Wenn es nicht richtig eingerichtet wird, funktioniert Commerce nicht wie erwartet.

UNIX-Systeme planen Aufgaben, die von bestimmten Benutzern mithilfe eines _crontab_ ausgeführt werden sollen. Dies ist eine Datei, die Anweisungen an den Cron-Daemon enthält, die den Daemon anweisen, „diesen Befehl zu diesem Zeitpunkt auszuführen“. Jeder Benutzer hat seine eigene crontab, und Befehle in jeder Crontab werden als der Benutzer ausgeführt, der sie besitzt.

Informationen zum Ausführen von cron in einem Webbrowser finden Sie unter [Sichern von cron.php für die Ausführung in einem Browser](../security/secure-cron-php.md).

## Erstellen oder Entfernen der Commerce-crontab

In diesem Abschnitt wird beschrieben, wie Sie Ihre Commerce-crontab (d. h. die Konfiguration für Commerce-Cron-Aufträge) erstellen oder entfernen.

Die _crontab_ ist die Konfiguration, die zum Ausführen von Cron-Aufträgen verwendet wird.

Die Commerce-Anwendung verwendet Cron-Aufgaben, die mit verschiedenen Konfigurationen ausgeführt werden können. Die PHP-Befehlszeilenkonfiguration steuert den allgemeinen Cron-Job, der Indexer neu indiziert, E-Mails generiert, die Sitemap generiert usw.

>[!WARNING]
>
>- Um Probleme während der Installation und des Upgrades zu vermeiden, empfehlen wir dringend, dieselben PHP-Einstellungen sowohl auf die PHP-Befehlszeilenkonfiguration als auch auf die Konfiguration des PHP-Webserver-Plug-ins anzuwenden. Weitere Informationen finden Sie unter [Erforderliche PHP-Einstellungen](../../installation/prerequisites/php-settings.md).
>- In einem System mit mehreren Knoten kann crontab nur auf einem Knoten ausgeführt werden. Dies gilt nur, wenn Sie aus Gründen der Leistung oder Skalierbarkeit mehr als einen Webknoten einrichten.

### Erstellen der Commerce-crontab

Ab Version 2.2 erstellt Commerce eine crontab für Sie. Wir fügen die crontab von Commerce zu jeder konfigurierten crontab für den Eigentümer des Commerce-Dateisystems hinzu. Anders ausgedrückt: Wenn Sie bereits crontabs für andere Erweiterungen oder Anwendungen eingerichtet haben, fügen wir die crontab von Commerce hinzu.

Die crontab von Commerce befindet sich in `#~ MAGENTO START` und `#~ MAGENTO END` Kommentare in Ihrer crontab.

So erstellen Sie die crontab von Commerce:

1. Melden Sie sich als „Dateisystembesitzer“ an [ wechseln Sie zu diesem ](../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie in das Commerce-Installationsverzeichnis.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   bin/magento cron:install [--force]
   ```

Verwenden Sie `--force`, um eine vorhandene crontab neu zu schreiben.

>[!INFO]
>
>- `magento cron:install` schreibt eine vorhandene crontab innerhalb von `#~ MAGENTO START` nicht um und `#~ MAGENTO END` Kommentare in Ihrer crontab.
>- `magento cron:install --force` hat keine Auswirkungen auf Cron-Aufträge außerhalb der Commerce-Kommentare.

Um die crontab anzuzeigen, geben Sie den folgenden Befehl als Eigentümer des Dateisystems ein:

```bash
crontab -l
```

Es folgt ein Beispiel:

```
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>Die `update/cron.php` wurde in Commerce 2.4.0 entfernt. Wenn diese Datei bereits in Ihrer Installation vorhanden ist, kann sie sicher entfernt werden.
>
>Alle Verweise auf `update/cron.php` und `bin/magento setup:cron:run` sollten auch aus dem crontab entfernt werden.

### Entfernen der Commerce-crontab

Sie sollten die crontab von Commerce nur vor der Deinstallation der Commerce-Anwendung entfernen.

So entfernen Sie die crontab von Commerce:

1. Melden Sie sich als an oder wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie in das Commerce-Installationsverzeichnis.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Dieser Befehl hat keine Auswirkungen auf Cron-Aufträge außerhalb der `#~ MAGENTO START` und `#~ MAGENTO END` Kommentare auf Ihrer crontab.

## Ausführen von cron über die Befehlszeile

Befehlsoptionen:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

Dabei gibt `--group` die auszuführende Cron-Gruppe an (lassen Sie diese Option weg, um Cron für alle Gruppen auszuführen)

Um den Cron-Indizierungsauftrag auszuführen, geben Sie Folgendes ein:

```bash
bin/magento cron:run --group index
```

Um den standardmäßigen Cron-Auftrag auszuführen, geben Sie Folgendes ein:

```bash
bin/magento cron:run --group default
```

Informationen zum Einrichten benutzerdefinierter Cron-Aufträge und -Gruppen finden Sie unter [Konfigurieren benutzerdefinierter Cron-Aufträge und Cron-Gruppen](../cron/custom-cron.md).

>[!INFO]
>
>Sie müssen Cron zweimal ausführen: das erste Mal, um Aufgaben auszuführen, und das zweite Mal, um die Aufgaben selbst auszuführen. Der zweite Cron-Durchgang muss am oder nach der `scheduled_at` für jede Aufgabe erfolgen.

## Protokollierung

Alle `cron` Auftragsinformationen wurden von `system.log` in eine separate `cron.log` verschoben.
Standardmäßig finden Sie die Cron-Informationen unter `<install_directory>/var/log/cron.log`.
Alle Ausnahmen von Cron-Aufträgen werden von `\Magento\Cron\Observer\ProcessCronQueueObserver::execute` protokolliert.

Zusätzlich zur Anmeldung `cron.log`:

- Fehlgeschlagene Aufträge mit dem Status `ERROR` und `MISSED` werden in der `<install_directory>/var/log/support_report.log` protokolliert.

- Aufträge mit dem Status `ERROR` werden immer als `CRITICAL` in `<install_directory>/var/log/exception.log` protokolliert.

- Aufträge mit dem Status `MISSED` werden als `INFO` im `<install_directory>/var/log/debug.log`-Verzeichnis protokolliert (nur Entwicklermodus).

>[!INFO]
>
>Alle Cron-Daten werden auch in die `cron_schedule` in der Commerce-Datenbank geschrieben. Die Tabelle enthält einen Verlauf der Cron-Aufträge, einschließlich:
>
>- Vorgangs-ID und Code
>- Status
>- Erstellungsdatum
>- Geplantes Datum
>- Ausführungsdatum
>- Enddatum
>
>Um die Datensätze in der Tabelle anzuzeigen, melden Sie sich in der Befehlszeile bei der Commerce-Datenbank an und geben Sie `SELECT * from cron_schedule;` ein.
