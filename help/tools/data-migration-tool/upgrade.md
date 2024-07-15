---
title: Aktualisieren Sie den [!DNL Data Migration Tool]
description: Erfahren Sie, wie Sie die [!DNL Data Migration Tool] aktualisieren, um Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Aktualisieren Sie die [!DNL Data Migration Tool]

Um sicherzustellen, dass die Versionen Ihrer aktuellen Magento 2-Installation und die [!DNL Data Migration Tool] genau übereinstimmen, müssen Sie möglicherweise das Tool aktualisieren.

## Voraussetzungen

Vor der Aktualisierung von [!DNL Data Migration Tool] müssen Sie:

* Aktualisieren Sie Ihre Magento-Software, um die neueste Version zu erhalten

* Sichern des Verzeichnisses `vendor/magento/data-migration-tool`

* Stellen Sie sicher, dass die [!DNL Data Migration Tool] -Version mit der Magento-Anwendungsversion übereinstimmt.

### Magento-Software aktualisieren

Wenn Sie dies noch nicht getan haben, aktualisieren Sie die Magento-Software](../../upgrade/overview.md).[

### Sichern des Verzeichnisses `vendor/magento/data-migration-tool`

Sichern Sie vor dem Upgrade von [!DNL Data Migration Tool] mindestens das Verzeichnis `vendor/magento/data-migration-tool` . Während der Aktualisierung konnte sie gelöscht und durch den aktualisierten Code ersetzt werden.

Sie können auch die gesamte Magento-Codebase und -Datenbank mithilfe des folgenden Befehls sichern:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>Das Verzeichnis `vendor/magento/data-migration-tool` enthält Ihren benutzerdefinierten Code. Wenn Sie dies nicht sichern, können Sie Ihre Anpassungen während der Aktualisierung verlieren.


### Sicherstellen, dass Versionen übereinstimmen

Die Versionen von [!DNL Data Migration Tool] und Ihrer Magento-Software müssen genau übereinstimmen. Für Magento 2.1.2 ist beispielsweise die Version 2.1.2 von [!DNL Data Migration Tool] erforderlich.

Weitere Informationen finden Sie im Thema [Installieren [!DNL Data Migration Tool]](install.md) .

* [Überprüfen Sie ](install.md#check-your-version) Ihre Magento 2-Version

* [Find](install.md#find-released-versions-of-data-migration-tool) veröffentlichte Versionen der [!DNL Data Migration Tool]

* [Überprüfen](install.md#check-version-of-installed-data-migration-tool) der [!DNL Data Migration Tool]-Version

## Aktualisieren Sie die [!DNL Data Migration Tool]

1. Melden Sie sich bei Ihrem Anwendungsserver als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) an oder wechseln Sie zu ihm.
1. Wechseln Sie zum Stammverzeichnis der Anwendung.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   wobei `<version>` mit der Magento 2-Codebase übereinstimmen muss.

   Geben Sie beispielsweise für Version 2.1.2 Folgendes ein:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Warten Sie, bis der Befehl abgeschlossen ist.
