---
title: Beispiel mit CLI-Befehlen
description: Sehen Sie sich ein Beispiel für das Festlegen von freigegebenen, systemspezifischen und sensiblen Werten in Ihrem Entwicklungssystem mithilfe der Befehlszeile an.
exl-id: d0058e9f-a5a9-48a6-9c66-c61515666335
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Beispiel mit CLI-Befehlen

Dieses Beispiel zeigt, wie Sie in Ihrem Entwicklungssystem gemeinsame, systemspezifische und vertrauliche Werte festlegen und diese Werte dann in Ihrem Produktionssystem bereitstellen.
Dies geschieht mithilfe einer Kombination aus freigegebenen Konfigurationen, der `config.php`-Datei und dem Commerce-CLI-Befehl.

In diesem Beispiel werden die folgenden Konfigurationseinstellungen verwendet:

- **Umsatzsteuernummer** und **Store-Name** für die freigegebenen Konfigurationseinstellungen.

  Diese finden Sie unter **Stores** > Einstellungen > **Konfiguration** > Allgemein **Allgemein**.

- **E-Mails senden an** für den sensiblen Konfigurationswert.

  Diese finden Sie unter **Stores** > Einstellungen > **Konfiguration** > Allgemein **Kontakte**.

- **Standard-E-Mail** Domain) für den systemspezifischen Konfigurationswert.

  Dies finden Sie unter **Stores** > Einstellungen > **Konfiguration** > Kunden > **Kundenkonfiguration** > **Optionen für neues Konto erstellen**.

Sie können das in diesem Beispiel beschriebene Verfahren verwenden, um alle Einstellungen in den folgenden Verweisen zu konfigurieren:

- [Referenz zu sensiblen und systemspezifischen Konfigurationspfaden](../reference/config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](../reference/config-reference-payment.md)
- [Referenz zu anderen Konfigurationspfaden](../reference/config-reference-general.md)
- [Konfigurationspfade für Commerce Enterprise B2B-Erweiterungen - Referenz](../reference/config-reference-b2b.md)

## Bevor Sie beginnen

Bevor Sie beginnen, richten Sie Dateisystemberechtigungen und -eigentümerschaft ein, wie in [Voraussetzung für Entwicklungs-, Build- und Produktionssysteme](../deployment/prerequisites.md) beschrieben.

## Annahmen

Dieses Thema enthält ein Beispiel für das Ändern der Konfiguration des Produktionssystems. Sie können bei Bedarf verschiedene Konfigurationsoptionen auswählen.

Für die Zwecke dieses Beispiels gehen wir von Folgendem aus:

- Sie verwenden die Git-Quell-Code-Verwaltung
- Das Entwicklungssystem ist in einem Git-Remote-Repository namens `mconfig` verfügbar
- Ihre Git-Arbeitsverzweigung heißt `m2.2_deploy`

## Schritt 1: Festlegen der Konfiguration im Entwicklungssystem

So legen Sie das Standardgebietsschema und die Gewichtungseinheiten in Ihrem Entwicklungssystem fest:

1. Melden Sie sich beim Administrator an.
1. Klicken Sie auf **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.
1. Wenn mehr als eine Website verfügbar ist, verwenden Sie die Liste **Store-Ansicht** in der oberen linken Ecke, um zu einer anderen Website zu wechseln, wie in der folgenden Abbildung dargestellt.

   ![Websites wechseln](../../assets/configuration/split-deploy-switch-website.png)

1. Erweitern Sie im rechten Bereich **Informationen speichern**.
1. Deaktivieren Sie bei Bedarf das **Standard verwenden** Kontrollkästchen neben den Feldern **MwSt.-Nummer** und **Store-Name**.
1. Geben Sie eine Zahl in das Feld ein (z. B. `12345`).
1. Geben **im Feld** Store-Name“ einen Wert ein (wie `My Store`).
1. Klicken Sie **Konfiguration speichern**.
1. Klicken Sie in der linken Navigation unter Allgemein auf **Kontakte**.
1. Erweitern Sie im rechten Bereich **E-Mail-Optionen**.
1. Deaktivieren Sie bei Bedarf das **Standard verwenden** neben dem Feld **E-Mails senden an**.
1. Geben Sie eine E-Mail-Adresse ein.
1. Klicken Sie **Konfiguration speichern**.
1. Wählen Sie in **Liste &quot;**&quot; die **Standardkonfiguration** aus, wie in der folgenden Abbildung dargestellt.

   ![Wechseln Sie zur Standardkonfiguration](../../assets/configuration/split-deploy-default-config.png)

1. Klicken Sie im linken Bereich auf Kunden > **Kundenkonfiguration**.
1. Erweitern Sie im rechten Bereich **Neue Kontooptionen erstellen**.
1. Deaktivieren Sie bei Bedarf das **Systemwert verwenden** neben dem Feld **Standard-E-Mail-Domain**.
1. Geben Sie einen Domain-Namen in das Feld ein.
1. Klicken Sie **Konfiguration speichern**.
1. Leeren Sie den Cache, wenn Sie dazu aufgefordert werden.

## Schritt 2: Aktualisieren der Konfiguration

Nachdem Sie nun die Konfiguration in Admin geändert haben, schreiben Sie die freigegebene Konfiguration in eine Datei , wie in den folgenden Schritten beschrieben:

{{$include /help/_includes/config-save-config.md}}

Auch wenn `app/etc/env.php` (die systemspezifische Konfiguration) aktualisiert wurde, checken Sie es nicht in die Versionsverwaltung ein.
Die Konfigurationseinstellungen werden später in diesem Verfahren auf Ihrem Produktionssystem erstellt.

## Schritt 3: Build-System aktualisieren und Dateien generieren

Nachdem Sie Ihre Änderungen an der freigegebenen Konfiguration in die Versionsverwaltung übertragen haben, können Sie diese Änderungen in Ihr Buildsystem übertragen, den Code kompilieren und statische Dateien generieren.

{{$include /help/_includes/config-update-build-system.md}}

## Schritt 4: Aktualisieren des Produktionssystems

Der letzte Schritt im Prozess ist die Aktualisierung Ihres Produktionssystems. Sie müssen es in zwei Teilen tun:

- Aktualisieren der sensiblen und systemspezifischen Einstellungen
- Aktualisieren der freigegebenen Einstellungen

### Aktualisieren der sensiblen und systemspezifischen Einstellungen

Um die sensiblen und systemspezifischen Einstellungen mithilfe von Umgebungsvariablen festzulegen, müssen Sie Folgendes wissen:

- Umfang für jede Einstellung

  Wenn Sie die Anweisungen in Schritt 1 befolgt haben, lautet der Bereich für **E-Mails senden an** Website und der Bereich für **Standard-E-Mail-Domain** ist global (d. h. der Standardkonfigurationsbereich).

  Sie benötigen den Website-Code, um den Konfigurationswert **E-Mails senden an“**.

  Weitere Informationen dazu, wie Sie diesen Wert finden, finden Sie unter [Verwenden von Umgebungsvariablen zum Überschreiben der Konfigurationseinstellungen](../reference/override-config-settings.md#environment-variables).

- Konfigurationspfade für die in diesem Beispiel verwendeten Einstellungen:

  | Name der Einstellung | Konfigurationspfad |
  | -------------------- | -------------------------------------- |
  | E-Mails senden an | `contact/email/recipient_email` |
  | Standard-E-Mail-Domain | `customer/create_account/email_domain` |

  Informationen zu allen sensiblen und systemspezifischen Konfigurationspfaden finden Sie unter: [Sensitive und systemspezifische Konfigurationspfade - Referenz](../reference/config-reference-sens.md).

### Festlegen der Variablen mithilfe von CLI-Befehlen

Verwenden Sie die folgenden CLI-Befehle, um systemspezifische und vertrauliche Konfigurationseinstellungen festzulegen:

- `magento config:set` für systemspezifische Einstellungen
- `magento config:sensitive:set` für vertrauliche Einstellungen

Verwenden Sie den folgenden Befehl, um die **Einstellung „Standard** E-Mail-Domain“ festzulegen, die sich im Standardbereich befindet:

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

Sie müssen den Bereich nicht im Befehl verwenden, da dies der Standardbereich ist.

Um Werte für **E-Mails senden an** festzulegen, müssen Sie jedoch den Bereichstyp (`website`) und den Bereichscode kennen, der wahrscheinlich auf jeder Site unterschiedlich ist.

Beispiel:

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### Aktualisieren der freigegebenen Einstellungen

In diesem Abschnitt wird beschrieben, wie Sie alle an Ihren Entwicklungs- und Build-Systemen vorgenommenen Änderungen in eine Produktionsumgebung übertragen, wodurch die freigegebenen Konfigurationseinstellungen (Store-Name und MwSt.-Nummer) aktualisiert werden.

{{$include /help/_includes/config-update-prod-system.md}}

### Überprüfen der Konfigurationseinstellungen in der Admin Console

So überprüfen Sie die Konfigurationseinstellungen:

1. Melden Sie sich beim Administrator Ihres Produktionssystems an.
1. Klicken Sie auf **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.
1. Verwenden Sie die **Store-Ansicht** in der oberen linken Ecke, um zu einer anderen Website zu wechseln.

   Die freigegebenen Konfigurationsoptionen, die Sie im Entwicklungssystem festlegen, werden ähnlich der folgenden angezeigt.

   ![Überprüfen Sie die Einstellungen im Produktionssystem](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >Das **Store-Name**-Feld kann im Website-Bereich bearbeitet werden, wenn Sie jedoch zum Standard-Konfigurationsbereich wechseln, ist es nicht bearbeitbar. Dies ist das Ergebnis der Einstellung der Optionen im Entwicklungssystem. Der Wert **MwSt.-Nummer** kann im Website-Umfang nicht bearbeitet werden.

1. Wechseln Sie, falls noch nicht geschehen, zum Bereich „Standardkonfiguration“.
1. Klicken Sie in der linken Navigation unter Allgemein auf **Kontakte**.

   Das Feld **E-Mails senden an** kann nicht bearbeitet werden, wie in der folgenden Abbildung dargestellt. Dies ist ein sensibler Bereich.

   ![Überprüfen Sie die Einstellungen im Produktionssystem](../../assets/configuration/split-deploy-verify-contacts.png)

1. Klicken Sie im linken Bereich auf Kunden > **Kundenkonfiguration**.
1. Erweitern Sie im rechten Bereich **Neue Kontooptionen erstellen**.

   Der Wert des Felds **Standard-E-Mail** Domain) wird wie folgt angezeigt. Dies ist eine systemspezifische Einstellung.

   ![Überprüfen Sie die Einstellungen im Produktionssystem](../../assets/configuration/split-default-domain.png)
