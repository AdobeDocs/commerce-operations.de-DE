---
title: '[!DNL Data Migration Tool] Voraussetzungen'
description: Erfahren Sie, was Sie tun müssen, bevor Sie mit der Verwendung von [!DNL Data Migration Tool] beginnen, um Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Data Migration Tool] Voraussetzungen

Bevor Sie mit der Migration beginnen, stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind.

## Magento 2-System

* Richten Sie Ihr Magento 2-System so ein, dass es die [Systemanforderungen](../../installation/system-requirements.md) erfüllt.

  Verwenden Sie eine Topologie und ein Design, die mindestens Ihrem bestehenden Magento 1-System entspricht.

* [Installieren Sie Magento 2](../../installation/overview.md).

## Cron

Starten Sie keine Magento 2 Cron-Aufträge.

## Datenbank

* Sichern Sie nach der Installation so bald wie möglich Ihre Magento 2-Datenbank oder [dump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html). Auf diese Weise können Sie den ursprünglichen Datenbankstatus wiederherstellen, wenn die Migration nicht erfolgreich war.

* Überprüfen Sie, ob der [!DNL Data Migration Tool] Netzwerkzugriff hat, um die Magento 1- und Magento 2-Datenbanken zu verbinden.

  Öffnen Sie Ports in Ihrer Firewall, damit das Migrationswerkzeug mit den Datenbanken kommunizieren kann.

* Stellen Sie sicher, dass Ihre MySQL-Konten über alle erforderlichen Berechtigungen zum Zugriff auf Magento-Datenbanken verfügen.

Wenn die binäre Protokollierung für Ihre Magento 1-Datenbank aktiviert ist, setzen Sie die globale MySQL-Systemvariable [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) auf `1` oder gewähren Sie Ihrem Konto die Berechtigung [SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super).

* Es wird empfohlen, vor der Migration keine neuen Entitäten (Produkte, Kategorien und Attribute) in Ihrem Magento 2-Store zu erstellen, da die [!DNL Data Migration Tool] diese neuen Entitäten mit den alten von Magento 1 überschreibt.

## Erweiterungen

Migrieren Sie den Magento 1-Erweiterungscode auf Magento 2.

Die neuesten Erweiterungsversionen finden Sie unter [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) oder kontaktieren Sie Ihren Erweiterungsanbieter.

Sie können auch den [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md) verwenden.
