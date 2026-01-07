---
user-guide-title: Konfigurationshandbuch
user-guide-description: Konfigurieren Sie die Funktionen und Services Ihrer Adobe Commerce-Anwendung.
feature: Configuration
source-git-commit: d86b9eb07a9da6dc93234f8a02103c543bbead68
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 1%

---


# Konfigurationshandbuch {#configuration-guide}

+ [Überblick](overview.md)
+ Allgemeine Einrichtung {#setup}
   + [Anwendungsinitialisierung und Bootstrap](bootstrap/initialization.md)
   + [Anwendungsmodi](bootstrap/application-modes.md)
   + [Bootstrap-Parameter](bootstrap/set-parameters.md)
   + [Profilerstellung](bootstrap/mage-profiler.md)
   + [Basisverzeichnispfade](bootstrap/mage-directory.md)
+ Bereitstellung {#deployment}
   + [Bereitstellungsübersicht](deployment/overview.md)
   + [Bereitstellung auf einem Computer](deployment/single-machine.md)
   + [Pipeline-Bereitstellung](deployment/technical-details.md)
   + [Voraussetzungen](deployment/prerequisites.md)
   + [Einrichten des Entwicklungssystems](deployment/development-system.md)
   + [System-Setup erstellen](deployment/build-system.md)
   + [Einrichtung des Produktionssystems](deployment/production-system.md)
   + [Zugriffsberechtigungen für Dateisysteme](deployment/file-system-permissions.md)
   + Beispiele {#examples}
      + [Verwenden einer freigegebenen Konfiguration](deployment/example-shared-configuration.md)
      + [Verwenden von CLI-Befehlen](deployment/example-using-cli.md)
      + [Verwenden von Umgebungsvariablen](deployment/example-environment-variables.md)
+ Cache {#cache}
   + [Übersicht über Caching](cache/caching-overview.md)
   + [Cache-Typen](cache/cache-types.md)
   + [Cache-Optionen](cache/cache-options.md)
   + [L2-Cache](cache/level-two-cache.md)
   + Redis {#redis}
      + [Konfigurieren von Redis](cache/config-redis.md)
      + [Redis für Standard-Cache verwenden](cache/redis-pg-cache.md)
      + [Redis für Sitzungsspeicher verwenden](cache/redis-session.md)
      + [Konfigurieren von ElastiCache für EC2-Instanzen](cache/redis-elasticache-for-ec2.md)
   + Tal {#valkey}
      + [Konfigurieren von Valley](cache/config-valkey.md)
      + [Valley für Standard-Cache verwenden](cache/valkey-pg-cache.md)
      + [Valley für Sitzungsspeicherung verwenden](cache/valkey-session.md)
   + lackieren {#varnish}
      + [Lackübersicht](cache/config-varnish.md)
      + [Lack installieren](cache/config-varnish-install.md)
   + [Webserver](cache/config-varnish-server.md)
   + [Konfigurieren des Commerce-Programms](cache/configure-varnish-commerce.md)
   + [Erweiterte Lackkonfiguration](cache/config-varnish-advanced.md)
   + [Cache-Leerung](cache/use-varnish-cache.md)
   + [Cache-Löschen mehrerer Lackinstanzen](cache/use-multiple-varnish-cache.md)
   + [Konfiguration der Lackierung überprüfen](cache/config-varnish-final.md)
   + [ESI-Block Lack](cache/use-varnish-esi.md)
   + [Cache für statische Inhalte](cache/static-content-signing.md)
+ Befehlszeile {#cli}
   + [Befehlszeilen-Tool](cli/config-cli.md)
   + [Allgemeine Befehle](cli/common-cli-commands.md)
   + [Protokollierung aktivieren](cli/enable-logging.md)
   + [Cache verwalten](cli/manage-cache.md)
   + [Verwalten von Indexern](cli/manage-indexers.md)
   + [Konfigurieren von Cron-Aufträgen](cli/configure-cron-jobs.md)
   + [Code kompilieren](cli/code-compiler.md)
   + [Betriebsart](cli/set-mode.md)
   + [Nachrichtenwarteschlangen-Verbraucher starten](cli/start-message-queues.md)
   + [URN-Highlighter](cli/urn-highlighter.md)
   + [Abhängigkeitsberichte](cli/dependency-reports.md)
   + [Lokalisierung](cli/localization.md)
   + Konfigurationsverwaltung {#configuration-management}
      + [Werte festlegen](cli/set-configuration-values.md)
      + [Einstellungen exportieren](cli/export-configuration.md)
      + [Daten importieren](cli/import-configuration.md)
   + Statische Ansicht {#static-view}
      + [Bereitstellungsstrategien](cli/static-view-file-strategy.md)
      + [Statische Ansichtsdateien bereitstellen](cli/static-view-file-deployment.md)
   + [Erstellen von Symlinks](cli/create-symlinks.md)
   + [Ausführen von Modultests](cli/unit-tests.md)
   + [Layout-Dateien konvertieren](cli/convert-layout-files.md)
   + [Generieren von Daten für Leistungstests](cli/generate-data.md)
   + [Ausführen von Support-Dienstprogrammen (nur Commerce)](cli/run-support-utilities.md)
+ Konfigurationsdateien {#files}
   + [Konfigurationsdateien für die Bereitstellung](reference/deployment-files.md)
   + [Konfigurationstypen](reference/config-create-types.md)
   + [Moduldateien](reference/module-files.md)
   + [Modulausgabe](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [Ignorieren](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ Konfigurationspfade {#paths}
   + [Allgemein](reference/config-reference-general.md)
   + [B2B-Erweiterung](reference/config-reference-b2b.md)
   + [Katalog](reference/config-reference-catalog.md)
   + [Kunden](reference/config-reference-customers.md)
   + [Zahlungsmethoden](reference/config-reference-payment.md)
   + [Verkauf](reference/config-reference-sales.md)
   + [Dienste](reference/config-reference-services.md)
   + [Sensible und systemspezifische Einstellungen](reference/config-reference-sens.md)
   + [Konfigurationseinstellungen überschreiben](reference/override-config-settings.md)
+ Cron-Aufträge {#crons}
   + [Cron-Aufträge und -Gruppen](cron/custom-cron.md)
   + [Anpassen der Cron-Referenz](cron/custom-cron-reference.md)
   + [Konfigurieren eines benutzerdefinierten Cron-Auftrags](cron/custom-cron-tutorial.md)
+ Protokolle {#logs}
   + [Benutzerdefinierte Protokolle](logs/custom-logging.md)
   + [Logger-Oberfläche](logs/logger-interface.md)
   + [Datenbankaktivität protokollieren](logs/database-activity.md)
   + [Schreiben in eine benutzerdefinierte Protokolldatei](logs/custom-log-files.md)
+ Nachrichtenwarteschlangen {#message-queues}
   + [Message Queue-Framework](queues/message-queue-framework.md)
   + [Verwalten von Nachrichtenwarteschlangen](queues/manage-message-queues.md)
   + [Einrichten von Amazon MQ](queues/aws-mq.md)
   + [Verbraucher](queues/consumers.md)
+ Mehrere Sites {#multi-sites}
   + [Mehrere Sites und Ansichten](multi-sites/ms-overview.md)
   + [Datenbankentität - Inkrement-ID](multi-sites/change-increment-id.md)
   + [Im Admin-Bereich eingerichtet](multi-sites/ms-admin.md)
   + [Einrichten mit Nginx](multi-sites/ms-nginx.md)
   + [Einrichten mit Apache](multi-sites/ms-apache.md)
+ Suchmaschine {#search}
   + [Überblick über Suchmaschinen](search/overview-search.md)
   + [Konfigurieren der Suchmaschine](search/configure-search-engine.md)
   + [Mit Stoppwörtern filtern](search/search-stopwords.md)
+ Sicherheit {#security}
   + [Sicherheitsübersicht](security/overview.md)
   + [Kennworthashing](security/password-hashing.md)
   + [Cache-Vergiftung](security/cache-poisoning.md)
   + [Sicheres Cron PHP](security/secure-cron-php.md)
   + [Sicherheits-TXT](security/security-txt.md)
   + [Clickjacking-Exploits](security/xframe-options.md)
+ Speicherung {#storage}
   + [Datenbank-Profiler](storage/db-profiler.md)
   + Remote-Speicher {#remote-storage}
      + [Remote-Speichermodul](remote-storage/remote-storage.md)
      + [AWS S3-Bucket](remote-storage/remote-storage-aws-s3.md)
      + [Ändern der Bildgröße](remote-storage/remote-storage-image-resize.md)
      + [Remote-Speicher für Cloud Manager](remote-storage/cloud-support.md)
   + Sitzungsspeicher {#session-storage}
      + [Speicherort der Sitzung](storage/sessions.md)
      + [Memcached für Sitzungsspeicherung](storage/memcached.md)
      + [in CentOS zwischengespeichert](storage/memcache-centos.md)
      + [Memcached auf Ubuntu](storage/memcache-ubuntu.md)
   + Datenbank teilen {#split-db}
      + [Übersicht über die Aufspaltungsdatenbank](storage/multi-master.md)
      + [Automatische Konfiguration](storage/multi-master-masterdb.md)
      + [Manuelle Konfiguration](storage/multi-master-manual.md)
      + [Geteilte Datenbank überprüfen](storage/multi-master-verify.md)
      + [Datenbankreplikation](storage/multi-master-replication.md)
      + [Auf einzelne Datenbank zurücksetzen](storage/revert-split-database.md)
+ [Zurück zu den Betriebshandbüchern](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)