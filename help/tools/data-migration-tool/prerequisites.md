---
title: '[!DNL Data Migration Tool] Voraussetzungen'
description: Erfahren Sie, was Sie tun müssen, bevor Sie mit der Verwendung des [!DNL Data Migration Tool] zur Übertragung von Daten zwischen Magento 1 und Magento 2.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# [!DNL Data Migration Tool] Voraussetzungen

Bevor Sie mit der Migration beginnen, stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind.

## Magento 2-System

* Richten Sie das Magento 2-System so ein, dass es die [Systemanforderungen](../../installation/system-requirements.md).

  Verwenden Sie eine Topologie und ein Design, die mindestens mit Ihrem bestehenden Magento 1-System übereinstimmen.

* [Magento 2 installieren](../../installation/overview.md).

## Cron

Starten Sie keine Cron-Aufträge für Magento 2.

## Datenbank

* Nach der Installation sichern oder [dump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) Ihre Magento 2-Datenbank so bald wie möglich. Auf diese Weise können Sie den ursprünglichen Datenbankstatus wiederherstellen, wenn die Migration nicht erfolgreich war.

* Überprüfen Sie, ob die [!DNL Data Migration Tool] verfügt über Netzwerkzugriff, um die Datenbanken von Magento 1 und Magento 2 zu verbinden.

  Öffnen Sie Ports in Ihrer Firewall, damit das Migrationswerkzeug mit den Datenbanken kommunizieren kann.

* Stellen Sie sicher, dass Ihre MySQL-Konten über alle erforderlichen Berechtigungen für den Zugriff auf Magento-Datenbanken verfügen.

Wenn die binäre Protokollierung für Ihre Magento 1-Datenbank aktiviert ist, legen Sie die globale [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL-Systemvariable zu `1`oder gewähren Sie die [Berechtigung SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) auf Ihr Konto ein.

* Wir empfehlen nicht, vor der Migration neue Entitäten (Produkte, Kategorien und Attribute) in Ihrem Magento 2-Store zu erstellen, da die Variable [!DNL Data Migration Tool] überschreibt solche neuen Entitäten mit den alten aus Magento 1.

## Erweiterungen

Migrieren Sie den Magento 1-Erweiterungscode nach Magento 2.

Die neuesten Erweiterungsversionen finden Sie unter [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) oder wenden Sie sich an Ihren Erweiterungsanbieter.

Sie können auch die [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
