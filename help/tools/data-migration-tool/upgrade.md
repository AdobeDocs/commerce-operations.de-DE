---
title: Aktualisieren der [!DNL Data Migration Tool]
description: Erfahren Sie, wie Sie die [!DNL Data Migration Tool] zur Datenübertragung zwischen Magento 1 und Magento 2 aktualisieren.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
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
source-wordcount: '235'
ht-degree: 0%
---
# Aktualisieren der [!DNL Data Migration Tool]

Um sicherzustellen, dass die Versionen Ihrer aktuellen Magento 2-Installation und die [!DNL Data Migration Tool] genau übereinstimmen, müssen Sie möglicherweise das Tool aktualisieren.

## Voraussetzungen

Bevor Sie ein Upgrade des [!DNL Data Migration Tool] durchführen, müssen Sie:

* Aktualisieren Sie Ihre Magento-Software, um die neueste Version zu erhalten

* Sichern Sie das `vendor/magento/data-migration-tool`

* Stellen Sie sicher, dass die [!DNL Data Migration Tool] Version mit der Version des Magento-Programms übereinstimmt

### Aktualisieren der Magento-Software

Falls Sie dies noch nicht getan haben, [&#x200B; Sie die Magento-Software &#x200B;](../../upgrade/overview.md).

### Sichern Sie das `vendor/magento/data-migration-tool`

Sichern Sie vor dem Upgrade des [!DNL Data Migration Tool] mindestens das `vendor/magento/data-migration-tool`. Während des Upgrades konnte er gelöscht und durch den aktualisierten Code ersetzt werden.

Sie können auch die gesamte Magento-Codebasis und -Datenbank mit dem folgenden Befehl sichern:

```shell
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>Das `vendor/magento/data-migration-tool` enthält den benutzerdefinierten Code. Wenn die Sicherung nicht durchgeführt wird, können Ihre Anpassungen während des Upgrades verloren gehen.


### Übereinstimmende Versionen sicherstellen

Die Versionen des [!DNL Data Migration Tool] und Ihrer Magento-Software müssen genau übereinstimmen. Magento 2.1.2 erfordert beispielsweise Version 2.1.2 des [!DNL Data Migration Tool].

Weitere Informationen finden Sie [&#x200B; Thema  [!DNL Data Migration Tool]](install.md)Installieren):

* [Überprüfen](install.md#check-your-version) Ihre Magento 2-Version

* [Suchen](install.md#find-released-versions-of-data-migration-tool) freigegebene Versionen des [!DNL Data Migration Tool]

* [Überprüfen](install.md#check-version-of-installed-data-migration-tool) die [!DNL Data Migration Tool] Version

## Aktualisieren der [!DNL Data Migration Tool]

1. Melden Sie sich bei Ihrem Anwendungs-Server als oder wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie in das Stammverzeichnis der Anwendung.
1. Geben Sie den folgenden Befehl ein:

   ```shell
   composer require magento/data-migration-tool:<version>
   ```

   wobei `<version>` mit der Version der Magento 2-Codebasis übereinstimmen muss.

   Geben Sie beispielsweise für Version 2.1.2 Folgendes ein:

   ```shell
   composer require magento/data-migration-tool:2.1.2
   ```

1. Warten Sie, während der Befehl abgeschlossen wird.
