---
title: Einrichten des Produktionssystems
description: Erfahren Sie, wie Sie ein Produktionssystem für die Commerce-Anwendung einrichten.
exl-id: e678e97e-d9f2-4f24-bb6b-1994a2a1167c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Einrichten des Produktionssystems

Sie können ein Produktionssystem haben. Folgendes muss zutreffen:

- Der gesamte Commerce-Code befindet sich in der Quell-Code-Verwaltung im selben Repository wie die Entwicklungs- und Build-Systeme.
- Stellen Sie sicher, dass alle folgenden Elemente _im Quellcode-Steuerelement enthalten sind:_

   - `app/etc/config.php`
   - Ordner `generated` (und Unterverzeichnisse)
   - Verzeichnis `pub/media`
   - Ordner `pub/media/wysiwyg` (und Unterverzeichnisse)
   - Ordner `pub/static` (und Unterverzeichnisse)

- Commerce 2.2 oder höher muss installiert und für den [Produktionsmodus](../bootstrap/application-modes.md#production-mode) festgelegt werden
- Sie verfügt über Dateisystemeigentum und -berechtigungen, wie in [Voraussetzung für Ihre Entwicklungs-, Build- und Produktionssysteme](../deployment/prerequisites.md) beschrieben.

## Einrichten eines Produktionsgeräts

So richten Sie einen Produktionsrechner ein:

1. Nachdem Sie Commerce installiert oder aus der Quell-Code-Verwaltung abgerufen haben, melden Sie sich beim Produktionsserver als Eigentümer des Dateisystems an oder wechseln Sie zu diesem.
1. Erstellen Sie `~/.ssh/.composer/auth.json` , falls noch nicht geschehen.

   Erstellen Sie den Ordner:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Erstellen Sie `auth.json` in diesem Verzeichnis.

   `auth.json` muss Ihre [Authentifizierungsschlüssel](../../installation/prerequisites/authentication-keys.md) enthalten.

   Ein Beispiel:

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
1. Öffnen Sie `env.php` in einem Texteditor und ändern Sie die erforderlichen Werte (z. B. Informationen zur Datenbankverbindung).
1. Führen Sie den Befehl [`magento config:set`](../cli/set-configuration-values.md) oder [`magento config:set-sensitive`](../cli/set-configuration-values.md) aus, um die Werte aller systemspezifischen bzw. sensiblen Konfigurationswerte festzulegen.

   Im folgenden Abschnitt finden Sie ein Beispiel.

## Festlegen von Konfigurationswerten in Ihrem Produktionssystem

In diesem Abschnitt wird beschrieben, wie Sie mithilfe des Befehls `magento config:sensitive:set` sensible Werte in Ihrem Produktionssystem festlegen.

So legen Sie sensible Werte fest:

1. Suchen Sie einen Wert, der mithilfe der [sensiblen Wertreferenz](../reference/config-reference-sens.md) festgelegt werden soll.
1. Notieren Sie den Konfigurationspfad für die Einstellung.
1. Melden Sie sich beim Produktionssystem als Eigentümer des Dateisystems an oder wechseln Sie zu ihm.
1. Wechseln Sie zum Installationsordner von Commerce.
1. Geben Sie den folgenden Befehl ein:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Um beispielsweise den Wert des YouTube-API-Schlüssels auf `1234` festzulegen, geben Sie

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

   Beispielsweise befindet sich die YouTube-API-Schlüsseleinstellung unter &quot;**Stores**&quot;> &quot;Einstellungen&quot;> &quot;**Konfiguration**&quot;> &quot;**Katalog**&quot;> &quot;**Katalog**&quot;> &quot;**Produktvideo**&quot;.

   Die Einstellung wird im Admin angezeigt und kann nicht bearbeitet werden. Die folgende Abbildung zeigt ein Beispiel.

   ![Sensitive Einstellung in Admin](../../assets/configuration/sensitive-set.png)
