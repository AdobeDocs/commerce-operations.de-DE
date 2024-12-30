---
title: Aktualisieren Sie die [!DNL Data Migration Tool]
description: Erfahren Sie, wie Sie die  [!DNL Data Migration Tool]  aktualisieren, um Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Aktualisieren der [!DNL Data Migration Tool]

Um sicherzustellen, dass die Versionen Ihrer aktuellen Magento 2-Installation und die [!DNL Data Migration Tool] genau übereinstimmen, müssen Sie möglicherweise das Tool aktualisieren.

## Voraussetzungen

Bevor Sie ein Upgrade des [!DNL Data Migration Tool] durchführen, müssen Sie:

* Aktualisieren Sie Ihre Magento-Software, um die neueste Version zu erhalten

* Sichern Sie das `vendor/magento/data-migration-tool`

* Stellen Sie sicher, dass die [!DNL Data Migration Tool] mit der Magento-Anwendungsversion übereinstimmt

### Upgrade der Magento-Software

Falls Sie dies noch nicht getan haben, [ Sie die Magento-Software ](../../upgrade/overview.md).

### Sichern Sie das `vendor/magento/data-migration-tool`

Sichern Sie vor dem Upgrade des [!DNL Data Migration Tool] mindestens das `vendor/magento/data-migration-tool`. Während des Upgrades konnte er gelöscht und durch den aktualisierten Code ersetzt werden.

Sie können auch die gesamte Magento-Codebasis und -Datenbank mit folgendem Befehl sichern:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>Das `vendor/magento/data-migration-tool` enthält den benutzerdefinierten Code. Wenn die Sicherung nicht durchgeführt wird, können Ihre Anpassungen während des Upgrades verloren gehen.


### Übereinstimmende Versionen sicherstellen

Die Versionen des [!DNL Data Migration Tool] und Ihrer Magento-Software müssen exakt übereinstimmen. Für Magento 2.1.2 ist beispielsweise Version 2.1.2 des [!DNL Data Migration Tool] erforderlich.

Weitere Informationen finden Sie [ Thema  [!DNL Data Migration Tool]](install.md)Installieren):

* [Überprüfen](install.md#check-your-version) Sie Ihre Magento 2-Version

* [Suchen](install.md#find-released-versions-of-data-migration-tool) freigegebene Versionen des [!DNL Data Migration Tool]

* [Überprüfen](install.md#check-version-of-installed-data-migration-tool) die [!DNL Data Migration Tool] Version

## Aktualisieren der [!DNL Data Migration Tool]

1. Melden Sie sich bei Ihrem Anwendungs-Server als oder wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie in das Stammverzeichnis der Anwendung.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   wobei `<version>` mit der Magento 2-Codebase übereinstimmen muss.

   Geben Sie beispielsweise für Version 2.1.2 Folgendes ein:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Warten Sie, während der Befehl abgeschlossen wird.
