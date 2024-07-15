---
title: Installieren Sie den  [!DNL Data Migration Tool]
description: Erfahren Sie, wie Sie den [!DNL Data Migration Tool] installieren, um Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Installieren Sie die [!DNL Data Migration Tool]

>[!INFO]
>
>Die Versionen von Magento und [!DNL Data Migration Tool] müssen übereinstimmen.


Stellen Sie sicher, dass Sie *dieselbe veröffentlichte Version* sowohl von Magento 2 als auch von [!DNL Data Migration Tool] verwenden. Für Magento Version 2.2.0 müssen Sie beispielsweise auch die [!DNL Data Migration Tool] -Version 2.2.0 verwenden.

## Überprüfen der Version

Nehmen Sie eine der folgenden Methoden vor, um Ihre Version von Magento zu überprüfen:

- [Verfasser](#composer-metapackage)
- [GitHub-Repository](#github-repository)

### Composer-Metapaket

Wenn Sie die Magento-Software mit einem Composer-Metapaket heruntergeladen haben, geben Sie den folgenden Befehl ein:

```bash
php <magento_root>/bin/magento --version
```

### GitHub-Repository

Wenn Sie das Magento 2 GitHub-Repository geklont haben, geben Sie die folgenden Befehle ein:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Wenn Sie sich derzeit im `develop`-Zweig befinden, müssen Sie zu einer [veröffentlichten Verzweigung](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) wechseln, bevor Sie fortfahren.

Wenn Sie die Adobe Commerce-Software noch nicht installiert haben, [installieren Sie sie jetzt](../../installation/prerequisites/commerce.md).
Wenn Sie das GitHub-Repository klonen, prüfen Sie unbedingt ein Release-Tag, wie unter [ (Mitarbeiter) Clone the GitHub repository](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) beschrieben.

## Erstellte Versionen von [!DNL Data Migration Tool] finden

Rufen Sie die Seite [Versionen](https://github.com/magento/data-migration-tool/releases) des GitHub-Repositorys [!DNL Data Migration Tool] auf, um verfügbare veröffentlichte Versionen zu finden.

## Installieren Sie die [!DNL Data Migration Tool]

Sie können den [!DNL Data Migration Tool] aus folgenden Quellen installieren:

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Stellen Sie vor der Installation Folgendes sicher:

- Alle im Abschnitt [Vorbedingungen](prerequisites.md) genannten Aufgaben abgeschlossen
- [Version](install.md#check-your-version) der Magento 2-Software verifiziert

### Installieren von `repo.magento.com`

Um die [!DNL Data Migration Tool] zu installieren, müssen Sie `composer.json` im Installationsverzeichnis des Magento-Stammordners aktualisieren, um den Speicherort des [!DNL Data Migration Tool]-Pakets anzugeben.

1. Melden Sie sich bei Ihrem Anwendungsserver als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) an oder wechseln Sie zu ihm.
1. Wechseln Sie zum Stammverzeichnis der Anwendung.
1. Geben Sie die folgenden Befehle ein:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Wobei `<version>` mit der Version der Magento 2-Codebase übereinstimmen muss.

   Geben Sie beispielsweise für Version 2.2.0 Folgendes ein:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Geben Sie bei Aufforderung die [Authentifizierungsschlüssel](../../installation/prerequisites/authentication-keys.md) ein. Ihr öffentlicher Schlüssel ist Ihr Benutzername, Ihr privater Schlüssel ist Ihr Passwort.

### Von GitHub installieren

Wenn Sie das GitHub-Repository geklont haben, führen Sie die folgenden Schritte aus, um die [!DNL Data Migration Tool] zu installieren.

1. Melden Sie sich bei Ihrem Anwendungsserver als [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md) an oder wechseln Sie zu ihm.
1. Wechseln Sie zum Stammverzeichnis der Anwendung.
1. Geben Sie die folgenden Befehle ein:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   wobei `<version>` mit der Magento 2-Codebase übereinstimmen muss.

   Geben Sie beispielsweise für Version 2.2.0 Folgendes ein:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Überprüfen der Version von installiertem [!DNL Data Migration Tool]

1. Ändern Sie in Ihr Verzeichnis [!DNL Data Migration Tool]: `<vendor>/magento/data-migration-tool`.

1. Öffnen Sie [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) in einem Texteditor.

1. Der Eintrag `version` in dieser Datei ist die Version des [!DNL Data Migration Tool].
