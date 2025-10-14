---
title: Einrichtung des Produktionssystems
description: Erfahren Sie, wie Sie ein Produktionssystem für das Commerce-Programm einrichten.
exl-id: e678e97e-d9f2-4f24-bb6b-1994a2a1167c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Einrichtung des Produktionssystems

Sie können ein Produktionssystem haben. Folgendes muss alle zutreffen:

- Der gesamte Commerce-Code befindet sich in der Quell-Code-Verwaltung im selben Repository wie die Entwicklungs- und Build-Systeme
- Stellen Sie sicher, dass Folgendes in _Quell_ Code-Verwaltung enthalten ist:

   - `app/etc/config.php`
   - `generated` (und Unterverzeichnisse)
   - `pub/media`
   - `pub/media/wysiwyg` (und Unterverzeichnisse)
   - `pub/static` (und Unterverzeichnisse)

- Commerce 2.2 oder höher muss installiert und für den [Produktionsmodus“ &#x200B;](../bootstrap/application-modes.md#production-mode)
- Für sie sind der Besitz und die Berechtigungen des Dateisystems festgelegt, wie unter [Voraussetzung für Ihre Entwicklungs-, Build- und Produktionssysteme](../deployment/prerequisites.md) erläutert.

## Einrichten einer Produktionsmaschine

So richten Sie eine Produktionsmaschine ein:

1. Melden Sie sich nach der Installation von Commerce oder dem Abrufen aus der Quell-Code-Verwaltung beim Produktionsserver als Eigentümer des Dateisystems an oder wechseln Sie zu diesem.
1. Erstellen Sie `~/.ssh/.composer/auth.json`, falls noch nicht geschehen.

   Erstellen Sie das Verzeichnis :

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Erstellen Sie `auth.json` in diesem Verzeichnis.

   `auth.json` müssen Ihre [Authentifizierungsschlüssel“ &#x200B;](../../installation/prerequisites/authentication-keys.md).

   Es folgt ein Beispiel:

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
1. Kopieren Sie `<Commerce root dir>/app/etc/env.php` aus Ihrem Entwicklungssystem in Ihr Produktionssystem.
1. Öffnen Sie `env.php` in einem Texteditor und ändern Sie die erforderlichen Werte (z. B. Datenbankverbindungsinformationen).
1. Führen Sie den Befehl [`magento config:set`](../cli/set-configuration-values.md) oder [`magento config:set-sensitive`](../cli/set-configuration-values.md) aus, um die Werte der systemspezifischen bzw. sensiblen Konfigurationswerte festzulegen.

   Der folgende Abschnitt zeigt ein Beispiel.

## Festlegen von Konfigurationswerten in Ihrem Produktionssystem

In diesem Abschnitt wird beschrieben, wie Sie mithilfe des `magento config:sensitive:set`-Befehls sensible Werte auf Ihrem Produktionssystem festlegen.

So legen Sie vertrauliche Werte fest:

1. Suchen Sie einen Wert, der mithilfe der [Referenz für vertrauliche Werte“ festgelegt &#x200B;](../reference/config-reference-sens.md) soll.
1. Notieren Sie den Konfigurationspfad für die Einstellung .
1. Melden Sie sich beim Produktionssystem als Eigentümer an oder wechseln Sie zum Dateisystembesitzer.
1. Wechseln Sie in das Commerce-Installationsverzeichnis.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Um beispielsweise den Wert des YouTube-API-Schlüssels auf `1234` festzulegen, geben Sie Folgendes ein

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   Sie können einen oder mehrere Werte auch interaktiv wie folgt festlegen:

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Wenn Sie dazu aufgefordert werden, geben Sie für jede vertrauliche Einstellung einen Wert ein oder drücken Sie die Eingabetaste , um einen Wert zu überspringen und zur nächsten Einstellung zu wechseln.

1. Um sicherzustellen, dass der Wert festgelegt wurde, melden Sie sich beim Administrator an.
1. Suchen Sie die Einstellung im Admin-Bereich.

   Die Einstellung für den YouTube-API-Schlüssel befindet sich beispielsweise unter **Stores** > Settings > **Configuration** > **Catalog** > **Catalog** > **Product Video**.

   Die Einstellung wird in Admin angezeigt und kann nicht bearbeitet werden. Die folgende Abbildung zeigt ein Beispiel.

   ![Sensitive-Einstellung in der Admin-](../../assets/configuration/sensitive-set.png)
