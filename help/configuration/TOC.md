---
user-guide-title: Konfigurationshandbuch
user-guide-description: Konfigurieren Sie die Funktionen und Dienste Ihrer Adobe Commerce- oder Magento Open Source-Anwendung.
source-git-commit: b872a61f74818990833ba6b48e061fa1ca69b7cb
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# Konfigurationshandbuch {#configuration-guide}

+ [Übersicht](overview.md)
+ Allgemeine Einrichtung {#setup}
   + [Anwendungsinitialisierung und Bootstrap](bootstrap/initialization.md)
   + [Anwendungsmodi](bootstrap/application-modes.md)
   + [Bootstrap-Parameter](bootstrap/set-parameters.md)
   + [Profiling](bootstrap/mage-profiler.md)
   + [Basisordnerpfade](bootstrap/mage-directory.md)
+ Implementierung {#deployment}
   + [Implementierungsübersicht](deployment/overview.md)
   + [Einzelmaschinenimplementierung](deployment/single-machine.md)
   + [Pipeline-Bereitstellung](deployment/technical-details.md)
   + [Voraussetzungen](deployment/prerequisites.md)
   + [Einrichten des Entwicklungssystems](deployment/development-system.md)
   + [Einrichten von Systemen](deployment/build-system.md)
   + [Einrichten des Produktionssystems](deployment/production-system.md)
   + [Zugriffsberechtigungen für Dateisysteme](deployment/file-system-permissions.md)
   + Beispiele {#examples}
      + [Verwenden einer freigegebenen Konfiguration](deployment/example-shared-configuration.md)
      + [Verwenden von CLI-Befehlen](deployment/example-using-cli.md)
      + [Umgebungsvariablen verwenden](deployment/example-environment-variables.md)
+ Cache {#cache}
   + [Zwischenspeicherung - Übersicht](cache/caching-overview.md)
   + [Cachetypen](cache/cache-types.md)
   + [Cacheoptionen](cache/cache-options.md)
   + [L2-Cache](cache/level-two-cache.md)
   + Redis {#redis}
      + [Konfigurieren von Redis](cache/config-redis.md)
      + [Verwenden von Redizes für den Standard-Cache](cache/redis-pg-cache.md)
      + [Verwenden von Redizes für die Sitzungsspeicherung](cache/redis-session.md)
   + Varnisch {#varnish}
      + [Übersicht über Varnish](cache/config-varnish.md)
      + [Installieren von Varnish](cache/config-varnish-install.md)
   + [Webserver](cache/config-varnish-server.md)
   + [Commerce-Anwendung konfigurieren](cache/configure-varnish-commerce.md)
   + [Erweiterte Varnish-Konfiguration](cache/config-varnish-advanced.md)
   + [Cache-Leerung](cache/use-varnish-cache.md)
   + [Cache-Leeren mehrerer verschiedener Instanzen](cache/use-multiple-varnish-cache.md)
   + [Varnish-Konfiguration überprüfen](cache/config-varnish-final.md)
   + [Varnischer ESI-Block](cache/use-varnish-esi.md)
   + [Statischer Inhalts-Cache](cache/static-content-signing.md)
+ Befehlszeile {#cli}
   + [Befehlszeilen-Tool](cli/config-cli.md)
   + [Allgemeine Befehle](cli/common-cli-commands.md)
   + [Protokollierung aktivieren](cli/enable-logging.md)
   + [Verwalten des Cache](cli/manage-cache.md)
   + [Indexer verwalten](cli/manage-indexers.md)
   + [Konfigurieren von Cron-Aufträgen](cli/configure-cron-jobs.md)
   + [Kompilierungscode](cli/code-compiler.md)
   + [Betriebsmodus](cli/set-mode.md)
   + [Starten von Nachrichtenwarteschlangen-Verbrauchern](cli/start-message-queues.md)
   + [URN-Highlighter](cli/urn-highlighter.md)
   + [Abhängigkeitsberichte](cli/dependency-reports.md)
   + [Lokalisierung](cli/localization.md)
   + Konfigurationsverwaltung {#configuration-management}
      + [Werte festlegen](cli/set-configuration-values.md)
      + [Exporteinstellungen](cli/export-configuration.md)
      + [Daten importieren](cli/import-configuration.md)
   + Statische Ansicht {#static-view}
      + [Implementierungsstrategien](cli/static-view-file-strategy.md)
      + [Bereitstellen von statischen Ansichtsdateien](cli/static-view-file-deployment.md)
   + [Symlinks erstellen](cli/create-symlinks.md)
   + [Ausführen von Komponententests](cli/unit-tests.md)
   + [Layout-Dateien konvertieren](cli/convert-layout-files.md)
   + [Generieren von Daten für Leistungstests](cli/generate-data.md)
   + [Ausführen von Hilfsprogrammen (nur Commerce)](cli/run-support-utilities.md)
+ Konfigurationsdateien {#files}
   + [Konfigurationsdateien für die Bereitstellung](reference/deployment-files.md)
   + [Konfigurationstypen](reference/config-create-types.md)
   + [Moduldateien](reference/module-files.md)
   + [Modulausgabe](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [gitignore](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ Konfigurationspfade {#paths}
   + [Allgemein](reference/config-reference-general.md)
   + [B2B-Erweiterung](reference/config-reference-b2b.md)
   + [Katalog](reference/config-reference-catalog.md)
   + [Kunden](reference/config-reference-customers.md)
   + [Zahlungsmethoden](reference/config-reference-payment.md)
   + [Vertrieb](reference/config-reference-sales.md)
   + [Dienste](reference/config-reference-services.md)
   + [Sensible und systemspezifische Einstellungen](reference/config-reference-sens.md)
   + [Konfigurationseinstellungen überschreiben](reference/override-config-settings.md)
+ Cron-Aufträge {#crons}
   + [Cron-Aufträge und -Gruppen](cron/custom-cron.md)
   + [Anpassen der ECrons-Referenz](cron/custom-cron-reference.md)
   + [Benutzerdefinierten Cron-Auftrag konfigurieren](cron/custom-cron-tutorial.md)
+ Protokolle {#logs}
   + [Benutzerdefinierte Protokolle](logs/custom-logging.md)
   + [Logger-Benutzeroberfläche](logs/logger-interface.md)
   + [Aktivität &quot;Logdatenbank&quot;](logs/database-activity.md)
   + [Schreiben in eine benutzerdefinierte Protokolldatei](logs/custom-log-files.md)
+ Nachrichtenwarteschlangen {#message-queues}
   + [Nachrichtenwarteschlangen-Framework](queues/message-queue-framework.md)
   + [Verwalten von Nachrichtenwarteschlangen](queues/manage-message-queues.md)
   + [Einrichten von Amazon MQ](queues/aws-mq.md)
+ Mehrere Sites {#multi-sites}
   + [Mehrere Sites und Ansichten](multi-sites/ms-overview.md)
   + [Inkrement-ID der Datenbankentität](multi-sites/change-increment-id.md)
   + [In der Admin einrichten](multi-sites/ms-admin.md)
   + [Einrichten mit Nginx](multi-sites/ms-nginx.md)
   + [Einrichten mit Apache](multi-sites/ms-apache.md)
+ Suchmaschine {#search}
   + [Übersicht über Suchmaschinen](search/overview-search.md)
   + [Suchmaschine konfigurieren](search/configure-search-engine.md)
   + [Filtern mit Stoppwörtern](search/search-stopwords.md)
+ Sicherheit {#security}
   + [Sicherheitsübersicht](security/overview.md)
   + [Kennwort-Hashing](security/password-hashing.md)
   + [Cache-Vergiftung](security/cache-poisoning.md)
   + [Sicheres cron-PHP](security/secure-cron-php.md)
   + [Sicherheits-TXT](security/security-txt.md)
   + [X-Frame-Options-Kopfzeile](security/xframe-options.md)
+ Speicherung {#storage}
   + [Datenbank-Profiler](storage/db-profiler.md)
   + Remote-Speicher {#remote-storage}
      + [Remote-Speichermodul](remote-storage/remote-storage.md)
      + [AWS S3-Bucket](remote-storage/remote-storage-aws-s3.md)
      + [Bildgröße ändern](remote-storage/remote-storage-image-resize.md)
      + [Remote-Speicher für Cloud](remote-storage/cloud-support.md)
   + Sitzungsspeicher {#session-storage}
      + [Speicherort der Sitzung](storage/sessions.md)
      + [Für Sitzungsspeicherung zwischengespeichert](storage/memcached.md)
      + [In CentOS zwischengespeichert](storage/memcache-centos.md)
      + [in Ubuntu gespeichert](storage/memcache-ubuntu.md)
   + Aufspaltungsdatenbank {#split-db}
      + [Geteilte Datenbank - Übersicht](storage/multi-master.md)
      + [Automatische Konfiguration](storage/multi-master-masterdb.md)
      + [Manuelle Konfiguration](storage/multi-master-manual.md)
      + [Geteilte Datenbank überprüfen](storage/multi-master-verify.md)
      + [Datenbankreplikation](storage/multi-master-replication.md)
      + [Auf einzelne Datenbank zurücksetzen](storage/revert-split-database.md)
