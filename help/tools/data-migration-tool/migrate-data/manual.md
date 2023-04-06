---
title: Daten, die eine manuelle Migration erfordern
description: Erfahren Sie mehr über Daten, die bei der Datenmigration aus dem Magento 1 nach Magento 2 manuell migriert werden müssen, und wie Sie dies durchführen können.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Daten, die eine manuelle Migration erfordern

Es gibt vier Arten von Daten, die manuell migriert werden müssen:

* Medien

* Storefront-Design

* Admin-Benutzerkonten

* Zugriffssteuerungslisten (ACLs)

## Medien

In diesem Abschnitt wird beschrieben, wie Sie Mediendateien manuell migrieren.

### In der Datenbank gespeicherte Mediendateien

>[!WARNING]
>
>Die Speichermethode für Datenbankmedien wird ab Magento 2.4.3 nicht mehr unterstützt.


Dieser Abschnitt gilt für Sie *only* , wenn Sie Mediendateien in der Magento-Datenbank speichern. Dieser Schritt sollte vor [Datenmigration](data.md):

1. Melden Sie sich beim Admin Panel von Magento 1 als Administrator an.

1. Klicken **System** > **Konfiguration** > ERWEITERT > **System**.

1. Scrollen Sie im rechten Bereich zu **Speicherkonfiguration für Medien**.

1. Aus dem **Mediendatenbank auswählen** klicken Sie auf den Namen Ihrer Medienspeicherdatenbank.

1. Klicken **Synchronisieren**.

Wiederholen Sie dann dieselben Schritte in Ihrem Magento 2 Admin-Bedienfeld.

### Mediendateien im Dateisystem

Alle Mediendateien (Bilder für Produkte, Kategorien, den WYSIWYG-Editor usw.) sollten manuell aus kopiert werden `<your Magento 1 install dir>/media` nach `<your Magento 2 install dir>/pub/media`.

Führen Sie jedoch *not* Kopieren Sie die `.htaccess` Dateien im Magento 1 `media` Ordner. Magento 2 hat eigene `.htaccess` die beibehalten werden sollen.

## Storefront-Design

* Das Design in Dateien (CSS, JS, Vorlagen, XML-Layouts) hat seinen Speicherort und sein Format geändert

* In der Datenbank gespeicherte Layout-Aktualisierungen. Platziert über Magento 1 Admin in CMS-Seiten, CMS-Widgets, Kategorieseiten und Produktseiten

## Zugriffssteuerungslisten (ACLs)

Sie müssen alle Elemente manuell neu erstellen:

* Anmeldeinformationen für Webdienst-APIs (SOAP, XML-RPC und REST)

* Admin-Benutzerkonten und Zuordnen dieser zu Zugriffsberechtigungen

>[!NOTE]
>
>Sie können die Zeitzone für eine Datenbankentität mithilfe der Variablen `\Migration\Handler\Timezone` Handler. Siehe [Folgemaßnahmen](follow-up.md) für weitere Details.
