---
title: Durchführen eines Upgrades
description: Führen Sie diese Schritte aus, um lokale Bereitstellungen von Adobe Commerce zu aktualisieren.
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---


# Durchführen eines Upgrades

Sie können über die Befehlszeile eine Aktualisierung von _lokalen_ -Implementierungen der Adobe Commerce-Anwendung durchführen, wenn Sie die Software installiert haben, indem Sie:

- Herunterladen des Composer-Metapakets mit dem Befehl `composer create-project` .
- Installieren des komprimierten Archivs.

>[!NOTE]
>
>- Informationen zu Adobe Commerce in Cloud-Infrastrukturprojekten finden Sie unter [Upgrade der Commerce-Version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) im Cloud-Handbuch.
>- Verwenden Sie diese Methode nicht zum Aktualisieren, wenn Sie das GitHub-Repository geklont haben. Siehe [Aktualisieren einer Git-basierten Installation](../developer/git-installs.md).

Die folgenden Anweisungen zeigen Ihnen, wie Sie ein Upgrade mit dem Composer Package Manager durchführen. Adobe Commerce 2.4.2 unterstützt Composer 2. Wenn Sie versuchen, ein Upgrade von &lt;2.4.1 durchzuführen, müssen Sie zunächst ein Upgrade auf eine Version durchführen, die mit Composer 2 kompatibel ist (z. B. 2.4.2), indem Sie Composer 1 _vor_ Upgrade auf Composer 2 für >2.4.2-Upgrades verwenden. Darüber hinaus müssen Sie eine [unterstützte Version](../../installation/system-requirements.md) von PHP ausführen.

>[!WARNING]
>
>Das Upgrade-Verfahren für Adobe Commerce wurde geändert. Sie müssen eine neue Version des `magento/composer-root-update-plugin`-Pakets installieren (siehe [Voraussetzungen](../prepare/prerequisites.md)). Darüber hinaus haben sich die Befehle für die Aktualisierung von `composer require magento/<package_name>` in `composer require-commerce magento/<package_name>` geändert.

## Bevor Sie beginnen

Sie müssen die [Upgrade-Voraussetzungen](../prepare/prerequisites.md) erfüllen, um Ihre Umgebung vorzubereiten, bevor Sie den Aktualisierungsprozess starten.

## Packages verwalten

>[!NOTE]
>
>In den Beispielen am Ende dieses Abschnitts finden Sie Hilfe zum Festlegen verschiedener Release-Ebenen. Beispielsweise Qualitäts-Patches und Sicherheits-Patches. Wenn Sie diese Pakete nicht in Composer finden können, wenden Sie sich an den Adobe Commerce-Support.

1. Wechseln Sie in den Wartungsmodus, um während des Aktualisierungsprozesses den Zugriff auf Ihren Speicher zu verhindern.

   ```bash
   bin/magento maintenance:enable
   ```

   Weitere Optionen finden Sie unter [Wartungsmodus aktivieren oder deaktivieren](../../installation/tutorials/maintenance-mode.md) . Optional können Sie eine [benutzerdefinierte Seite für den Wartungsmodus ](../troubleshooting/maintenance-mode-options.md) erstellen.

1. Der Start des Aktualisierungsprozesses während der Ausführung asynchroner Prozesse, z. B. von Verbrauchern in der Nachrichtenwarteschlange, kann zu Datenbeschädigungen führen. Um Datenbeschädigungen zu vermeiden, deaktivieren Sie alle Cron-Aufträge.

   _Adobe Commerce in der Cloud-Infrastruktur:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. Starten Sie alle Verbraucher in der Nachrichtenwarteschlange manuell, um sicherzustellen, dass alle Nachrichten verbraucht werden.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   Warten Sie, bis der Cron-Auftrag abgeschlossen ist. Sie können den Status des Auftrags mit einem Prozess-Viewer überwachen oder den Befehl `ps aux | grep 'bin/magento queue'` mehrmals ausführen, bis alle Prozesse abgeschlossen sind.

1. Erstellen Sie eine Sicherung der Datei &quot;`composer.json`&quot;.

   ```bash
   cp composer.json composer.json.bak
   ```

1. Fügen Sie spezifische Pakete entsprechend Ihren Anforderungen hinzu oder entfernen Sie sie.

   Wenn Sie beispielsweise von Magento Open Source auf Adobe Commerce aktualisieren, entfernen Sie das Magento Open Source-Package.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   Sie können auch Beispieldaten aktualisieren.

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - _Magento Open Source:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. Aktualisieren Sie Ihre Instanz mit der folgenden `composer require-commerce` -Befehlssyntax:

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   Zu den Befehlsoptionen gehören:

   - `<product>` - (Erforderlich) Das zu aktualisierende Paket. Bei lokalen Installationen muss dieser Wert entweder `product-community-edition` oder `product-enterprise-edition` betragen.

   - `<version>` - (Erforderlich) Die Version von Adobe Commerce, auf die Sie ein Upgrade durchführen. Beispiel: `2.4.3`.

   - `--no-update` - (Erforderlich) Deaktiviert die automatische Aktualisierung der Abhängigkeiten.

   - `--interactive-root-conflicts` - (Optional) Ermöglicht Ihnen die interaktive Ansicht und Aktualisierung von nicht mehr aktuellen Werten aus früheren Versionen oder von benutzerdefinierten Werten, die nicht mit der Version übereinstimmen, auf die Sie aktualisieren.

   - `--force-root-updates` - (Optional) Überschreibt alle in Konflikt stehenden benutzerdefinierten Werte mit den erwarteten Commerce-Werten.

   - `--help` —(Optional) Bietet Nutzungsdetails zum Plug-in.

   Wenn weder `--interactive-root-conflicts` noch `--force-root-updates` angegeben sind, behält der Befehl die vorhandenen Konfliktwerte bei und zeigt eine Warnmeldung an. Weitere Informationen zum Plug-in finden Sie in der [Gebrauchsanleitung für Plug-ins](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. Aktualisieren Sie die Abhängigkeiten.

   ```bash
   composer update
   ```

### Beispiel - Liste der verfügbaren Versionen

Die vollständige Liste der verfügbaren 2.4.x-Versionen finden Sie unter:

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### Beispiel - Qualitäts-Patch

Qualitäts-Patches enthalten in erster Linie funktionale Sicherheitskorrekturen für _und_. Sie können jedoch manchmal neue, abwärtskompatible Funktionen enthalten. Verwenden Sie Composer , um einen Qualitäts-Patch herunterzuladen.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### Beispiel - Sicherheits-Patch

Sicherheits-Patches enthalten nur Sicherheitskorrekturen. Sie sind so konzipiert, dass der Aktualisierungsprozess schneller und einfacher wird. Sicherheits-Patches verwenden die Composer-Namenskonvention `2.4.x-px`.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## Aktualisieren von Metadaten

1. Aktualisieren Sie die Felder `"name"`, `"version"` und `"description"` in der Datei `composer.json` nach Bedarf.

   >[!NOTE]
   >
   >Die Aktualisierung der Metadaten in der Datei &quot;`composer.json`&quot; ist vollkommen oberflächlich und funktioniert nicht.

1. Wenden Sie Aktualisierungen an.

   ```bash
   composer update
   ```

1. Löschen Sie die Unterverzeichnisse `var/` und `generated/`:

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >Wenn Sie einen anderen Cache-Speicher als das Dateisystem verwenden, z. B. Redis oder Memcached, müssen Sie den Cache auch dort manuell löschen.

1. Datenbankschema und Daten aktualisieren.

   ```bash
   bin/magento setup:upgrade
   ```

1. Wartungsmodus deaktivieren.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(Optional)_ Varnish neu starten.

   Wenn Sie für die Seiten-Zwischenspeicherung &quot;Varnish&quot;verwenden, starten Sie es neu:

   ```bash
   service varnish restart
   ```

## Überprüfen Sie Ihre Arbeit

Um zu überprüfen, ob das Upgrade erfolgreich war, öffnen Sie Ihre Storefront-URL in einem Webbrowser. Wenn Ihr Upgrade nicht erfolgreich war, wird Ihre Storefront nicht ordnungsgemäß geladen.

Wenn die Anwendung mit einem `We're sorry, an error has occurred while generating this email.` -Fehler fehlschlägt:

1. Zurücksetzen von [Dateisystemeigentum und -berechtigungen](../../installation/prerequisites/file-system/configure-permissions.md) als Benutzer mit `root` -Berechtigungen.
1. Löschen Sie die folgenden Ordner:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Überprüfen Sie Ihre Storefront in Ihrem Webbrowser erneut.
