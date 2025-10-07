---
title: Erweiterungen von Drittanbietern verwalten
description: Führen Sie die folgenden Schritte aus, um Adobe Commerce Extensions zu installieren, zu aktivieren, zu aktualisieren und zu deinstallieren.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Erweiterungen von Drittanbietern verwalten

Code, der das Verhalten von Adobe Commerce erweitert oder anpasst, wird als Erweiterung bezeichnet. Sie können Erweiterungen optional im [Commerce Marketplace oder &#x200B;](https://commercemarketplace.adobe.com/) anderen Erweiterungsverteilungssystem verpacken und verteilen.

Zu den Erweiterungen gehören:

- Module (Adobe Commerce-Funktionen erweitern)
- Designs (Ändern des Erscheinungsbilds Ihrer Storefront und Ihres Administrators)
- Sprachpakete (Lokalisieren der Storefront und Admin)

In diesem Abschnitt wird erläutert, wie Sie mit der Befehlszeilenschnittstelle Erweiterungen von Drittanbietern verwalten können, die Sie für lokale Projekte _Commerce Marketplace_. Informationen zu Cloud-Infrastrukturprojekten finden Sie unter [Erweiterungen verwalten](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions).

Sie können dieselbe Vorgehensweise verwenden, um die Erweiterung _any_ zu installieren. Sie benötigen lediglich den Namen und die Version des Composers der Erweiterung. Öffnen Sie dazu die `composer.json`-Datei der Erweiterung und notieren Sie sich die Werte für `"name"` und `"version"`.

## Installieren von

Vor der Installation sollten Sie Folgendes tun:

1. Sichern Sie Ihre Datenbank.
1. Wartungsmodus aktivieren:

   ```bash
   bin/magento maintenance:enable
   ```

Um eine Erweiterung zu installieren, müssen Sie:

1. Erhalten Sie eine Erweiterung vom Commerce Marketplace oder einem anderen Erweiterungsentwickler.
1. Wenn Sie eine Erweiterung über die Commerce Marketplace installieren, stellen Sie sicher, dass das `repo.magento.com`-Repository in Ihrer `composer.json` vorhanden ist:

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Abrufen des Namens und der Version des E-Mail-Editors der Erweiterung
1. Aktualisieren Sie die `composer.json` Datei in Ihrem Projekt mit dem Namen und der Version der Erweiterung.
1. Stellen Sie sicher, dass die Erweiterung ordnungsgemäß installiert ist.
1. Aktivieren und Konfigurieren der Erweiterung.

### Abrufen von Erweiterungsinformationen

Wenn Sie den Namen und die Version der Erweiterung „Composer“ bereits kennen, überspringen Sie diesen Schritt und fahren Sie mit &quot;[&#x200B; der `composer.json`-Datei“ &#x200B;](#update-composer-dependencies).

So rufen Sie den Namen und die Version der Erweiterung „Composer“ aus Commerce Marketplace ab:

1. Melden Sie sich bei [Commerce Marketplace](https://commercemarketplace.adobe.com/) mit dem Benutzernamen und Kennwort an, mit dem Sie die Erweiterung erworben haben.

1. Klicken Sie oben rechts auf **Ihr Name** > **Mein Profil**.

   ![Zugriff auf Ihr Marketplace-Konto](../../assets/installation/marketplace-my-profile.png)

1. Klicken Sie **Meine Einkäufe**.

   ![Marketplace-Kaufverlauf](../../assets/installation//marketplace-my-purchases.png)

1. Suchen Sie die Erweiterung, die Sie installieren möchten, und notieren Sie sich den Komponentennamen und die Version.

   ![Technische Details der Erweiterung mit dem Namen des Composer-Pakets für die Installation](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>Alternativ können Sie den Composer-Namen und die Version der _any_-Erweiterung (unabhängig davon, ob Sie sie in Commerce Marketplace oder an einem anderen Ort erworben haben) in der `composer.json` der Erweiterung finden.

### Aktualisieren von Composer-Abhängigkeiten

Fügen Sie den Namen und die Version der Erweiterung zu Ihrer `composer.json` hinzu:

1. Navigieren Sie zu Ihrem Projektverzeichnis und aktualisieren Sie Ihre `composer.json`.

   ```bash
   composer require <component-name>:<version>
   ```

   Beispiel:

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Geben Sie [Authentifizierungsschlüssel“ &#x200B;](../prerequisites/authentication-keys.md). Ihr öffentlicher Schlüssel ist Ihr Benutzername; Ihr privater Schlüssel ist Ihr Kennwort.

1. Warten Sie, bis Composer die Aktualisierung Ihrer Projektabhängigkeiten abgeschlossen hat, und stellen Sie sicher, dass keine Fehler vorhanden sind:

   ```
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

### Installation überprüfen

Um sicherzustellen, dass die Erweiterung ordnungsgemäß installiert ist, führen Sie den folgenden Befehl aus:

```bash
bin/magento module:status J2t_Payplug
```

Standardmäßig ist die Erweiterung wahrscheinlich deaktiviert:

```
Module is disabled
```

Der Name der Erweiterung hat das Format `<VendorName>_<ComponentName>`. Dies ist ein anderes Format als der Name des Komponisten. Verwenden Sie dieses Format, um die Erweiterung zu aktivieren. Wenn Sie sich bezüglich des Namens der Erweiterung nicht sicher sind, führen Sie Folgendes aus:

```bash
bin/magento module:status
```

und suchen Sie nach der Erweiterung unter „Liste der deaktivierten Module“.

### Aktivieren

Einige Erweiterungen funktionieren nicht richtig, es sei denn, Sie löschen zuerst die generierten statischen Ansichtsdateien. Verwenden Sie die Option `--clear-static-content` , um statische Ansichtsdateien zu löschen, wenn Sie eine Erweiterung aktivieren.

1. Aktivieren Sie die Erweiterung und löschen Sie statische Ansichtsdateien:

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   Es sollte folgende Ausgabe angezeigt werden:

   ```
   The following modules have been enabled:
   - J2t_Payplug
   
   To make sure that the enabled modules are properly registered, run 'setup:upgrade'.
   Cache cleared successfully.
   Generated classes cleared successfully. Please run the 'setup:di:compile' command to generate classes.
   Generated static view files cleared successfully.
   ```

1. Registrieren Sie die Erweiterung:

   ```bash
   bin/magento setup:upgrade
   ```

1. Kompilieren Sie Ihr Projekt neu: Im Produktionsmodus erhalten Sie möglicherweise eine Nachricht mit dem Titel „Bitte führen Sie den Magento-Kompilierungsbefehl erneut aus“. Die Anwendung fordert Sie nicht auf, den Kompilierungsbefehl im Entwicklermodus auszuführen.

   ```bash
   bin/magento setup:di:compile
   ```

1. Stellen Sie sicher, dass die Erweiterung aktiviert ist:

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   Es sollte eine Ausgabe angezeigt werden, die bestätigt, dass die Erweiterung nicht mehr deaktiviert ist:

   ```
   Module is enabled
   ```

1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```

1. Konfigurieren Sie die Erweiterung nach Bedarf in Admin.

>[!TIP]
>
>Wenn beim Laden der Storefront in einem Browser Fehler auftreten, verwenden Sie den folgenden Befehl, um den Cache zu löschen: `bin/magento cache:flush`.

## Upgrade

So aktualisieren oder aktualisieren Sie ein Modul oder eine Erweiterung:

1. Laden Sie die aktualisierte Datei von Marketplace oder einem anderen Entwickler der Erweiterung herunter. Notieren Sie sich den Modulnamen und die Version.

1. Exportieren Sie die Inhalte in das Stammverzeichnis der Anwendung.

1. Wenn für das Modul ein Composer-Paket vorhanden ist, führen Sie einen der folgenden Schritte aus.

   Aktualisierung pro Modulname:

   ```bash
   composer update vendor/module-name
   ```

   Aktualisierung pro Version:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Führen Sie die folgenden Befehle aus, um den Cache zu aktualisieren, bereitzustellen und zu bereinigen.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```

## Deinstallieren

Sie sollten sich an den Anbieter der Erweiterung wenden, um Anweisungen zum Entfernen einer Erweiterung eines Drittanbieters zu erhalten. Die Anweisungen sollten die folgenden Informationen enthalten:

- Rückgängigmachen von Änderungen an Datenbanktabellen
- Zurücksetzen von Datenbankdatenänderungen
- Welche Dateien entfernt oder zurückgesetzt werden sollen

>[!CAUTION]
>
>Führen Sie die Deinstallationsschritte in einer Nicht-Produktionsumgebung durch _zuerst_ und testen Sie sie sorgfältig, bevor Sie sie in Ihrer Produktionsumgebung bereitstellen.

Die folgenden Anweisungen enthalten allgemeine Informationen zur Deinstallation von Erweiterungen von Drittanbietern:

1. Entfernen Sie die Erweiterung aus Ihrem Adobe Commerce-Projekt-Repository.

   - Entfernen Sie bei Composer-basierten Erweiterungen die Erweiterung aus Ihrer Adobe Commerce-`composer.json`.

     ```bash
     composer remove <component-name>
     ```

   - Bei nicht auf dem Composer basierenden Erweiterungen entfernen Sie die physischen Dateien aus dem Adobe Commerce-Projekt-Repository.

     ```bash
     rm -rf app/code/<vendor-name>/<component-name>
     ```

1. Wenn sich die `config.php` in Ihrem Adobe Commerce-Projekt-Repository unter der Versionskontrolle befindet, entfernen Sie die Erweiterung aus der `config.php`.

1. Testen Sie Ihre lokale Datenbank, um sicherzustellen, dass die vom Anbieter bereitgestellten Anweisungen erwartungsgemäß funktionieren.

1. Vergewissern Sie sich, dass die Erweiterung ordnungsgemäß deaktiviert ist und Ihre Website in Ihrer Staging-Umgebung erwartungsgemäß funktioniert.

1. Stellen Sie die Änderungen in Ihrer Produktionsumgebung bereit.
