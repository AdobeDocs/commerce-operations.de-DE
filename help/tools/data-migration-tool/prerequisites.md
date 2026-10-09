---
title: Voraussetzungen für [!DNL Data Migration Tool]
description: Erfahren Sie, was Sie tun müssen, bevor Sie mit der Verwendung des [!DNL Data Migration Tool] beginnen, um Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
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
source-wordcount: '266'
ht-degree: 0%
---
# Voraussetzungen für [!DNL Data Migration Tool]

Bevor Sie mit der Migration beginnen, stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind.

## Magento 2-System

* Richten Sie Ihr Magento 2-System so ein, dass es die [Systemanforderungen](../../installation/system-requirements.md) erfüllt.

  Verwenden Sie eine Topologie und ein Design, die mindestens Ihrem vorhandenen Magento 1-System entsprechen.

* [Installieren von Magento 2](../../installation/overview.md).

## Cron

Starten Sie keine Magento 2 Cron-Aufträge.

## Datenbank

* Sichern oder [ Sie Ihre Magento 2](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)Datenbank nach der Installation so schnell wie möglich. Auf diese Weise können Sie den ursprünglichen Datenbankstatus wiederherstellen, wenn die Migration nicht erfolgreich war.

* Überprüfen Sie, ob der [!DNL Data Migration Tool] über Netzwerkzugriff verfügt, um die Magento 1- und Magento 2-Datenbanken zu verbinden.

  Öffnen Sie Ports in Ihrer Firewall, damit das Migrations-Tool mit den Datenbanken kommunizieren kann.

* Stellen Sie sicher, dass Ihre MySQL-Konten über alle erforderlichen Berechtigungen für den Zugriff auf Magento-Datenbanken verfügen.

Wenn die Binärprotokollierung für Ihre Magento 1-Datenbank aktiviert ist, legen Sie die globale [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL-Systemvariable auf `1` fest oder gewähren Sie Ihrem Konto die [SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super)Berechtigung.

* Es wird nicht empfohlen, vor der Migration neue Entitäten (Produkte, Kategorien und Attribute) in Ihrem Magento 2 -Store zu erstellen, da die [!DNL Data Migration Tool] solche neuen Entitäten mit den alten von Magento 1 überschreibt.

## Erweiterungen

Migrieren Sie den Magento 1-Erweiterungs-Code zu Magento 2.

Um die neuesten Erweiterungsversionen zu finden, besuchen Sie [!DNL [Commerce Marketplace]](https://commercemarketplace.adobe.com//) oder wenden Sie sich an Ihren Erweiterungsanbieter.

Sie können auch die [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md) verwenden.
