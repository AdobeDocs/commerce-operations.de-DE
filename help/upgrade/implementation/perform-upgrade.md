---
title: Durchführen eines Upgrades
description: Führen Sie diese Schritte aus, um lokale Bereitstellungen von Adobe Commerce zu aktualisieren.
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: 0cee0ab36274758b583c04dbee8251ce3b78e559
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 0%

---


# Durchführen eines Upgrades

Sie können _vor Ort_ Bereitstellungen der Adobe Commerce- oder Magento Open Source-Anwendung über die Befehlszeile, wenn Sie die Software installiert haben durch:

- Herunterladen des Composer-Metapakets mit dem `composer create-project` Befehl.
- Installieren des komprimierten Archivs.

>[!NOTE]
>
>- Informationen zu Adobe Commerce zu Cloud-Infrastrukturprojekten finden Sie unter [Upgrade der Commerce-Version](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) im Cloud-Handbuch.
>- Verwenden Sie diese Methode nicht zum Aktualisieren, wenn Sie das GitHub-Repository geklont haben. Siehe [Aktualisierung einer Git-basierten Installation](../developer/git-installs.md).

Die folgenden Anweisungen zeigen Ihnen, wie Sie ein Upgrade mit dem Composer Package Manager durchführen. Adobe Commerce 2.4.2 unterstützt Composer 2. Wenn Sie versuchen, von &lt;2.4.1 zu aktualisieren, müssen Sie zunächst mithilfe von Composer 1 auf eine Version aktualisieren, die mit Composer 2 kompatibel ist (z. B. 2.4.2) _before_ Upgrade auf Composer 2 für >2.4.2-Upgrades. Darüber hinaus müssen Sie eine [unterstützte Version](../../installation/system-requirements.md) von PHP.

>[!WARNING]
>
>Das Verfahren für die Aktualisierung von Adobe Commerce und Magento Open Source wurde geändert. Sie müssen eine neue Version der `magento/composer-root-update-plugin` Paket (siehe [Voraussetzungen](../prepare/prerequisites.md)). Darüber hinaus haben sich die Befehle für die Aktualisierung von `composer require magento/<package_name>` nach `composer require-commerce magento/<package_name>`.

## Bevor Sie beginnen

Sie müssen die [Upgrade-Voraussetzungen](../prepare/prerequisites.md) , um Ihre Umgebung vor dem Beginn des Aktualisierungsprozesses vorzubereiten.

## Packages verwalten

>[!NOTE]
>
>In den Beispielen am Ende dieses Abschnitts finden Sie Hilfe zum Festlegen verschiedener Release-Ebenen. Beispielsweise Qualitäts-Patches und Sicherheits-Patches. Wenn Sie diese Pakete nicht in Composer finden können, wenden Sie sich an den Adobe Commerce-Support.

1. Wechseln Sie in den Wartungsmodus, um während des Aktualisierungsprozesses den Zugriff auf Ihren Speicher zu verhindern.

   ```bash
   bin/magento maintenance:enable
   ```

   Siehe [Aktivieren oder Deaktivieren des Wartungsmodus](../../installation/tutorials/maintenance-mode.md) für zusätzliche Optionen. Optional können Sie eine [Benutzerdefinierte Wartungsmodusseite](../troubleshooting/maintenance-mode-options.md).

1. Der Start des Aktualisierungsprozesses während der Ausführung asynchroner Prozesse, z. B. von Verbrauchern in der Nachrichtenwarteschlange, kann zu Datenbeschädigungen führen. Um Datenbeschädigungen zu vermeiden, deaktivieren Sie alle Cron-Aufträge.

   _Adobe Commerce über Cloud-Infrastruktur:_

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

   Warten Sie, bis der Cron-Auftrag abgeschlossen ist. Sie können den Status des Auftrags mit einem Prozess-Viewer überwachen oder die `ps aux | grep 'bin/magento queue'` mehrmals zu beenden, bis alle Prozesse abgeschlossen sind.

1. Erstellen Sie eine Sicherungskopie des `composer.json` -Datei.

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

1. Aktualisieren Sie Ihre Instanz mithilfe der folgenden `composer require-commerce` Befehlssyntax:

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   Zu den Befehlsoptionen gehören:

   - `<product>` —(Erforderlich) Das zu aktualisierende Paket. Bei ortsansässigen Anlagen muss dieser Wert entweder `product-community-edition` oder `product-enterprise-edition`.

   - `<version>` - (Erforderlich) Die Version von Adobe Commerce oder Magento Open Source, auf die Sie ein Upgrade durchführen. Beispiel: `2.4.3`.

   - `--no-update` —(Erforderlich) Deaktiviert die automatische Aktualisierung der Abhängigkeiten.

   - `--interactive-root-conflicts` —(Optional) Ermöglicht die interaktive Ansicht und Aktualisierung von nicht mehr aktuellen Werten aus früheren Versionen oder von benutzerdefinierten Werten, die nicht mit der Version übereinstimmen, auf die Sie aktualisieren.

   - `--force-root-updates` —(Optional) Überschreibt alle in Konflikt stehenden benutzerdefinierten Werte mit den erwarteten Commerce-Werten.

   - `--help` —(Optional) Bietet Nutzungsdetails zum Plug-in.

   Wenn `--interactive-root-conflicts` nor `--force-root-updates` festgelegt sind, behält der Befehl die vorhandenen Werte bei, die in Konflikt stehen, und zeigt eine Warnmeldung an. Weitere Informationen zum Plug-in finden Sie im Abschnitt [Plug-in Usage README](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

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

Qualitäts-Patches enthalten in erster Linie Funktionen _und_ Sicherheitskorrekturen. Sie können jedoch manchmal neue, abwärtskompatible Funktionen enthalten. Verwenden Sie Composer , um einen Qualitäts-Patch herunterzuladen.

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

1. Aktualisieren Sie die `"name"`, `"version"`, und `"description"` -Felder in der `composer.json` Datei nach Bedarf.

   >[!NOTE]
   >
   >Aktualisieren der Metadaten im `composer.json` -Datei ist völlig oberflächlich, nicht funktionsfähig.

1. Wenden Sie Aktualisierungen an.

   ```bash
   composer update
   ```

1. Löschen Sie die `var/` und `generated/` Unterverzeichnisse:

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

1. _(Optional)_ Starten Sie Varnish neu.

   Wenn Sie für die Seiten-Zwischenspeicherung &quot;Varnish&quot;verwenden, starten Sie es neu:

   ```bash
   service varnish restart
   ```

## Überprüfen Sie Ihre Arbeit

Um zu überprüfen, ob das Upgrade erfolgreich war, öffnen Sie Ihre Storefront-URL in einem Webbrowser. Wenn Ihr Upgrade nicht erfolgreich war, wird Ihre Storefront nicht ordnungsgemäß geladen.

Wenn die Anwendung mit einer  `We're sorry, an error has occurred while generating this email.` error:

1. Zurücksetzen [Eigentümer und Berechtigungen des Dateisystems](../../installation/prerequisites/file-system/configure-permissions.md) als Benutzer mit `root` -Berechtigungen.
1. Löschen Sie die folgenden Ordner:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Überprüfen Sie Ihre Storefront in Ihrem Webbrowser erneut.
