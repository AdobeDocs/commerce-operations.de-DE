---
title: Einrichten des Produktionssystems
description: Erfahren Sie, wie Sie ein Produktionssystem für die Commerce-Anwendung einrichten.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Einrichten des Produktionssystems

Sie können ein Produktionssystem haben. Folgendes muss zutreffen:

- Der gesamte Commerce-Code befindet sich in der Quell-Code-Verwaltung im selben Repository wie die Entwicklungs- und Build-Systeme.
- Stellen Sie sicher, dass alle folgenden Elemente _enthalten_ in der Quell-Code-Verwaltung:

   - `app/etc/config.php`
   - `generated` Verzeichnis (und Unterverzeichnisse)
   - `pub/media` directory
   - `pub/media/wysiwyg` Verzeichnis (und Unterverzeichnisse)
   - `pub/static` Verzeichnis (und Unterverzeichnisse)

- Commerce 2.2 oder höher muss installiert und für [Produktionsmodus](../bootstrap/application-modes.md#production-mode)
- Sie verfügt über Dateisystemeigentümer und -berechtigungen, wie hier beschrieben: [Voraussetzungen für Ihre Entwicklungs-, Build- und Produktionssysteme](../deployment/prerequisites.md).

## Einrichten eines Produktionsgeräts

So richten Sie einen Produktionsrechner ein:

1. Melden Sie sich nach der Installation von Commerce oder dem Abruf von der Quell-Code-Verwaltung beim Produktionsserver als Eigentümer des Dateisystems an oder wechseln Sie zu diesem.
1. Erstellen `~/.ssh/.composer/auth.json` wenn Sie dies noch nicht getan haben.

   Erstellen Sie den Ordner:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Erstellen `auth.json` in diesem Verzeichnis.

   `auth.json` muss enthalten: [Authentifizierungsschlüssel](../../installation/prerequisites/authentication-keys.md).

   Beispiel:

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Speichern Sie Ihre Änderungen in `auth.json`.
1. Kopieren `<Commerce root dir>/app/etc/env.php` von Ihrem Entwicklungssystem zu Ihrem Produktionssystem.
1. Öffnen `env.php` in einem Texteditor verwenden und die erforderlichen Werte ändern (z. B. Informationen zur Datenbankverbindung).
1. Führen Sie die [`magento config:set`](../cli/set-configuration-values.md) oder [`magento config:set-sensitive`](../cli/set-configuration-values.md) -Befehl, um die Werte aller systemspezifischen oder sensiblen Konfigurationswerte festzulegen.

   Im folgenden Abschnitt finden Sie ein Beispiel.

## Festlegen von Konfigurationswerten in Ihrem Produktionssystem

In diesem Abschnitt wird beschrieben, wie Sie mithilfe der `magento config:sensitive:set` Befehl.

So legen Sie sensible Werte fest:

1. Suchen Sie nach einem Wert, der mithilfe der [Sensible Value Reference](../reference/config-reference-sens.md).
1. Notieren Sie den Konfigurationspfad für die Einstellung.
1. Melden Sie sich beim Produktionssystem als Eigentümer des Dateisystems an oder wechseln Sie zu ihm.
1. Wechseln Sie zum Installationsverzeichnis für Commerce.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   So legen Sie beispielsweise den Wert des YouTube-API-Schlüssels auf `1234`, eingeben

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   Sie können auch einen oder mehrere Werte wie folgt interaktiv festlegen:

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Wenn Sie dazu aufgefordert werden, geben Sie für jede sensible Einstellung einen Wert ein oder drücken Sie die Eingabetaste , um einen Wert zu überspringen und zur nächsten zu wechseln.

1. Um zu überprüfen, ob der Wert festgelegt wurde, melden Sie sich beim Administrator an.
1. Suchen Sie die Einstellung in der Admin-Konsole.

   Beispielsweise befindet sich die YouTube-API-Schlüsseleinstellung unter **Stores** > Einstellungen > **Konfiguration** > **Katalog** > **Katalog** > **Produktvideo**.

   Die Einstellung wird im Admin angezeigt und kann nicht bearbeitet werden. Die folgende Abbildung zeigt ein Beispiel.

   ![Sensitive Einstellung in der Admin-Konsole](../../assets/configuration/sensitive-set.png)
