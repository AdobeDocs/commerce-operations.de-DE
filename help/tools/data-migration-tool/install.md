---
title: Installieren Sie die [!DNL Data Migration Tool]
description: Erfahren Sie, wie Sie die [!DNL Data Migration Tool] um Daten zwischen Magento 1 und Magento 2 zu übertragen.
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
>Versionen von Magento und [!DNL Data Migration Tool] muss übereinstimmen.


Stellen Sie sicher, dass Sie *dieselbe veröffentlichte Version* sowohl Magento 2 als auch [!DNL Data Migration Tool]. Für Magento Version 2.2.0 müssen Sie beispielsweise auch die Variable [!DNL Data Migration Tool] Version 2.2.0.

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

Wenn Sie sich derzeit im `develop` Verzweigung, müssen Sie zu einer [freigegebene Verzweigung](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) bevor Sie fortfahren.

Wenn Sie die Adobe Commerce-Software noch nicht installiert haben, [jetzt installieren](../../installation/prerequisites/commerce.md).
Wenn Sie das GitHub-Repository klonen, prüfen Sie unbedingt ein Release-Tag, wie hier beschrieben: [(Mitarbeiter) GitHub-Repository klonen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

## Erstellte Versionen von finden [!DNL Data Migration Tool]

Navigieren Sie zu [Versionen](https://github.com/magento/data-migration-tool/releases) der [!DNL Data Migration Tool] GitHub-Repository , um verfügbare veröffentlichte Versionen zu finden.

## Installieren Sie die [!DNL Data Migration Tool]

Sie können die [!DNL Data Migration Tool] von:

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Stellen Sie vor der Installation Folgendes sicher:

- Alle im Abschnitt [Voraussetzungen](prerequisites.md) Abschnitt
- [Version überprüft](install.md#check-your-version) der Magento 2-Software

### Installieren von `repo.magento.com`

So installieren Sie die [!DNL Data Migration Tool], müssen Sie `composer.json` im Installationsverzeichnis des Magento-Stammordners, um den Speicherort der [!DNL Data Migration Tool] Paket.

1. Melden Sie sich bei Ihrem Anwendungsserver als an oder wechseln Sie zu der [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie zum Stammverzeichnis der Anwendung.
1. Geben Sie die folgenden Befehle ein:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Wo `<version>` muss mit der Version der Magento 2-Codebase übereinstimmen.

   Geben Sie beispielsweise für Version 2.2.0 Folgendes ein:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Geben Sie bei Aufforderung Ihre [Authentifizierungsschlüssel](../../installation/prerequisites/authentication-keys.md). Ihr öffentlicher Schlüssel ist Ihr Benutzername, Ihr privater Schlüssel ist Ihr Passwort.

### Von GitHub installieren

Wenn Sie das GitHub-Repository geklont haben, führen Sie die folgenden Schritte aus, um das [!DNL Data Migration Tool].

1. Melden Sie sich bei Ihrem Anwendungsserver als an oder wechseln Sie zu der [Dateisysteminhaber](../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie zum Stammverzeichnis der Anwendung.
1. Geben Sie die folgenden Befehle ein:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   where `<version>` muss mit der Version der Magento 2-Codebase übereinstimmen.

   Geben Sie beispielsweise für Version 2.2.0 Folgendes ein:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Überprüfen der installierten Version [!DNL Data Migration Tool]

1. Ändern Sie Ihre [!DNL Data Migration Tool] directory: `<vendor>/magento/data-migration-tool`.

1. Öffnen [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) in einem Texteditor.

1. Die `version` -Eintrag in dieser Datei ist die Version der [!DNL Data Migration Tool].
