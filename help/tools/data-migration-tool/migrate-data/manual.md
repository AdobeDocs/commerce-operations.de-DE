---
title: Daten, die manuell migriert werden müssen
description: Erfahren Sie mehr über Daten, die während einer Datenmigration von Magento 1 zu Magento 2 manuell migriert werden müssen, und wie Sie dies tun können.
exl-id: 830abd81-4c6d-418b-9da4-b6acd95f5ec8
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%
---
# Daten, die manuell migriert werden müssen

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
>Die Speichermethode für Datenbankmedien wird seit Magento 2.4.3 nicht mehr unterstützt.


Dieser Abschnitt gilt nur für *,* Sie Mediendateien in der Magento-Datenbank speichern. Dieser Schritt sollte vor der [Datenmigration) ](data.md) werden:

1. Melden Sie sich beim Magento 1 Admin Panel als Administrator an.

1. Klicken Sie auf **System** > **Konfiguration** > ERWEITERT > **System**.

1. Scrollen Sie im rechten Bereich zu **Speicherkonfiguration für Medien**.

1. Klicken Sie in der **Mediendatenbank auswählen** auf den Namen Ihrer Medienspeicherdatenbank.

1. Klicken Sie **Synchronisieren**.

Wiederholen Sie dann dieselben Schritte in Ihrem Magento 2 Admin-Bedienfeld.

### Mediendateien im Dateisystem

Alle Mediendateien (Bilder für Produkte, Kategorien, den WYSIWYG-Editor usw.) sollten manuell von `<your Magento 1 install dir>/media` nach `<your Magento 2 install dir>/pub/media` kopiert werden.

Kopieren Sie jedoch *nicht* die `.htaccess` Dateien im Ordner Magento 1 `media` . Magento 2 verfügt über eine eigene `.htaccess`, die beibehalten werden sollte.

## Storefront-Design

* Das Design in -Dateien (CSS, JS, Vorlagen, XML-Layouts) hat den Speicherort und das Format geändert

* In der Datenbank gespeicherte Layout-Aktualisierungen. Platziert über Magento 1 Admin in CMS Pages, CMS Widgets, Kategorieseiten und Produktseiten

## Zugriffssteuerungslisten (ACLs)

Sie müssen alle manuell neu erstellen:

* Anmeldedaten für Webservice-APIs (SOAP, XML-RPC und REST)

* Administratorkonten verwenden und sie mit Zugriffsberechtigungen verknüpfen

>[!NOTE]
>
>Sie können die Zeitzone für eine Datenbankentität mithilfe des `\Migration\Handler\Timezone`-Handlers anpassen. Weitere Informationen finden [ im Abschnitt ](follow-up.md)Follow-up“.
