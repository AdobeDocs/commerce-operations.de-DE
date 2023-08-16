---
title: Aktualisieren Sie die [!DNL Data Migration Tool]
description: Erfahren Sie, wie Sie die [!DNL Data Migration Tool] um Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Aktualisieren Sie die [!DNL Data Migration Tool]

Um sicherzustellen, dass die Versionen Ihrer aktuellen Magento 2-Installation und die [!DNL Data Migration Tool] genau übereinstimmen, müssen Sie möglicherweise das Tool aktualisieren.

## Voraussetzungen

Vor der Aktualisierung [!DNL Data Migration Tool]müssen Sie:

* Aktualisieren Sie Ihre Magento-Software, um die neueste Version zu erhalten

* Sichern Sie die `vendor/magento/data-migration-tool` directory

* Stellen Sie sicher, dass die Variable [!DNL Data Migration Tool] Version entspricht der Magento-Anwendungsversion

### Magento-Software aktualisieren

Wenn Sie das noch nicht getan haben, [Aktualisieren der Magento-Software](../../upgrade/overview.md).

### Sichern Sie die `vendor/magento/data-migration-tool` directory

Vor der Aktualisierung [!DNL Data Migration Tool], um mindestens die `vendor/magento/data-migration-tool` Verzeichnis. Während der Aktualisierung konnte sie gelöscht und durch den aktualisierten Code ersetzt werden.

Sie können auch die gesamte Magento-Codebase und -Datenbank mithilfe des folgenden Befehls sichern:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>Die `vendor/magento/data-migration-tool` enthält Ihren benutzerdefinierten Code. Wenn Sie dies nicht sichern, können Sie Ihre Anpassungen während der Aktualisierung verlieren.


### Sicherstellen, dass Versionen übereinstimmen

Die Versionen der [!DNL Data Migration Tool] und Ihre Magento-Software muss genau übereinstimmen. Für Magento 2.1.2 ist beispielsweise die Version 2.1.2 des [!DNL Data Migration Tool].

Siehe [Installieren [!DNL Data Migration Tool]](install.md) Thema, um zu erfahren, wie:

* [Überprüfen](install.md#check-your-version) Ihre Magento 2-Version

* [Suchen](install.md#find-released-versions-of-data-migration-tool) veröffentlichte Versionen der [!DNL Data Migration Tool]

* [Überprüfen](install.md#check-version-of-installed-data-migration-tool) die [!DNL Data Migration Tool] version

## Aktualisieren Sie die [!DNL Data Migration Tool]

1. Melden Sie sich bei Ihrem Anwendungsserver an oder wechseln Sie zu [der Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie zum Stammverzeichnis der Anwendung.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   where `<version>` muss mit der Version der Magento 2-Codebase übereinstimmen.

   Geben Sie beispielsweise für Version 2.1.2 Folgendes ein:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Warten Sie, bis der Befehl abgeschlossen ist.
