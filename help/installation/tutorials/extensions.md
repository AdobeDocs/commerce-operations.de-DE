---
title: Verwalten von Erweiterungen von Drittanbietern
description: Führen Sie diese Schritte aus, um eine Adobe Commerce-Erweiterung zu installieren, zu aktivieren, zu aktualisieren und zu deinstallieren.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: f057cf082eeab1e34957e284817c6b93517de21b
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 0%

---


# Verwalten von Erweiterungen von Drittanbietern

Code, der das Adobe Commerce-Verhalten erweitert oder anpasst, wird als Erweiterung bezeichnet. Optional können Sie Erweiterungen auf dem [Commerce Marketplace](https://commercemarketplace.adobe.com/) oder einem anderen Erweiterungsverteilungssystem verpacken und verteilen.

Zu den Erweiterungen gehören:

- Module (Adobe Commerce-Funktionen erweitern)
- Designs (ändern Sie das Erscheinungsbild Ihrer Storefront und Ihres Administrators)
- Sprachpakete (Storefront und Admin lokalisieren)

In diesem Thema wird erläutert, wie Sie mit der Befehlszeilenschnittstelle Drittanbietererweiterungen verwalten können, die Sie über die Commerce Marketplace für _lokale_ -Projekte erwerben. Informationen zu Cloud-Infrastrukturprojekten finden Sie unter [Verwalten von Erweiterungen](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions).

Sie können dasselbe Verfahren verwenden, um die Erweiterung _any_ zu installieren. Sie benötigen lediglich den Namen und die Version des Komponentenprogramms der Erweiterung. Um sie zu finden, öffnen Sie die Datei `composer.json` der Erweiterung und notieren Sie die Werte für `"name"` und `"version"`.

## Installieren

Vor der Installation sollten Sie Folgendes tun:

1. Sichern Sie Ihre Datenbank.
1. Wartungsmodus aktivieren:

   ```bash
   bin/magento maintenance:enable
   ```

Um eine Erweiterung zu installieren, müssen Sie:

1. Rufen Sie eine Erweiterung von der Commerce Marketplace oder einem anderen Erweiterungsentwickler ab.
1. Wenn Sie eine Erweiterung aus dem Commerce Marketplace installieren, stellen Sie sicher, dass das `repo.magento.com`-Repository in Ihrer `composer.json`-Datei vorhanden ist:

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Rufen Sie den Namen und die Version des Composers der Erweiterung ab.
1. Aktualisieren Sie die Datei `composer.json` in Ihrem Projekt mit dem Namen und der Version der Erweiterung.
1. Überprüfen Sie, ob die Erweiterung ordnungsgemäß installiert ist.
1. Aktivieren und konfigurieren Sie die Erweiterung.

### Abrufen von Erweiterungsinformationen

Wenn Sie den Namen und die Version des Komponentenprogramms der Erweiterung bereits kennen, überspringen Sie diesen Schritt und fahren Sie mit [Aktualisieren der `composer.json` -Datei](#update-composer-dependencies) fort.

So rufen Sie den Composer-Namen und die Version der Erweiterung von der Commerce Marketplace ab:

1. Melden Sie sich bei [Commerce Marketplace](https://commercemarketplace.adobe.com/) mit dem Benutzernamen und dem Kennwort an, mit dem Sie die Erweiterung gekauft haben.

1. Klicken Sie oben rechts auf **Ihr Name** > **Mein Profil**.

   ![Zugriff auf Ihr Marketplace-Konto](../../assets/installation/marketplace-my-profile.png)

1. Klicken Sie auf **Meine Einkäufe**.

   ![Einkaufsverlauf für Marketplace](../../assets/installation//marketplace-my-purchases.png)

1. Suchen Sie die Erweiterung, die Sie installieren möchten, und notieren Sie sich den Komponentennamen und die Version.

   ![Technische Details zeigen den Namen des Komponisten der Erweiterung an](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>Alternativ können Sie den Namen des Komponisten und die Version der Erweiterung _any_ (unabhängig davon, ob Sie sie auf der Commerce Marketplace oder an einer anderen Stelle erworben haben) in der Datei `composer.json` der Erweiterung finden.

### Aktualisieren von Composer-Abhängigkeiten

Fügen Sie den Namen und die Version der Erweiterung Ihrer `composer.json` -Datei hinzu:

1. Navigieren Sie zu Ihrem Projektverzeichnis und aktualisieren Sie Ihre `composer.json` -Datei.

   ```bash
   composer require <component-name>:<version>
   ```

   Beispiel:

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Geben Sie Ihre [Authentifizierungsschlüssel](../prerequisites/authentication-keys.md) ein. Ihr öffentlicher Schlüssel ist Ihr Benutzername, Ihr privater Schlüssel ist Ihr Passwort.

1. Warten Sie, bis der Composer die Aktualisierung Ihrer Projektabhängigkeiten abgeschlossen hat, und stellen Sie sicher, dass keine Fehler vorliegen:

   ```
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

### Installation überprüfen

Um zu überprüfen, ob die Erweiterung ordnungsgemäß installiert wurde, führen Sie den folgenden Befehl aus:

```bash
bin/magento module:status J2t_Payplug
```

Standardmäßig ist die Erweiterung wahrscheinlich deaktiviert:

```
Module is disabled
```

Der Name der Erweiterung hat das Format `<VendorName>_<ComponentName>`. Dieses Format unterscheidet sich vom Namen des Composers. Verwenden Sie dieses Format, um die Erweiterung zu aktivieren. Wenn Sie sich nicht sicher sind, welchen Namen die Erweiterung hat, führen Sie Folgendes aus:

```bash
bin/magento module:status
```

Suchen Sie nach der Erweiterung unter &quot;Liste der deaktivierten Module&quot;.

### Aktivieren

Einige Erweiterungen funktionieren nur dann ordnungsgemäß, wenn Sie zuvor generierte statische Ansichtsdateien löschen. Verwenden Sie die Option &quot;`--clear-static-content`&quot;, um statische Ansichtsdateien zu löschen, wenn Sie eine Erweiterung aktivieren.

1. Aktivieren Sie die Erweiterung und löschen Sie statische Ansichtsdateien:

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   Die folgende Ausgabe sollte angezeigt werden:

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

1. Kompilieren Sie Ihr Projekt neu: Im Produktionsmodus erhalten Sie möglicherweise eine Meldung mit der Meldung &quot;Magento-Kompilierungsbefehl erneut ausführen&quot;. Die Anwendung fordert Sie nicht auf, den Befehl &quot;Kompilieren&quot;im Entwicklermodus auszuführen.

   ```bash
   bin/magento setup:di:compile
   ```

1. Stellen Sie sicher, dass die Erweiterung aktiviert ist:

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   Es sollte eine Ausgabe angezeigt werden, die überprüft, ob die Erweiterung nicht mehr deaktiviert ist:

   ```
   Module is enabled
   ```

1. Cache leeren:

   ```bash
   bin/magento cache:clean
   ```

1. Konfigurieren Sie die Erweiterung in Admin nach Bedarf.

>[!TIP]
>
>Wenn beim Laden der Storefront in einen Browser Fehler auftreten, verwenden Sie den folgenden Befehl, um den Cache zu löschen: `bin/magento cache:flush`.

## Upgrade

So aktualisieren oder aktualisieren Sie ein Modul oder eine Erweiterung:

1. Laden Sie die aktualisierte Datei von Marketplace oder einem anderen Erweiterungsentwickler herunter. Notieren Sie sich den Modulnamen und die Version.

1. Exportieren Sie die Inhalte in den Stammordner der Anwendung.

1. Wenn für das Modul ein Composer-Paket vorhanden ist, führen Sie einen der folgenden Schritte aus.

   Aktualisierung nach Modulname:

   ```bash
   composer update vendor/module-name
   ```

   Aktualisierung pro Version:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Führen Sie die folgenden Befehle aus, um den Cache zu aktualisieren, bereitzustellen und zu leeren.

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

Wenden Sie sich an den Erweiterungsanbieter, um Anweisungen zum Entfernen einer Drittanbietererweiterung zu erhalten. Die Anweisungen sollten die folgenden Informationen enthalten:

- Wiederherstellen von Datenbanktabellenänderungen
- Wiederherstellen von Datenbankdatenänderungen
- Welche Dateien sollten entfernt oder zurückgesetzt werden?

>[!CAUTION]
>
>Führen Sie die Deinstallationsschritte für eine Nicht-Produktionsumgebung _first_ aus und testen Sie sie gründlich, bevor Sie sie in Ihre Produktionsumgebung übernehmen.

Die folgenden Anweisungen enthalten allgemeine Informationen zum Deinstallieren von Drittanbietererweiterungen:

1. Entfernen Sie die Erweiterung aus Ihrem Adobe Commerce-Projekt-Repository.

   - Entfernen Sie bei Composer-basierten Erweiterungen die Erweiterung aus Ihrer Adobe Commerce `composer.json` -Datei.

     ```bash
     composer remove <component-name>
     ```

   - Entfernen Sie bei Nicht-Composer-basierten Erweiterungen die physischen Dateien aus Ihrem Adobe Commerce-Projekt-Repository.

     ```bash
     rm -rf app/code/<vendor-name>/<component-name>
     ```

1. Wenn die Datei &quot;`config.php`&quot; in Ihrem Adobe Commerce-Projekt-Repository unter Quellcodeverwaltung steht, entfernen Sie die Erweiterung aus der Datei &quot;`config.php`&quot;.

1. Testen Sie Ihre lokale Datenbank, um sicherzustellen, dass die vom Anbieter bereitgestellten Anweisungen erwartungsgemäß funktionieren.

1. Vergewissern Sie sich, dass die Erweiterung ordnungsgemäß deaktiviert ist und dass Ihre Website in Ihrer Staging-Umgebung erwartungsgemäß funktioniert.

1. Stellen Sie die Änderungen in Ihrer Produktionsumgebung bereit.
