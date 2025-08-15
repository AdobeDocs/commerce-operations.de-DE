---
user-guide-title: Installationsanleitung
user-guide-description: Erfahren Sie, wie Sie Adobe Commerce für lokale Bereitstellungen installieren.
feature: Install
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---


# Installationsanleitung {#installation-guide}

- [Überblick](overview.md)
- [Systemanforderungen](system-requirements.md)
- Voraussetzungen {#prerequisites}
   - [Übersicht](prerequisites/overview.md)
   - Dateisystem {#file-system}
      - [Überblick](prerequisites/file-system/overview.md)
      - [Konfigurieren von Berechtigungen](prerequisites/file-system/configure-permissions.md)
   - Webserver {#web-server}
      - [Nginx](prerequisites/web-server/nginx.md)
      - [Apache](prerequisites/web-server/apache.md)
   - Datenbank-Server {#database-server}
      - [MySQL](prerequisites/database/mysql.md)
      - [Remoteverbindungen](prerequisites/database/mysql-remote.md)
   - Suchmaschine {#search-engine}
      - [Überblick](prerequisites/search-engine/overview.md)
      - [AWS OpenSearch](prerequisites/search-engine/aws-opensearch.md)
      - [Konfigurieren von nginx](prerequisites/search-engine/configure-nginx.md)
      - [Konfigurieren von Apache](prerequisites/search-engine/configure-apache.md)
   - [PHP](prerequisites/php-settings.md)
   - [Nachrichten-Broker](prerequisites/rabbitmq.md)
   - [Sicherheit](prerequisites/security.md)
   - [Authentifizierungsschlüssel](prerequisites/authentication-keys.md)
   - [Adobe Commerce](prerequisites/commerce.md)
   - [Optionale Software](prerequisites/optional-software.md)
- [Schnellstart-Installation](composer.md)
- [Erweiterte Installation](advanced.md)
- Schritte nach der Installation {#next-steps}
   - [Überprüfen der Installation](next-steps/verify.md)
   - [Konfigurieren des Programms](next-steps/configuration.md)
   - [Maske festlegen (optional)](next-steps/set-umask.md)
   - Installieren von Beispieldaten (optional) {#sample-data}
      - [Überblick](sample-data/overview.md)
      - [Herunterladen von Composer-Paketen](sample-data/composer-packages.md)
      - [Klonen von Git-Repositorys](sample-data/git-repositories.md)
      - [Module entfernen oder aktualisieren](sample-data/remove-or-update.md)
- Tutorials {#tutorials}
   - [Sichern und Rollback von Dateisystem, Medien und Datenbank](tutorials/backup.md)
   - [Datenbankstatus überprüfen](tutorials/database-status.md)
   - [Konfigurieren des Verhaltens von Nachrichtenbenutzern](tutorials/message-consumers.md)
   - [Konfigurieren des Sperranbieters](tutorials/lock-provider.md)
   - [Konfigurieren des Stores](tutorials/store.md)
   - [Erstellen, Bearbeiten oder Entsperren von Admin-Konten](tutorials/admin.md)
   - [Erstellen oder Aktualisieren der Bereitstellungskonfiguration](tutorials/deployment.md)
   - [Erstellen des Datenbankschemas](tutorials/database.md)
   - [Admin-URI anzeigen oder ändern](tutorials/admin-uri.md)
   - [Wartungsmodus aktivieren oder deaktivieren](tutorials/maintenance-mode.md)
   - [Module aktivieren oder deaktivieren](tutorials/manage-modules.md)
   - [Installieren einer Erweiterung](tutorials/extensions.md)
   - [Installieren von Commerce](tutorials/install.md)
   - [Ändern des Stammverzeichnisses zur Verbesserung der Sicherheit](tutorials/docroot.md)
   - [Sprachpakete deinstallieren](tutorials/language-packages.md)
   - [Module deinstallieren](tutorials/uninstall-modules.md)
   - [Commerce deinstallieren oder neu installieren](tutorials/uninstall.md)
   - [Designs deinstallieren](tutorials/themes.md)
   - [Datenbankschema aktualisieren](tutorials/database-upgrade.md)
- [Zurück zu den Betriebshandbüchern](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
