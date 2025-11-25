---
title: Installieren Sie  [!DNL Data Migration Tool]
description: Erfahren Sie, wie Sie  [!DNL Data Migration Tool]  installieren, um Daten zwischen Magento 1 und Magento 2 zu übertragen.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Installieren des [!DNL Data Migration Tool]

>[!INFO]
>
>Die Versionen von Magento und [!DNL Data Migration Tool] müssen übereinstimmen.


Stellen Sie sicher, dass Sie *dieselbe freigegebene Version* sowohl von Magento 2 als auch von [!DNL Data Migration Tool] verwenden. Beispielsweise müssen Sie für Magento Version 2.2.0 auch die [!DNL Data Migration Tool] Version 2.2.0 verwenden.

## Version überprüfen

Verwenden Sie eine der folgenden Methoden, um Ihre Version von Magento zu überprüfen:

- [Komponist](#composer-metapackage)
- [GitHub-Repository](#github-repository)

### Composer-Metapaket

Wenn Sie die Magento-Software mit einem Composer-Metapaket heruntergeladen haben, geben Sie den folgenden Befehl ein:

```bash
php <magento_root>/bin/magento --version
```

### GitHub-Repository

Wenn Sie das GitHub-Repository für Magento 2 geklont haben, geben Sie die folgenden Befehle ein:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Wenn Sie sich derzeit in der `develop` Verzweigung befinden, müssen Sie zu einer [freigegebenen Verzweigung“ wechseln](https://developer.adobe.com/commerce/contributor/guides/install/change-version) bevor Sie fortfahren.

Wenn Sie die Adobe Commerce-Software noch nicht installiert haben, [&#x200B; Sie sie jetzt &#x200B;](../../installation/prerequisites/commerce.md).
Wenn Sie das GitHub-Repository klonen, sollten Sie ein Release-Tag auschecken, wie in [(Mitwirkende) Klonen des GitHub-Repositorys &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository).

## Veröffentlichte Versionen von [!DNL Data Migration Tool] suchen

Auf der [Releases](https://github.com/magento/data-migration-tool/releases) des [!DNL Data Migration Tool] GitHub-Repositorys finden Sie verfügbare freigegebene Versionen.

## Installieren des [!DNL Data Migration Tool]

Sie können die [!DNL Data Migration Tool] unter folgendem Pfad installieren:

- [`repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Stellen Sie vor der Installation Folgendes sicher:

- Alle Aufgaben abgeschlossen, die im Abschnitt [Voraussetzungen](prerequisites.md) aufgeführt sind
- [Version überprüft](install.md#check-your-version) der Magento 2-Software

### Installieren von aus `repo.magento.com`

Um das [!DNL Data Migration Tool] zu installieren, müssen Sie `composer.json` im Magento-Stamminstallationsverzeichnis aktualisieren, um den Speicherort des [!DNL Data Migration Tool] anzugeben.

1. Melden Sie sich bei Ihrem Anwendungs-Server als oder wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie in das Stammverzeichnis der Anwendung.
1. Geben Sie die folgenden Befehle ein:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Dabei muss `<version>` mit der Version der Magento 2-Codebasis übereinstimmen.

   Geben Sie beispielsweise für Version 2.2.0 Folgendes ein:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Geben Sie nach Aufforderung Ihre [Authentifizierungsschlüssel](../../installation/prerequisites/authentication-keys.md) ein. Ihr öffentlicher Schlüssel ist Ihr Benutzername; Ihr privater Schlüssel ist Ihr Kennwort.

### Installieren über GitHub

Wenn Sie das GitHub-Repository geklont haben, führen Sie die folgenden Schritte aus, um das [!DNL Data Migration Tool] zu installieren.

1. Melden Sie sich bei Ihrem Anwendungs-Server als oder wechseln Sie zum [Dateisystembesitzer](../../installation/prerequisites/file-system/overview.md).
1. Wechseln Sie in das Stammverzeichnis der Anwendung.
1. Geben Sie die folgenden Befehle ein:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Dabei muss `<version>` mit der Version der Magento 2-Code-Basis übereinstimmen.

   Geben Sie beispielsweise für Version 2.2.0 Folgendes ein:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Überprüfen der Version installierter [!DNL Data Migration Tool]

1. Ändern Sie in Ihr [!DNL Data Migration Tool]: `<vendor>/magento/data-migration-tool`.

1. Öffnen Sie [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) in einem Texteditor.

1. Der `version` Eintrag in dieser Datei ist die Version der [!DNL Data Migration Tool].
