---
title: Benutzerdefinierten Cron-Auftrag und eine Cron-Gruppe konfigurieren (Tutorial)
description: Verwenden Sie dieses Schritt-für-Schritt-Tutorial, um einen benutzerdefinierten Cron-Auftrag zu erstellen.
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 0%

---

# Benutzerdefinierten Cron-Auftrag konfigurieren

In diesem Schritt-für-Schritt-Tutorial erfahren Sie, wie Sie einen benutzerdefinierten Cron-Auftrag und optional eine Cron-Gruppe in einem Beispielmodul erstellen. Sie können ein bereits vorhandenes Modul verwenden oder ein Beispielmodul aus unserem [`magento2-samples`-Repository][samples] verwenden.

Wenn Sie den Cron-Auftrag ausführen, wird der Tabelle `cron_schedule` eine Zeile mit dem Namen des Cron-Auftrags, `custom_cron`, hinzugefügt.

Wir zeigen Ihnen auch, wie Sie optional eine Cron-Gruppe erstellen, mit der Sie benutzerdefinierte Cron-Aufträge mit anderen Einstellungen als den Standardeinstellungen der Commerce-Anwendung ausführen können.

In diesem Tutorial gehen wir von Folgendem aus:

- Die Commerce-Anwendung wird in `/var/www/html/magento2` installiert.
- Ihr Benutzername und Kennwort für die Commerce-Datenbank lauten jeweils `magento`
- Sie führen alle Aktionen als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) aus.

## Schritt 1: Abrufen eines Beispielmoduls

Um einen benutzerdefinierten Cron-Auftrag einzurichten, benötigen Sie ein Beispielmodul. Wir empfehlen das Modul `magento-module-minimal` .

Wenn Sie bereits über ein Beispielmodul verfügen, können Sie es verwenden. Überspringen Sie diesen Schritt und den nächsten Schritt und fahren Sie mit Schritt 3: Erstellen Sie eine Klasse zum Ausführen von Cron fort.

**So rufen Sie ein Beispielmodul ab:**

1. Melden Sie sich bei Ihrem Commerce-Server als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) an oder wechseln Sie zu ihm.
1. Wechseln Sie in einen Ordner, der sich nicht im Stammordner der Commerce-Anwendung befindet (z. B. in Ihrem Basisverzeichnis).
1. Klonen Sie das [`magento2-samples` Repository][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   Wenn der Befehl mit dem Fehler `Permission denied (publickey).` fehlschlägt, müssen Sie Ihren öffentlichen SSH-Schlüssel zu GitHub.com][git-ssh] hinzufügen.[

1. Erstellen Sie einen Ordner, in den der Beispielcode kopiert werden soll:

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Kopieren Sie den Beispielmodulcode:

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Überprüfen Sie die kopierten Dateien ordnungsgemäß:

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   Sie sollten das folgende Ergebnis sehen:

   ```terminal
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. Aktualisieren Sie die Commerce-Datenbank und das Schema:

   ```bash
   bin/magento setup:upgrade
   ```

1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```

## Schritt 2: Testmodul überprüfen

Bevor Sie fortfahren, überprüfen Sie, ob das Beispielmodul registriert und aktiviert ist.

1. Führen Sie den folgenden Befehl aus:

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. Stellen Sie sicher, dass das Modul aktiviert ist.

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>Wenn die Ausgabe anzeigt, dass der `Module does not exist`, überprüfen Sie sorgfältig den [Schritt 1](#step-1-get-a-sample-module). Stellen Sie sicher, dass sich Ihr Code im richtigen Verzeichnis befindet. Rechtschreibung und Groß-/Kleinschreibung sind wichtig. Wenn etwas Anderes ist, wird das Modul nicht geladen. Vergessen Sie nicht, `magento setup:upgrade` auszuführen.

## Schritt 3: Erstellen einer Klasse zum Ausführen von Cron

Dieser Schritt zeigt eine einfache Klasse zum Erstellen eines Cron-Auftrags. Die Klasse schreibt nur eine Zeile in die Tabelle `cron_schedule` , die bestätigt, dass sie erfolgreich eingerichtet wurde.

So erstellen Sie eine Klasse:

1. Erstellen Sie einen Ordner für die Klasse und ändern Sie ihn in diesen Ordner:

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. Es wurde eine Datei mit dem Namen `Test.php` in diesem Verzeichnis mit folgendem Inhalt erstellt:

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## Schritt 4: Erstellen Sie `crontab.xml`

Die Datei `crontab.xml` legt einen Zeitplan fest, um Ihren benutzerdefinierten Cron-Code auszuführen.

Erstellen Sie `crontab.xml` wie folgt im Verzeichnis `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` :

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

Die vorherige `crontab.xml` führt die `Magento/SampleMinimal/Cron/Test.php`-Klasse einmal pro Minute aus, was dazu führt, dass der `cron_schedule`-Tabelle eine Zeile hinzugefügt wird.

Verwenden Sie den Konfigurationspfad Ihres Systemkonfigurationsfelds, damit der Cron-Zeitplan vom Administrator aus konfiguriert werden kann.

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

Dabei ist `system/config/path` ein in `etc/adminhtml/system.xml` eines Moduls definierter Systemkonfigurationspfad.

## Schritt 5: Kompilieren und Bereinigen des Cache

Kompilieren Sie den Code mit diesem Befehl:

```bash
bin/magento setup:di:compile
```

Löschen Sie den Cache mit diesem Befehl:

```bash
bin/magento cache:clean
```

## Schritt 6: Überprüfen des Cron-Auftrags

Dieser Schritt zeigt, wie Sie den benutzerdefinierten Cron-Auftrag mithilfe einer SQL-Abfrage in der Datenbanktabelle `cron_schedule` erfolgreich überprüfen können.

Überprüfen von Cron:

1. Ausführen von Commerce-Cron-Aufträgen:

   ```bash
   bin/magento cron:run
   ```

1. Geben Sie den Befehl `magento cron:run` zwei- oder dreimal ein.

   Wenn Sie den Befehl zum ersten Mal eingeben, werden Aufträge in die Warteschlange gestellt. Anschließend werden die Cron-Aufträge ausgeführt. Sie müssen den Befehl _mindestens_ zweimal eingeben.

1. Führen Sie die SQL-Abfrage `SELECT * from cron_schedule WHERE job_code like '%custom%'` wie folgt aus:

   1. `mysql -u magento -p` eingeben
   1. Geben Sie an der Eingabeaufforderung `mysql>` den Wert `use magento;` ein.
   1. `SELECT * from cron_schedule WHERE job_code like '%custom%';` eingeben

      Das Ergebnis sollte in etwa wie folgt aussehen:

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. (Optional) Stellen Sie sicher, dass die Meldungen in das Systemprotokoll von Commerce geschrieben werden:

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   Sie sollten einen oder mehrere Einträge wie den folgenden sehen:

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   Diese Meldungen stammen aus der `execute` -Methode in `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

Wenn der SQL-Befehl und das Systemprotokoll keine Einträge enthalten, führen Sie den Befehl `magento cron:run` mehrmals aus und warten Sie. Es kann einige Zeit dauern, bis die Datenbank aktualisiert wird.

## Schritt 7 (optional): Einrichten einer benutzerdefinierten Cron-Gruppe

Dieser Schritt zeigt, wie Sie optional eine benutzerdefinierte Cron-Gruppe einrichten. Sie sollten eine benutzerdefinierte Cron-Gruppe einrichten, wenn Sie möchten, dass Ihr benutzerdefinierter Cron-Auftrag unter einem anderen Zeitplan ausgeführt wird als andere Cron-Aufträge (normalerweise einmal pro Minute) oder wenn Sie möchten, dass mehrere benutzerdefinierte Cron-Aufträge mit unterschiedlichen Einstellungen ausgeführt werden.

So richten Sie eine benutzerdefinierte Cron-Gruppe ein:

1. Öffnen Sie `crontab.xml` in einem Texteditor.
1. `<group id="default">` in `<group id="custom_crongroup">` ändern
1. Beenden Sie den Texteditor.
1. Erstellen Sie `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` mit dem folgenden Inhalt:

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

Eine Beschreibung der Bedeutung der Optionen finden Sie unter [Anpassen der Crons-Referenz](custom-cron-reference.md).

## Schritt 8: Überprüfen der benutzerdefinierten Cron-Gruppe

Dieser Schritt _optional_ zeigt, wie Sie Ihre benutzerdefinierte Cron-Gruppe mithilfe des Administrators überprüfen können.

Überprüfen der benutzerdefinierten Cron-Gruppe:

1. Führen Sie Commerce-Cron-Aufträge für Ihre benutzerdefinierte Gruppe aus:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   Führen Sie den Befehl mindestens zweimal aus.

1. Cache leeren:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. Melden Sie sich bei Admin als Administrator an.
1. Klicken Sie auf **Stores** > **Einstellungen** > **Konfiguration** > **Erweitert** > **System**.
1. Erweitern Sie im rechten Bereich den Eintrag **Cron**.

   Ihre Cron-Gruppe wird wie folgt angezeigt:

   ![Ihre benutzerdefinierte Cron-Gruppe](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
