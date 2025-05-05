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

Sie können _On-Premise_-Bereitstellungen der Adobe Commerce-Anwendung über die Befehlszeile aktualisieren, wenn Sie die Software wie folgt installiert haben:

- Herunterladen des Composer-Metapakets mit dem `composer create-project`.
- Installieren des komprimierten Archivs.

>[!NOTE]
>
>- Informationen zu Adobe Commerce in Cloud-Infrastrukturprojekten finden Sie unter [Commerce-Version aktualisieren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html?lang=de) im Cloud-Handbuch.
>- Verwenden Sie diese Methode nicht zum Upgrade, wenn Sie das GitHub-Repository geklont haben. Siehe [Upgrade einer Git-basierten Installation](../developer/git-installs.md).

Die folgenden Anweisungen zeigen Ihnen, wie Sie mit dem Composer Package Manager ein Upgrade durchführen. Mit Adobe Commerce 2.4.2 wurde Unterstützung für Composer 2 eingeführt. Wenn Sie versuchen, von &lt;2.4.1 auf eine Version zu aktualisieren, die mit Composer 2 kompatibel ist (z. B. 2.4.2), müssen Sie zunächst Composer 1 _vor_ aktualisieren auf Composer 2 für >2.4.2-Upgrades. Außerdem muss eine (unterstützte[ Version von PHP ](../../installation/system-requirements.md) werden.

>[!WARNING]
>
>Das Verfahren zum Aktualisieren von Adobe Commerce wurde geändert. Sie müssen eine neue Version des `magento/composer-root-update-plugin` installieren (siehe [Voraussetzungen](../prepare/prerequisites.md)). Darüber hinaus wurden die Befehle zum Aktualisieren von `composer require magento/<package_name>` in `composer require-commerce magento/<package_name>` geändert.

## Bevor Sie beginnen

Sie müssen die [Upgrade-Voraussetzungen](../prepare/prerequisites.md) abschließen, um Ihre Umgebung vorzubereiten, bevor Sie den Upgrade-Prozess starten.

## Verwalten von Paketen

>[!NOTE]
>
>In den Beispielen am Ende dieses Abschnitts finden Sie Hilfe bei der Angabe verschiedener Versionsebenen. Beispielsweise hochwertige Patches und Sicherheits-Patches. Wenn Sie diese Pakete nicht in Composer finden können, wenden Sie sich an den Adobe Commerce-Support.

1. Wechseln Sie in den Wartungsmodus, um den Zugriff auf Ihren Store während des Upgrade-Prozesses zu verhindern.

   ```bash
   bin/magento maintenance:enable
   ```

   Siehe [Aktivieren oder Deaktivieren des ](../../installation/tutorials/maintenance-mode.md)) für zusätzliche Optionen. Optional können Sie eine [benutzerdefinierte Wartungsmodusseite“ ](../troubleshooting/maintenance-mode-options.md).

1. Das Starten des Upgrade-Prozesses während der Ausführung asynchroner Prozesse, z. B. der Nachrichtenwarteschlange für Verbraucher, kann zu Datenbeschädigungen führen. Um Datenbeschädigungen zu verhindern, deaktivieren Sie alle Cron-Aufträge.

   _Adobe Commerce auf Cloud-Infrastruktur:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. Starten Sie alle Nachrichtenwarteschlangenbenutzer manuell, um sicherzustellen, dass alle Nachrichten verarbeitet werden.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   Warten Sie, bis der Cron-Vorgang abgeschlossen ist. Sie können den Status des Auftrags mit einem Prozess-Viewer überwachen oder indem Sie den `ps aux | grep 'bin/magento queue'`-Befehl mehrmals ausführen, bis alle Prozesse abgeschlossen sind.

1. Erstellen Sie eine Sicherung der `composer.json`.

   ```bash
   cp composer.json composer.json.bak
   ```

1. Fügen Sie bestimmte Pakete je nach Bedarf hinzu oder entfernen Sie sie.

   Wenn Sie beispielsweise ein Upgrade von Magento Open Source auf Adobe Commerce durchführen, entfernen Sie das Magento Open Source-Package.

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

1. Aktualisieren Sie Ihre Instanz mithilfe der folgenden `composer require-commerce`-Befehlssyntax:

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   Zu den Befehlsoptionen gehören:

   - `<product>` - (Erforderlich) Das zu aktualisierende Paket. Bei On-Premise-Installationen muss dieser Wert entweder `product-community-edition` oder `product-enterprise-edition` sein.

   - `<version>` - (Erforderlich) Die Adobe Commerce-Version, auf die Sie ein Upgrade durchführen. Beispiel: `2.4.3`.

   - `--no-update` -(Erforderlich) Deaktiviert die automatische Aktualisierung der Abhängigkeiten.

   - `--interactive-root-conflicts` - (Optional) Ermöglicht die interaktive Anzeige und Aktualisierung veralteter Werte aus früheren Versionen oder benutzerdefinierter Werte, die nicht mit der Version übereinstimmen, auf die Sie ein Upgrade durchführen.

   - `--force-root-updates` - (Optional) Überschreibt alle im Konflikt stehenden benutzerdefinierten Werte mit den erwarteten Commerce-Werten.

   - `--help` - (Optional) Enthält Nutzungsdetails zum Plug-in.

   Wenn weder `--interactive-root-conflicts` noch `--force-root-updates` angegeben sind, behält der Befehl die vorhandenen Werte bei, die in Konflikt stehen, und zeigt eine Warnmeldung an. Weitere Informationen zum Plug-in finden Sie in der [README zur Verwendung von Plug-ins](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. Aktualisieren Sie die Abhängigkeiten.

   ```bash
   composer update
   ```

### Beispiel - Liste der verfügbaren Versionen

So zeigen Sie die vollständige Liste der verfügbaren 2.4.x-Versionen an:

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### Beispiel - Qualitäts-Patch

Qualitäts-Patches enthalten hauptsächlich funktionale _und_ Sicherheitskorrekturen. Sie können jedoch manchmal neue, abwärtskompatible Funktionen enthalten. Verwenden Sie Composer, um einen Qualitäts-Patch herunterzuladen.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### Beispiel - Sicherheits-Patch

Sicherheits-Patches enthalten nur Sicherheitskorrekturen. Sie wurden entwickelt, um den Upgrade-Prozess schneller und einfacher zu machen. Sicherheits-Patches verwenden die Composer-Namenskonvention `2.4.x-px`.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## Aktualisieren von Metadaten

1. Aktualisieren Sie die Felder `"name"`, `"version"` und `"description"` in der `composer.json` nach Bedarf.

   >[!NOTE]
   >
   >Die Aktualisierung der Metadaten in der `composer.json`-Datei ist nur oberflächlich, nicht funktionsfähig.

1. Aktualisierungen anwenden.

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

1. Datenbankschema und -daten aktualisieren.

   ```bash
   bin/magento setup:upgrade
   ```

1. Deaktivieren Sie den Wartungsmodus.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(optional)_ Lack neu starten.

   Wenn Sie Lack für das Zwischenspeichern von Seiten verwenden, starten Sie es neu:

   ```bash
   service varnish restart
   ```

## Überprüfen Sie Ihre Arbeit

Um zu überprüfen, ob das Upgrade erfolgreich war, öffnen Sie Ihre Storefront-URL in einem Webbrowser. Wenn das Upgrade nicht erfolgreich war, wird Ihre Storefront nicht ordnungsgemäß geladen.

Wenn die Anwendung mit einem `We're sorry, an error has occurred while generating this email.` Fehler fehlschlägt:

1. Setzen Sie [Dateisysteminhaber und -berechtigungen](../../installation/prerequisites/file-system/configure-permissions.md) als Benutzer mit `root` zurück.
1. Löschen Sie die folgenden Ordner:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Überprüfen Sie Ihre Storefront in Ihrem Webbrowser erneut.
