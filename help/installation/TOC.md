---
user-guide-title: Installationsanleitung
user-guide-description: Erfahren Sie, wie Sie Adobe Commerce und Magento Open Source für lokale Bereitstellungen installieren.
source-git-commit: 949ef8d2036ceeef3cc892a5063ddecc2586a6a9
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Installationsanleitung {#installation-guide}

- [Übersicht](overview.md)
- [Systemanforderungen](system-requirements.md)
- Voraussetzungen {#prerequisites}
   - [Übersicht](prerequisites/overview.md)
   - Dateisystem {#file-system}
      - [Übersicht](prerequisites/file-system/overview.md)
      - [Berechtigungen konfigurieren](prerequisites/file-system/configure-permissions.md)
   - Webserver {#web-server}
      - [Nginx](prerequisites/web-server/nginx.md)
      - [Apache](prerequisites/web-server/apache.md)
   - Datenbankserver {#database-server}
      - [MySQL](prerequisites/database/mysql.md)
      - [Remote-Verbindungen](prerequisites/database/mysql-remote.md)
   - Suchmaschine {#search-engine}
      - [Übersicht](prerequisites/search-engine/overview.md)
      - [AWS OpenSearch](prerequisites/search-engine/aws-opensearch.md)
      - [Nginx konfigurieren](prerequisites/search-engine/configure-nginx.md)
      - [Konfigurieren von Apache](prerequisites/search-engine/configure-apache.md)
   - [PHP](prerequisites/php-settings.md)
   - [Nachrichtenbroker](prerequisites/rabbitmq.md)
   - [Sicherheit](prerequisites/security.md)
   - [Authentifizierungsschlüssel](prerequisites/authentication-keys.md)
   - [Adobe Commerce](prerequisites/commerce.md)
   - [Optionale Software](prerequisites/optional-software.md)
- [Schnellstartinstallation](composer.md)
- [Erweiterte Installation](advanced.md)
- Schritte nach der Installation {#next-steps}
   - [Installation überprüfen](next-steps/verify.md)
   - [Anwendung konfigurieren](next-steps/configuration.md)
   - [Festlegen einer Umfrage (optional)](next-steps/set-umask.md)
   - Beispieldaten installieren (optional) {#sample-data}
      - [Übersicht](sample-data/overview.md)
      - [Herunterladen von Composer-Paketen](sample-data/composer-packages.md)
      - [Git-Repositorys klonen](sample-data/git-repositories.md)
      - [Module entfernen oder aktualisieren](sample-data/remove-or-update.md)
- Tutorials {#tutorials}
   - [Backup und Rollback des Dateisystems, der Medien und der Datenbank](tutorials/backup.md)
   - [Überprüfen des Datenbankstatus](tutorials/database-status.md)
   - [Verbraucherverhalten von Nachrichten konfigurieren](tutorials/message-consumers.md)
   - [Konfigurieren des Sperranbieters](tutorials/lock-provider.md)
   - [Konfigurieren des Stores](tutorials/store.md)
   - [Admin-Konten erstellen, bearbeiten oder entsperren](tutorials/admin.md)
   - [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](tutorials/deployment.md)
   - [Datenbankschema erstellen](tutorials/database.md)
   - [Anzeigen oder Ändern des Admin-URI](tutorials/admin-uri.md)
   - [Wartungsmodus aktivieren oder deaktivieren](tutorials/maintenance-mode.md)
   - [Module aktivieren oder deaktivieren](tutorials/manage-modules.md)
   - [Installieren einer Erweiterung](tutorials/extensions.md)
   - [Commerce installieren](tutorials/install.md)
   - [Basisverzeichnis zur Verbesserung der Sicherheit ändern](tutorials/docroot.md)
   - [Sprachpakete deinstallieren](tutorials/language-packages.md)
   - [Module deinstallieren](tutorials/uninstall-modules.md)
   - [Commerce deinstallieren oder neu installieren](tutorials/uninstall.md)
   - [Designs deinstallieren](tutorials/themes.md)
   - [Datenbankschema aktualisieren](tutorials/database-upgrade.md)