---
title: Installationshandbuch
description: Verwenden Sie dieses Handbuch zur Installation von [!DNL Site-Wide Analysis Tool] für Ihre Website
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
>Mit Wirkung vom 23. April 2024 wird der [!DNL Site-Wide Analysis Tool] für alle Adobe Commerce-Kunden vor Ort eingestellt.

Der [!DNL Site-Wide Analysis Tool] bietet rund um die Uhr eine Leistungsüberwachung, Berichte und Empfehlungen zur Gewährleistung der Sicherheit und Bedienbarkeit von Adobe Commerce bei Cloud-Infrastrukturinstallationen. Darüber hinaus finden Sie detaillierte Informationen zu verfügbaren und installierten Patches, Erweiterungen von Drittanbietern und Ihrer Adobe Commerce-Installation.

>[!INFO]
>
>Erfahren Sie, wie Sie ](../site-wide-analysis-tool/access.md) die [!DNL Site-Wide Analysis Tool] aktivieren und Berichte generieren.[

Wenn Sie eine lokale Installation von Adobe Commerce haben, installieren Sie einen Agenten in Ihrer Infrastruktur, um das Tool zu verwenden. Sie müssen den Agenten nicht in Adobe Commerce in Cloud-Infrastrukturprojekten installieren.

## Agent

Mit dem [!DNL Site-Wide Analysis Tool] -Agenten können Sie die [!DNL Site-Wide Analysis Tool] für lokale Installationen von Adobe Commerce verwenden.

Der [!DNL Site-Wide Analysis Tool]-Agent sammelt Anwendungs- und Geschäftsdaten, analysiert sie und liefert zusätzliche Einblicke in den Zustand Ihrer Installation, sodass Sie das Kundenerlebnis verbessern können. Sie überwacht Ihre Anwendung und hilft Ihnen bei der Erkennung von Leistungs-, Sicherheits-, Verfügbarkeits- und Anwendungsproblemen.

Die Installation des Agenten erfordert die folgenden Schritte:

1. Überprüfen Sie die Systemanforderungen.

1. Konfigurieren Sie API-Schlüssel in der Erweiterung [!UICONTROL Commerce Services Connector] .

1. Installieren Sie den Agenten.

1. Führen Sie den Agenten aus.

>[!INFO]
>
>Der Agent unterstützt Adobe Commerce-Installationen mit mehreren Knoten. Installieren und konfigurieren Sie den Agenten auf jedem Knoten.

## Systemanforderungen

Ihre lokale Infrastruktur muss die folgenden Anforderungen erfüllen, bevor der Agent installiert wird:

- Betriebssysteme

   - [!DNL Linux x86-64] Distributionen wie [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian] und ähnliche

  >[!IMPORTANT]
  >
  >Adobe Commerce wird nicht für [!DNL Microsoft Windows] oder [!DNL macOS] unterstützt.

- Adobe Commerce 2.4.5-p1 oder höher (aufgrund der Abhängigkeit von Service Connector)

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

Der Agent erfordert die Installation der Erweiterung [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) auf Ihrem System und die Konfiguration [3} mit API-Schlüsseln. ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) Um zu überprüfen, ob die Erweiterung installiert ist, führen Sie den folgenden Befehl aus:

```bash
bin/magento module:status Magento_ServicesId
```

Wenn Sie die Erweiterung installiert und mithilfe eines vorhandenen API-Schlüssels für einen anderen Dienst konfiguriert haben, MÜSSEN Sie **den API-Schlüssel neu generieren** und ihn im Adobe Commerce-Admin für den Agenten aktualisieren.

1. Setzen Sie Ihre Website in den [Wartungsmodus](../../installation/tutorials/maintenance-mode.md).

1. Melden Sie sich bei [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671) an.

   >[!NOTE]
   >
   > Wenn Sie Probleme beim Zugriff auf Ihr Konto haben, finden Sie Hilfe zur Fehlerbehebung unter [Anmeldung beim Adobe Commerce-Support oder Cloud-Konto nicht möglich](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) .

1. Klicken Sie auf **[!UICONTROL API Portal]**.

1. Klicken Sie neben dem vorhandenen API-Schlüssel auf **[!UICONTROL Delete]** .

1. [Konfigurieren Sie](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) einen neuen API-Schlüssel.

>[!IMPORTANT]
>
> Wenn Sie im API-Portal neue Schlüssel generieren, aktualisieren Sie sofort die API-Schlüssel in der [!DNL Admin configuration]. Wenn Sie neue Schlüssel generieren und die Schlüssel nicht im [!DNL Admin] aktualisieren, funktionieren Ihre SaaS-Erweiterungen nicht mehr und Sie verlieren wertvolle Daten.

Wenn die Erweiterung nicht installiert ist, installieren Sie sie mit den folgenden Anweisungen:

1. Fügen Sie die Erweiterung zu Ihrer `composer.json` -Datei hinzu und installieren Sie sie.

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

1. [API-Schlüssel konfigurieren](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) , um die Erweiterung mit Ihrem System zu verbinden.

## Installieren des Agenten

Wir haben ein [Shell-Skript](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) erstellt, um die Installation zu vereinfachen. Es wird empfohlen, das Shell-Skript zu verwenden. Sie können jedoch bei Bedarf die Methode [manuelle Installation](#manual) befolgen.

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

1. Nachdem Sie den Agenten heruntergeladen und installiert haben, konfigurieren Sie ihn mithilfe einer der folgenden Methoden für die Ausführung von ](#run-the-agent):[

   - [Dienst](#service) (empfohlen, wenn Sie über Stammzugriff verfügen)

   - [Cron](#cron)

### Manuell {#manual}

Wenn Sie den Agenten nicht mithilfe unseres [Shell-Skripts](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) installieren möchten, müssen Sie ihn manuell installieren, indem Sie die folgenden Schritte ausführen:

1. Erstellen Sie ein Verzeichnis, in das Sie den Agenten herunterladen möchten.

   >[!TIP]
   >
   >Es wird empfohlen, den Agenten außerhalb des Stammordners des Adobe Commerce-Projekts zu installieren.

1. Laden Sie die Binärdatei herunter und entpacken Sie sie.

   >[!INFO]
   >
   >Um den [!DNL Site-Wide Analysis Tool] zu verwenden, müssen Sie zunächst die Nutzungsbedingungen lesen und akzeptieren, die beim Zugriff auf das Dashboard über den Adobe Commerce-Administrator angezeigt werden.

   Für die Architektur von **AMD64**:

   1. Laden Sie das Starterarchiv herunter.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Entpacken Sie das Starterarchiv.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   Für die Architektur von **ARM64**:

   1. Laden Sie das Starterarchiv herunter.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
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

1. *(Optional)* Prüfsumme überprüfen.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Erstellen Sie die Datei &quot;`config.yaml`&quot; mit folgendem Inhalt.

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

1. Nachdem Sie den Agenten heruntergeladen und installiert haben, müssen Sie ihn mithilfe einer der folgenden Methoden für die Ausführung von ](#run-the-agent) konfigurieren:[

   - [Dienst](#service) (empfohlen, wenn Sie über Stammzugriff verfügen)

   - [Cron](#cron)

## Ausführen des Agenten {#run-the-agent}

Es wird empfohlen, den Agenten für die Ausführung als Dienst zu konfigurieren. Wenn Sie eingeschränkten Zugriff auf Ihre Infrastruktur haben und keine Root-Berechtigungen haben, müssen Sie stattdessen [cron](#cron) verwenden.

### Dienst {#service}

1. Erstellen Sie eine systemd unit file `(/etc/systemd/system/scheduler.service)` mit der folgenden Konfiguration (ersetzen Sie `<filesystemowner>` durch den UNIX®-Benutzer, der Eigentümer des Ordners ist, in dem der Agent und die Adobe Commerce-Software installiert sind). Wenn Sie den Agenten als Stammbenutzer heruntergeladen haben, ändern Sie den Ordner und den Eigentümer der verschachtelten Dateien.

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

1. Entfernen Sie die Einheitendatei des Planungsdienstes &quot;`systemd`&quot;.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Laden Sie die Manager-Konfiguration `systemd` neu.

   ```bash
   systemctl daemon-reload
   ```

1. Setzen Sie alle `systemd` -Einheiten aus einem fehlgeschlagenen Status zurück.

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

Wenn Sie den Agenten für die Ausführung mit cron konfiguriert haben, verwenden Sie die folgenden Anweisungen:

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

## Fehlerbehebung

### Zugriffsschlüssel nicht ordnungsgemäß analysiert

Wenn Ihre Zugriffsschlüssel nicht richtig analysiert werden, wird möglicherweise der folgende Fehler angezeigt:

```
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Um diesen Fehler zu beheben, führen Sie die folgenden Schritte aus:

1. Führen Sie eine [skriptgesteuerte Installation](#scripted) durch, speichern Sie die Ausgabe und überprüfen Sie die Ausgabe auf Fehler.
1. Überprüfen Sie die generierte `config.yaml` -Datei und stellen Sie sicher, dass der Pfad zu Ihrer Commerce-Instanz und PHP korrekt ist.
1. Stellen Sie sicher, dass sich der Benutzer, der den Planer ausführt, in der Unix-Gruppe [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) oder demselben Benutzer wie der Dateisysteminhaber befindet.
1. Vergewissern Sie sich, dass die Schlüssel [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) richtig installiert sind, und versuchen Sie, sie zu aktualisieren, um die Erweiterung mit Ihrem System zu verbinden.
1. [Deinstallieren Sie den Agenten, nachdem Sie die Schlüssel aktualisiert und mit dem [Installationsskript](#scripted) neu installiert haben.](#uninstall)
1. Führen Sie den Planer aus und überprüfen Sie, ob Sie immer noch denselben Fehler erhalten.
1. Wenn Sie immer noch denselben Fehler erhalten, erhöhen Sie die Protokollebene in `config.yaml`, um ein Support-Ticket zu debuggen und zu öffnen.

### Fehler *SIGFAULT*

Wenn beim Ausführen der Binärdatei ein Fehler vom Typ *SIGFAULT* auftritt, führen Sie diesen wahrscheinlich nicht als Dateiinhaber von Adobe Commerce- und Agentendateien aus.
Um dieses Problem zu beheben, überprüfen Sie, ob alle Dateien im Agentenverzeichnis, die denselben Benutzer wie der Dateiinhaber haben, den Adobe Commerce-Dateien haben, und die Binärdatei auch unter diesem Benutzer ausgeführt werden sollen.
Sie können den Befehl `chown` verwenden, um den Dateiinhaber zu ändern und zum entsprechenden Benutzer zu wechseln.
Stellen Sie sicher, dass Ihr Daemonisierungsmechanismus (Cron oder System.d) den Prozess unter dem entsprechenden Benutzer ausführt.

>[!INFO]
>
>Siehe [Zugriff auf [!DNL Site-Wide Analysis Tool] und Generieren von Berichten](../site-wide-analysis-tool/access.md).
