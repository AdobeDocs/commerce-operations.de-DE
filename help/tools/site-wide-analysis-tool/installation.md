---
title: Installationshandbuch
description: Verwenden Sie dieses Installationshandbuch [!DNL Site-Wide Analysis Tool] für Ihre Website
source-git-commit: 23ad424a913c5ee58f4092aae008a47fe37b5382
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# Installationshandbuch

Die [!DNL Site-Wide Analysis Tool] bietet rund um die Uhr Leistungsüberwachung, Berichte und Empfehlungen zur Gewährleistung der Sicherheit und Bedienbarkeit von Adobe Commerce in Cloud-Infrastrukturinstallationen. Darüber hinaus finden Sie detaillierte Informationen zu verfügbaren und installierten Patches, Erweiterungen von Drittanbietern und Ihrer Adobe Commerce-Installation.

>[!INFO]
>
>Lernen [aktivieren](../site-wide-analysis-tool/access.md) die [!DNL Site-Wide Analysis Tool] und Berichte erstellen.

Wenn Sie eine lokale Installation von Adobe Commerce haben, müssen Sie einen Agenten in Ihrer Infrastruktur installieren, um das Tool zu verwenden. Sie müssen den Agenten nicht in Adobe Commerce in Cloud-Infrastrukturprojekten installieren.

## Agent

Die [!DNL Site-Wide Analysis Tool] Agent ermöglicht Ihnen die Verwendung der [!DNL Site-Wide Analysis Tool] für Vor-Ort-Anlagen in Adobe Commerce.

Die [!DNL Site-Wide Analysis Tool] Der Agent sammelt Anwendungs- und Geschäftsdaten, analysiert sie und liefert zusätzliche Einblicke in den Zustand Ihrer Installation, sodass Sie das Kundenerlebnis verbessern können. Sie überwacht Ihre Anwendung und hilft Ihnen bei der Erkennung von Leistungs-, Sicherheits-, Verfügbarkeits- und Anwendungsproblemen.

Die Installation des Agenten erfordert die folgenden Schritte:

1. Überprüfen Sie die Systemanforderungen.

1. Konfigurieren Sie API-Schlüssel in der [!UICONTROL Commerce Services Connector] -Erweiterung.

1. Installieren Sie den Agenten.

1. Führen Sie den Agenten aus.

>[!INFO]
>
>Der Agent unterstützt Adobe Commerce-Installationen mit mehreren Knoten. Sie müssen den Agenten auf jedem Knoten installieren und konfigurieren.

## Systemanforderungen

Ihre lokale Infrastruktur muss die folgenden Anforderungen erfüllen, bevor der Agent installiert wird:

- Betriebssysteme

   - [!DNL Linux x86-64] Verteilungen, wie [!DNL RedHat Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian], und ähnliche
   >[!IMPORTANT]
   >
   >Adobe Commerce wird in nicht unterstützt [!DNL Microsoft Windows] oder [!DNL macOS].

- Adobe Commerce 2.4.1 oder höher

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Bash-/Shell-Dienstprogramme

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

Der Agent benötigt die [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) Erweiterung, die auf Ihrem System installiert werden soll, und [konfiguriert](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) mit API-Schlüsseln. Um zu überprüfen, ob die Erweiterung installiert ist, führen Sie den folgenden Befehl aus:

```bash
bin/magento module:status Magento_ServicesConnector
```

Wenn Sie die Erweiterung installiert und mit einem vorhandenen API-Schlüssel für einen anderen Dienst konfiguriert haben, haben Sie **MUSS API-Schlüssel neu generieren** und aktualisieren Sie sie im Adobe Commerce-Admin für den Agenten.

1. Website in [Wartungsmodus](../../installation/tutorials/maintenance-mode.md).

1. Anmelden [accounts.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

1. Klicken **[!UICONTROL API Portal]**.

1. Klicken **[!UICONTROL Delete]** neben dem vorhandenen API-Schlüssel.

1. [Konfigurieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) einen neuen API-Schlüssel.

>[!IMPORTANT]
>
> Wenn Sie im API-Portal neue Schlüssel generieren, aktualisieren Sie die API-Schlüssel im [!DNL Admin configuration]. Wenn Sie neue Schlüssel generieren und diese nicht im [!DNL Admin], funktionieren Ihre SaaS-Erweiterungen nicht mehr und Sie verlieren wertvolle Daten.

Wenn die Erweiterung nicht installiert ist, installieren Sie sie mit den folgenden Anweisungen:

1. Fügen Sie die Erweiterung zu Ihrer `composer.json` und installieren Sie sie.

   ```bash
   composer require magento/services-connector:1.*
   ```

1. Aktivieren Sie die Erweiterung.

   ```bash
   bin/magento module:enable Magento_ServicesConnector
   ```

1. Aktualisieren Sie das Datenbankschema.

   ```bash
   bin/magento setup:upgrade
   ```

1. [API-Schlüssel konfigurieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) , um die Erweiterung mit Ihrem System zu verbinden.

## Installieren des Agenten

Wir haben eine [Shell-Skript](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) um die Installation zu vereinfachen. Es wird empfohlen, das Shell-Skript zu verwenden. Sie können jedoch dem [manuelle Installation](#manual) -Methode.

>[!INFO]
>
>Nachdem der Agent installiert wurde, wird er automatisch aktualisiert, sobald eine neue Version verfügbar ist.

### Skripten

1. Laden Sie das Shell-Skript herunter und führen Sie es aus.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >Es wird empfohlen, den Agenten außerhalb des Stammordners des Adobe Commerce-Projekts zu installieren.

1. Überprüfen Sie die Installation.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Nach dem Herunterladen und Installieren des Agenten müssen Sie [konfigurieren, um](#run-the-agent) Verwendung einer der folgenden Methoden:

   - [Diensleistung](#service) (empfohlen, wenn Sie Stammzugriff haben)

   - [Cron](#cron)

### Manuell {#manual}

Wenn Sie die [Shell-Skript](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) um den Agenten zu installieren, müssen Sie ihn manuell installieren, indem Sie die folgenden Schritte ausführen:

1. Erstellen Sie ein Verzeichnis, in das Sie den Agenten herunterladen möchten.

   >[!TIP]
   >
   >Es wird empfohlen, den Agenten außerhalb des Stammordners des Adobe Commerce-Projekts zu installieren.

1. Laden Sie die Binärdatei herunter und entpacken Sie sie.

   >[!INFO]
   >
   >So verwenden Sie die [!DNL Site-Wide Analysis Tool]müssen Sie zunächst die Nutzungsbedingungen lesen und akzeptieren, die beim Zugriff auf das Dashboard über den Adobe Commerce-Administrator angezeigt werden.

   Für **AMD 64** Architektur:

   1. Laden Sie das Starterarchiv herunter.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Entpacken Sie das Starterarchiv.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   Für **ARM64** Architektur:

   1. Laden Sie das Starterarchiv herunter.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Entpacken Sie das Starterarchiv.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```


1. *(Optional)* Überprüfen Sie die Signatur für die Prüfsummendatei.

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *(Optional)* Überprüfen Sie die Prüfsumme.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Erstellen Sie die `config.yaml` mit dem folgenden Inhalt.

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. Überprüfen Sie die Installation.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Nach dem Herunterladen und Installieren des Agenten müssen Sie [konfigurieren, um](#run-the-agent) Verwendung einer der folgenden Methoden:

   - [Diensleistung](#service) (empfohlen, wenn Sie Stammzugriff haben)

   - [Cron](#cron)

## Ausführen des Agenten {#run-the-agent}

Es wird empfohlen, den Agenten für die Ausführung als Dienst zu konfigurieren. Wenn Sie eingeschränkten Zugriff auf Ihre Infrastruktur haben und keine Root-Berechtigungen haben, müssen Sie [cron](#cron) anstatt.

### Diensleistung {#service}

1. Erstellen einer Datei mit einer systemd-Einheit `(/etc/systemd/system/scheduler.service)` durch die folgende Konfiguration (ersetzen Sie `<filesystemowner>` mit dem Unix-Benutzer, der Eigentümer des Ordners ist, in dem der Agent und die Adobe Commerce-Software installiert sind). Wenn Sie den Agenten als Stammbenutzer heruntergeladen haben, ändern Sie den Ordner und den Eigentümer der verschachtelten Dateien.

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. Starten Sie den Dienst.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Überprüfen Sie, ob der Dienst aktiv ist.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Wenn Sie nicht über Root-Berechtigungen verfügen oder nicht über Berechtigungen zum Konfigurieren eines Dienstes als Root verfügen, können Sie stattdessen Cron verwenden.

Aktualisieren Sie Ihren Cron-Zeitplan:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Deinstallieren

Führen Sie die folgenden Befehle aus, um den Dienst aus Ihrem System zu deinstallieren und alle generierten Dateien zu entfernen:

1. Beenden Sie die Planung.

   ```bash
   systemctl stop scheduler
   ```

1. Deaktivieren Sie die Planung.

   ```bash
   systemctl disable scheduler
   ```

1. Entfernen Sie den Scheduler-Dienst `systemd` Einheitendatei.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Laden Sie die `systemd` Manager-Konfiguration.

   ```bash
   systemctl daemon-reload
   ```

1. Alle zurücksetzen `systemd` Einheiten aus einem fehlgeschlagenen Status.

   ```bash
   systemctl reset-failed
   ```

1. Entfernen Sie den Ordner des Scheduler-Dienstes.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. Entfernen Sie die Binärdatei des Schedulers.

   ```bash
   rm /usr/local/bin/scheduler
   ```

Wenn Sie den Agenten so konfiguriert haben, dass er stattdessen mit cron ausgeführt wird, verwenden Sie die folgenden Anweisungen:

1. Entfernen Sie den Agenten aus der Liste der Kronen.

   ```bash
   crontab -e
   ```

1. Beenden Sie den laufenden Auftrag.

   ```bash
   ps aux | grep scheduler
   ```

1. Entfernen Sie den Ordner, in dem Sie den Agenten installiert haben.

   ```bash
   rm -rf swat-agent
   ```

## Konfigurationsdatei überschreiben

Mithilfe von Umgebungsvariablen können Sie die Werte überschreiben, die Sie während der Installation in der Konfigurationsdatei angegeben haben. Dadurch wird die Abwärtskompatibilität mit früheren Versionen des Agenten beibehalten. In der folgenden Tabelle finden Sie empfohlene Werte:

| EIGENSCHAFT | BESCHREIBUNG |
| --- | --- |
| `SWAT_AGENT_APP_NAME` | Firma oder Site-Name, den Sie bei der Installation des Agenten angegeben haben |
| `SWAT_AGENT_APPLICATION_PHP_PATH` | Pfad zu Ihrem PHP CLI-Interpreter (in der Regel `/usr/bin/php`) |
| `SWAT_AGENT_APPLICATION_MAGENTO_PATH` | Stammordner, in dem Ihre Adobe Commerce-Anwendung installiert ist (normalerweise `/var/www/html`) |
| `SWAT_AGENT_APPLICATION_DB_USER` | Datenbankbenutzer für Ihre Adobe Commerce-Installation |
| `SWAT_AGENT_APPLICATION_DB_PASSWORD` | Datenbankkennwort für den angegebenen Benutzer für Ihre Adobe Commerce-Installation |
| `SWAT_AGENT_APPLICATION_DB_HOST` | Datenbankhost für Ihre Adobe Commerce-Installation |
| `SWAT_AGENT_APPLICATION_DB_NAME` | Datenbankname für Ihre Adobe Commerce-Installation |
| `SWAT_AGENT_APPLICATION_DB_PORT` | Datenbankanschluss für Ihre Adobe Commerce-Installation (in der Regel `3306`) |
| `SWAT_AGENT_APPLICATION_DB_TABLE_PREFIX` | Tabellenpräfix für Ihre Adobe Commerce-Installation (Standardwert: `empty`) |
| `SWAT_AGENT_APPLICATION_DB_REPLICATED` | Gibt an, ob Ihre Adobe Commerce-Installation über eine sekundäre Datenbankinstanz verfügt (normalerweise `false`) |
| `SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH` | Temporärer Ordner für den Agenten (in der Regel `/usr/local/swat-agent/tmp`) |
| `SWAT_AGENT_RUN_CHECKS_ON_START` | Daten beim ersten Start erfassen (in der Regel `1`) |
| `SWAT_AGENT_LOG_LEVEL` | Bestimmt, welche Ereignisse basierend auf dem Schweregrad protokolliert werden (in der Regel `error`) |
| `SWAT_AGENT_ENABLE_AUTO_UPGRADE` | Aktiviert die automatische Aktualisierung (Neustart nach einer Aktualisierung erforderlich); Der Agent prüft nicht auf Aktualisierungen, wenn die Option deaktiviert ist. `true` oder `false`) |
| `SWAT_AGENT_IS_SANDBOX=false` | Aktivieren des Sandbox-Modus zur Verwendung des Agenten in der Staging-Umgebung |

>[!INFO]
>
>Siehe [Zugriff [!DNL Site-Wide Analysis Tool] und Berichte erstellen](../site-wide-analysis-tool/access.md).
