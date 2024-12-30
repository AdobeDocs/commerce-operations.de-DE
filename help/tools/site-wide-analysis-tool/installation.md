---
title: Installationshandbuch
description: Verwenden Sie dieses Handbuch, um  [!DNL Site-Wide Analysis Tool]  für Ihre Website zu installieren
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# Installationshandbuch

>[!IMPORTANT]
>
>Ab dem 23. April 2024 wird die [!DNL Site-Wide Analysis Tool] für alle Adobe Commerce On-Premise-Kunden eingestellt.

Die [!DNL Site-Wide Analysis Tool] bietet rund um die Uhr Echtzeit-Leistungsüberwachung, Berichte und Empfehlungen, um die Sicherheit und Betriebsfähigkeit von Adobe Commerce auf Cloud-Infrastrukturinstallationen sicherzustellen. Außerdem enthält es detaillierte Informationen über verfügbare und installierte Patches, Erweiterungen von Drittanbietern und Ihre Adobe Commerce-Installation.

>[!INFO]
>
>Erfahren Sie[ wie Sie ](../site-wide-analysis-tool/access.md) [!DNL Site-Wide Analysis Tool] aktivieren und Berichte erstellen.

Wenn Sie über eine lokale Installation von Adobe Commerce verfügen, installieren Sie einen Agenten auf Ihrer Infrastruktur, um das Tool zu verwenden. Sie müssen den Agenten nicht in Cloud-Infrastrukturprojekten auf Adobe Commerce installieren.

## Agent

Mit dem [!DNL Site-Wide Analysis Tool] Agent können Sie die [!DNL Site-Wide Analysis Tool] für lokale Installationen von Adobe Commerce verwenden.

Der [!DNL Site-Wide Analysis Tool] Agent erfasst Anwendungs- und Geschäftsdaten, analysiert sie und bietet zusätzliche Einblicke in den Zustand Ihrer Installation, damit Sie das Kundenerlebnis verbessern können. Es überwacht Ihre Anwendung und hilft Ihnen, Leistungs-, Sicherheits-, Verfügbarkeits- und Anwendungsprobleme zu identifizieren.

Die Installation des Agenten erfordert die folgenden Schritte:

1. Überprüfen Sie die Systemanforderungen.

1. Konfigurieren von API-Schlüsseln in der [!UICONTROL Commerce Services Connector].

1. Installieren Sie den Agenten.

1. Führen Sie den Agenten aus.

>[!INFO]
>
>Der Agent unterstützt Adobe Commerce-Installationen mit mehreren Knoten. Installieren und konfigurieren Sie den Agenten auf jedem Knoten.

## Systemanforderungen

Ihre lokale Infrastruktur muss vor der Installation des Agenten die folgenden Anforderungen erfüllen:

- Betriebssysteme

   - [!DNL Linux x86-64] wie [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian] und Ähnliches

  >[!IMPORTANT]
  >
  >Adobe Commerce wird auf [!DNL Microsoft Windows] oder [!DNL macOS] nicht unterstützt.

- Adobe Commerce 2.4.5-p1 oder höher (aufgrund der Abhängigkeit von Service Connector)

- [!DNL Commerce Services Connector extension]

- PHP-CLI

- Bash/Shell-Dienstprogramme

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

Für den Agenten muss die [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)-Erweiterung auf Ihrem System installiert und mit API[Schlüsseln ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) werden. Um sicherzustellen, dass die Erweiterung installiert ist, führen Sie den folgenden Befehl aus:

```bash
bin/magento module:status Magento_ServicesId
```

Wenn Sie die Erweiterung installiert und mithilfe eines vorhandenen API-Schlüssels für einen anderen Service konfiguriert haben, **Sie den API-Schlüssel neu generieren** im Adobe Commerce Admin für den Agenten aktualisieren.

1. Setzen Sie Ihre Website in [Wartungsmodus](../../installation/tutorials/maintenance-mode.md).

1. Melden Sie sich bei [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671) an.

   >[!NOTE]
   >
   > Wenn Sie Probleme beim Zugriff auf Ihr -Konto haben, finden Sie unter [Anmeldung beim Adobe Commerce-Support oder Cloud-Konto nicht möglich](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) Hilfe zur Fehlerbehebung.

1. Klicken Sie auf **[!UICONTROL API Portal]**.

1. Klicken Sie **[!UICONTROL Delete]** neben dem vorhandenen API-Schlüssel.

1. [Konfigurieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) Sie einen neuen API-Schlüssel.

>[!IMPORTANT]
>
> Wenn Sie neue Schlüssel im API-Portal generieren, aktualisieren Sie die API-Schlüssel in der [!DNL Admin configuration] sofort. Wenn Sie neue Schlüssel generieren und die Schlüssel im [!DNL Admin] nicht aktualisieren, funktionieren Ihre SaaS-Erweiterungen nicht mehr und Sie verlieren wertvolle Daten.

Wenn die Erweiterung nicht installiert ist, verwenden Sie die folgenden Anweisungen, um sie zu installieren:

1. Fügen Sie die Erweiterung Ihrer `composer.json`-Datei hinzu und installieren Sie sie.

   ```bash
   composer require magento/services-id
   ```

1. Aktivieren Sie die Erweiterung.

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. Aktualisieren Sie das Datenbankschema.

   ```bash
   bin/magento setup:upgrade
   ```

1. Löschen Sie den Cache.

   ```bash
   bin/magento cache:clean
   ```

1. [API-Schlüssel konfigurieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) um die Erweiterung mit Ihrem System zu verbinden.

## Installieren des Agenten

Wir haben ein [Shell-Skript](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) erstellt, um die Installation zu vereinfachen. Es wird empfohlen, das Shell-Skript zu verwenden, aber Sie können bei [ die Methode ](#manual)manuelle Installation“ verwenden.

>[!INFO]
>
>Nachdem der Agent installiert wurde, wird er automatisch aktualisiert, wenn eine neue Version verfügbar ist.

### Gescript

1. Herunterladen und Ausführen des Shell-Skripts.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >Es wird empfohlen, den Agenten außerhalb Ihres Adobe Commerce-Stammprojektverzeichnisses zu installieren.

1. Überprüfen Sie die Installation.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Nach dem Herunterladen und Installieren des Agenten [konfigurieren Sie ihn für ](#run-the-agent) Ausführung) mit einer der folgenden Methoden:

   - [Service](#service) (empfohlen, wenn Sie über Stammzugriff verfügen)

   - [Cron](#cron)

### Manuell {#manual}

Wenn Sie den Agenten nicht mit unserem [Shell-Skript](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) installieren möchten, müssen Sie ihn manuell installieren, indem Sie die folgenden Schritte ausführen:

1. Erstellen Sie ein Verzeichnis, in das Sie den Agenten herunterladen möchten.

   >[!TIP]
   >
   >Es wird empfohlen, den Agenten außerhalb Ihres Adobe Commerce-Stammprojektverzeichnisses zu installieren.

1. Laden Sie die Binärdatei herunter und entpacken Sie sie.

   >[!INFO]
   >
   >Um die [!DNL Site-Wide Analysis Tool] verwenden zu können, müssen Sie zunächst die Nutzungsbedingungen lesen und akzeptieren, die beim Zugriff auf das Dashboard über die Adobe Commerce-Admin angezeigt werden.

   Für die **AMD64**-Architektur:

   1. Laden Sie das Starter-Archiv herunter.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Entpacken Sie das Starter-Archiv.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   Für die **ARM64**-Architektur:

   1. Laden Sie das Starter-Archiv herunter.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Entpacken Sie das Starter-Archiv.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *(Optional)* Überprüfen der Signatur für die Prüfsummendatei.

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

1. Erstellen Sie die `config.yaml`-Datei mit folgendem Inhalt.

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

1. Nach dem Herunterladen und Installieren des Agenten müssen Sie [ihn so konfigurieren, dass er ausgeführt ](#run-the-agent), indem Sie eine der folgenden Methoden verwenden:

   - [Service](#service) (empfohlen, wenn Sie über Stammzugriff verfügen)

   - [Cron](#cron)

## Ausführen des Agenten {#run-the-agent}

Es wird empfohlen, den Agenten so zu konfigurieren, dass er als Dienst ausgeführt wird. Wenn Sie eingeschränkten Zugriff auf Ihre Infrastruktur haben und keine Stammberechtigungen haben, müssen Sie stattdessen [cron](#cron) verwenden.

### Service {#service}

1. Erstellen Sie eine systemd-`(/etc/systemd/system/scheduler.service)` mit der folgenden Konfiguration (ersetzen Sie `<filesystemowner>` durch den UNIX®-Benutzer, dem das Verzeichnis gehört, in dem der Agent und die Adobe Commerce-Software installiert sind). Wenn Sie den Agenten als Root-Benutzer heruntergeladen haben, ändern Sie das Verzeichnis und den Besitzer der verschachtelten Dateien.

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

1. Starten Sie den Service.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Überprüfen Sie, ob der Dienst ausgeführt wird.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Wenn Sie keine Stammberechtigungen haben oder nicht berechtigt sind, einen Service als Root zu konfigurieren, können Sie stattdessen cron verwenden.

Aktualisieren Sie Ihren Cron-Zeitplan:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Deinstallieren

Führen Sie die folgenden Befehle aus, um den Dienst von Ihrem System zu deinstallieren und alle generierten Dateien zu entfernen:

1. Planung anhalten.

   ```bash
   systemctl stop scheduler
   ```

1. Deaktivieren Sie die Planung.

   ```bash
   systemctl disable scheduler
   ```

1. Entfernen Sie die `systemd`-Einheitendatei des Scheduler-Services.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Laden Sie die `systemd` Manager-Konfiguration neu.

   ```bash
   systemctl daemon-reload
   ```

1. Setzen Sie alle `systemd` aus einem fehlgeschlagenen Status zurück.

   ```bash
   systemctl reset-failed
   ```

1. Entfernen Sie das Dienstverzeichnis der Planung.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. Entfernen Sie die Planungsbinärdatei.

   ```bash
   rm /usr/local/bin/scheduler
   ```

Wenn Sie den Agenten stattdessen für die Ausführung mit Cron konfiguriert haben, verwenden Sie die folgenden Anweisungen:

1. Entfernen Sie den Agenten aus der crontab-Liste.

   ```bash
   crontab -e
   ```

1. Beenden Sie den laufenden Auftrag.

   ```bash
   ps aux | grep scheduler
   ```

1. Entfernen Sie das Verzeichnis, in dem Sie den Agenten installiert haben.

   ```bash
   rm -rf swat-agent
   ```

## Fehlerbehebung

### Zugriffsschlüssel nicht ordnungsgemäß geparst

Wenn Ihre Zugriffsschlüssel nicht ordnungsgemäß analysiert werden, wird möglicherweise der folgende Fehler angezeigt:

```
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Um diesen Fehler zu beheben, führen Sie die folgenden Schritte aus:

1. Führen Sie eine [ Installation durch](#scripted) speichern Sie die Ausgabe und überprüfen Sie die Ausgabe auf Fehler.
1. Überprüfen Sie die generierte `config.yaml`-Datei und überprüfen Sie, ob der Pfad zu Ihrer Commerce-Instanz und PHP korrekt ist.
1. Stellen Sie sicher, dass sich der Benutzer, der die Planung ausführt, in der Gruppe [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md) Unix befindet oder der gleiche Benutzer wie der Dateisystembesitzer ist.
1. Stellen Sie sicher, dass die [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html)-Schlüssel korrekt installiert sind, und aktualisieren Sie sie, um die Erweiterung mit Ihrem System zu verbinden.
1. [Deinstallieren](#uninstall) Sie den Agenten, nachdem Sie die Schlüssel aktualisiert haben, und installieren Sie ihn mithilfe des [Installationsskripts](#scripted) neu.
1. Führen Sie die Planung aus und überprüfen Sie, ob Sie immer noch denselben Fehler erhalten.
1. Wenn Sie immer noch denselben Fehler erhalten, erhöhen Sie die Protokollebene in der `config.yaml`, um zu debuggen, und öffnen Sie ein Support-Ticket.

### *SIGFAULT* Fehler

Wenn beim Ausführen der Binärdatei ein *SIGFAULT*-Fehler auftritt, führen Sie dies wahrscheinlich nicht als Dateibesitzer von Adobe Commerce- und Agentendateien aus.
Überprüfen Sie zur Behebung, ob alle Dateien im Agentenverzeichnis, die denselben Benutzer wie der Dateieigentümer haben, über den Adobe Commerce-Dateien verfügen, und die Binärdatei sollte auch unter diesem Benutzer ausgeführt werden.
Sie können den Befehl `chown` verwenden, um den Dateibesitzer zu ändern und zum entsprechenden Benutzer zu wechseln.
Stellen Sie sicher, dass Ihr Dämonisierungsmechanismus (Cron oder System.d) den Prozess unter dem entsprechenden Benutzer ausführt.

>[!INFO]
>
>Siehe [Zugreifen auf und  [!DNL Site-Wide Analysis Tool]  von Berichten](../site-wide-analysis-tool/access.md).
