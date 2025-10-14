---
title: Voraussetzungen für [!DNL Data Migration Tool]
description: Erfahren Sie, was Sie tun müssen, bevor Sie mit der  [!DNL Data Migration Tool] zur Datenübertragung zwischen Magento 1 und Magento 2 beginnen.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Voraussetzungen für [!DNL Data Migration Tool]

Bevor Sie mit der Migration beginnen, stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind.

## Magento 2-System

* Richten Sie Ihr Magento 2-System so ein, dass es die [Systemanforderungen“ &#x200B;](../../installation/system-requirements.md).

  Verwenden Sie eine Topologie und ein Design, die mindestens Ihrem bestehenden Magento 1-System entsprechen.

* [Installieren von Magento 2](../../installation/overview.md).

## Cron

Starten Sie keine Magento 2-Cron-Aufträge.

## Datenbank

* Sichern oder [&#x200B; Sie Ihre Magento 2](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)Datenbank nach der Installation so schnell wie möglich. Auf diese Weise können Sie den ursprünglichen Datenbankstatus wiederherstellen, wenn die Migration nicht erfolgreich war.

* Überprüfen Sie, ob der [!DNL Data Migration Tool] über Netzwerkzugriff verfügt, um die Magento 1- und Magento 2-Datenbanken zu verbinden.

  Öffnen Sie Ports in Ihrer Firewall, damit das Migrations-Tool mit den Datenbanken kommunizieren kann.

* Stellen Sie sicher, dass Ihre MySQL-Konten über alle erforderlichen Berechtigungen für den Zugriff auf Magento-Datenbanken verfügen.

Wenn die Binärprotokollierung für Ihre Magento 1-Datenbank aktiviert ist, legen Sie die globale [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL-Systemvariable auf `1` fest oder gewähren Sie Ihrem Konto die [SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super)Berechtigung.

* Es wird nicht empfohlen, vor der Migration neue Entitäten (Produkte, Kategorien und Attribute) in Ihrem Magento 2 Store zu erstellen, da die [!DNL Data Migration Tool] solche neuen Entitäten mit den alten aus Magento 1 überschreibt.

## Erweiterungen

Migrieren des Magento 1-Erweiterungs-Codes zu Magento 2.

Um die neuesten Erweiterungsversionen zu finden, besuchen Sie [[!DNL [Commerce Marketplace]]](https://marketplace.magento.com/) oder wenden Sie sich an Ihren Erweiterungsanbieter.

Sie können auch die [[!DNL [Code Migration Tool]]](https://github.com/magento-commerce/code-migration/blob/develop/README.md) verwenden.
