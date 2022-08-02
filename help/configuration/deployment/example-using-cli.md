---
title: Beispiel mit CLI-Befehlen
description: Sehen Sie sich ein Beispiel dafür an, wie Sie mithilfe der Befehlszeile in Ihrem Entwicklungssystem gemeinsame, systemspezifische und sensible Werte festlegen.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---


# Beispiel mit CLI-Befehlen

In diesem Beispiel wird gezeigt, wie Sie in Ihrem Entwicklungssystem gemeinsame, systemspezifische und sensible Werte festlegen und diese Werte dann in Ihrem Produktionssystem bereitstellen.
Dies geschieht mithilfe einer Kombination aus freigegebenen Konfigurationen, der `config.php` und Commerce-CLI-Befehl.

In diesem Beispiel werden die folgenden Konfigurationseinstellungen verwendet:

- **MwSt.-Nummer** und **Speichername** für die freigegebenen Konfigurationseinstellungen.

   Diese finden Sie unter **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.

- **E-Mails an senden** für den sensiblen Konfigurationswert.

   Dies finden Sie unter **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Kontakte**.

- **Standard-E-Mail-Domain** für den systemspezifischen Konfigurationswert.

   Dies finden Sie unter **Stores** > Einstellungen > **Konfiguration** > Kunden > **Kundenkonfiguration** > **Neue Kontooptionen erstellen**.

Sie können das gleiche Verfahren wie in diesem Beispiel verwenden, um Einstellungen in den folgenden Referenzen zu konfigurieren:

- [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](../reference/config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](../reference/config-reference-payment.md)
- [Andere Konfigurationspfade](../reference/config-reference-general.md)
- [Referenz zu den Konfigurationspfaden für Commerce Enterprise B2B-Erweiterungen](../reference/config-reference-b2b.md)

## Bevor Sie beginnen

Richten Sie zunächst die Dateisystemberechtigungen und den Eigentümer ein, wie hier beschrieben: [Voraussetzungen für Entwicklungs-, Build- und Produktionssysteme](../deployment/prerequisites.md).

## Annahmen

Dieses Thema enthält ein Beispiel für die Änderung der Konfiguration des Produktionssystems. Sie können bei Bedarf verschiedene Konfigurationsoptionen auswählen.

Für die Zwecke dieses Beispiels gehen wir von Folgendem aus:

- Verwenden Sie die Git-Quellsteuerung
- Das Entwicklungssystem ist in einem Git-Remote-Repository mit dem Namen `mconfig`
- Ihre Git-Arbeitsverzweigung heißt `m2.2_deploy`

## Schritt 1: Konfiguration im Entwicklungssystem festlegen

So legen Sie die standardmäßige Gebietsschema- und Gewichtseinheiten in Ihrem Entwicklungssystem fest:

1. Melden Sie sich beim Administrator an.
1. Klicken **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.
1. Wenn Sie mehr als eine Website zur Verfügung haben, verwenden Sie die **Store-Ansicht** in der oberen linken Ecke, um zu einer anderen Website zu wechseln, wie in der folgenden Abbildung dargestellt.

   ![Wechseln von Websites](../../assets/configuration/split-deploy-switch-website.png)

1. Erweitern Sie im rechten Bereich **Store-Informationen**.
1. Falls erforderlich, löschen Sie die **Use Default** Kontrollkästchen neben dem **MwSt.-Nummer** und **Speichername** -Felder.
1. Geben Sie eine Zahl in das Feld ein (z. B. `12345`).
1. Im **Speichername** ein Wert eingeben (wie `My Store`).
1. Klicken **Konfiguration speichern**.
1. Klicken Sie im linken Navigationsbereich unter &quot;General&quot;auf **Kontakte**.
1. Erweitern Sie im rechten Bereich **E-Mail-Optionen**.
1. Falls erforderlich, löschen Sie die **Use Default** Kontrollkästchen neben dem **E-Mails an senden** -Feld.
1. Geben Sie eine E-Mail-Adresse in das Feld ein.
1. Klicken **Konfiguration speichern**.
1. Verwenden Sie die **Store-Ansicht** Liste zur Auswahl der **Standardkonfiguration** wie in der folgenden Abbildung dargestellt.

   ![Zur Standardkonfiguration wechseln](../../assets/configuration/split-deploy-default-config.png)

1. Klicken Sie im linken Bereich auf Customers > **Kundenkonfiguration**.
1. Erweitern Sie im rechten Bereich **Neue Kontooptionen erstellen**.
1. Falls erforderlich, löschen Sie die **Systemwert verwenden** Kontrollkästchen neben dem **Standard-E-Mail-Domain** -Feld.
1. Geben Sie einen Domänennamen in das Feld ein.
1. Klicken **Konfiguration speichern**.
1. Wenn Sie dazu aufgefordert werden, leeren Sie den Cache.

## Schritt 2: Konfiguration aktualisieren

Nachdem Sie die Konfiguration in Admin geändert haben, schreiben Sie die freigegebene Konfiguration wie folgt in eine Datei:

{{$include /help/_includes/config-save-config.md}}

Auch `app/etc/env.php` (die systemspezifische Konfiguration) aktualisiert wurde, checken Sie sie nicht in die Quell-Code-Verwaltung ein.
Sie werden später in diesem Verfahren dieselben Konfigurationseinstellungen für Ihr Produktionssystem erstellen.

## Schritt 3: Build-System aktualisieren und Dateien generieren

Nachdem Sie Ihre Änderungen an der freigegebenen Konfiguration an die Quell-Code-Verwaltung übertragen haben, können Sie diese Änderungen in Ihr Build-System übernehmen, den Code kompilieren und statische Dateien generieren.

{{$include /help/_includes/config-update-build-system.md}}

## Schritt 4: Produktionssystem aktualisieren

Der letzte Schritt im Prozess besteht darin, Ihr Produktionssystem zu aktualisieren. Sie müssen dies in zwei Teilen tun:

- Aktualisieren der sensiblen und systemspezifischen Einstellungen
- Aktualisieren der freigegebenen Einstellungen

### Aktualisieren der sensiblen und systemspezifischen Einstellungen

Um die sensiblen und systemspezifischen Einstellungen mithilfe von Umgebungsvariablen festzulegen, müssen Sie Folgendes wissen:

- Umfang der einzelnen Einstellungen

   Wenn Sie die Anweisungen in Schritt 1 befolgt haben, wird der Umfang für **E-Mails an senden** ist Website und der Umfang für **Standard-E-Mail-Domain** ist global (d. h. der Standardkonfig-Umfang).

   Sie benötigen den Website-Code, um die **E-Mails an senden** Konfigurationswert.

   Weitere Informationen zum Auffinden dieses Werts finden Sie unter: [Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen verwenden](../reference/override-config-settings.md#environment-variables).

- Konfigurationspfade für die in diesem Beispiel verwendeten Einstellungen:

   | Einstellungsname | Konfigurationspfad |
   | -------------------- | -------------------------------------- |
   | E-Mails an senden | `contact/email/recipient_email` |
   | Standard-E-Mail-Domain | `customer/create_account/email_domain` |

   Alle sensiblen und systemspezifischen Konfigurationspfade finden Sie unter: [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](../reference/config-reference-sens.md).

### Variablen mithilfe von CLI-Befehlen festlegen

Verwenden Sie die folgenden CLI-Befehle, um systemspezifische und vertrauliche Konfigurationseinstellungen festzulegen:

- `magento config:set` für systemspezifische Einstellungen
- `magento config:sensitive:set` für vertrauliche Einstellungen

So legen Sie die systemspezifische Einstellung fest **Standard-E-Mail-Domain** verwenden, die sich im Standardbereich befindet, den folgenden Befehl:

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

Sie müssen den Bereich im -Befehl nicht verwenden, da es sich um den Standardbereich handelt.

So legen Sie Werte für fest **E-Mails an senden** müssen Sie jedoch den Perimeter (`website`) und dem Perimeter-Code, der sich wahrscheinlich auf jeder Site unterscheidet.

Beispiel:

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### Aktualisieren der freigegebenen Einstellungen

In diesem Abschnitt wird beschrieben, wie Sie alle Änderungen, die Sie an Ihren Entwicklungs- und Build-Systemen vorgenommen haben, in eine Produktionsumgebung ziehen, wodurch die freigegebenen Konfigurationseinstellungen (Store Name und VAT Number) aktualisiert werden.

{{$include /help/_includes/config-update-prod-system.md}}

### Konfigurationseinstellungen in der Admin-Konsole überprüfen

Überprüfen der Konfigurationseinstellungen:

1. Melden Sie sich beim Administrator Ihres Produktionssystems an.
1. Klicken **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.
1. Verwenden Sie die **Store-Ansicht** Liste oben links, um zu einer anderen Website zu wechseln.

   Die freigegebenen Konfigurationsoptionen, die Sie im Entwicklungssystem festlegen, werden ähnlich wie die folgenden angezeigt.

   ![Einstellungen im Produktionssystem überprüfen](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >Die **Speichername** -Feld im Website-Bereich bearbeitbar ist, aber wenn Sie zum Bereich Standardkonfiguration wechseln, kann er nicht bearbeitet werden. Dies ist das Ergebnis der Festlegung der Optionen im Entwicklungssystem. Der Wert von **MwSt.-Nummer** im Website-Umfang nicht bearbeitbar ist.

1. Wechseln Sie, falls noch nicht geschehen, zum Bereich Standardkonfiguration .
1. Klicken Sie im linken Navigationsbereich unter &quot;General&quot;auf **Kontakte**.

   Die **E-Mails an senden** -Feld kann nicht bearbeitet werden, wie in der folgenden Abbildung dargestellt. Dies ist eine sensible Einstellung.

   ![Einstellungen im Produktionssystem überprüfen](../../assets/configuration/split-deploy-verify-contacts.png)

1. Klicken Sie im linken Bereich auf Customers > **Kundenkonfiguration**.
1. Erweitern Sie im rechten Bereich **Neue Kontooptionen erstellen**.

   Der Wert der **Standard-E-Mail-Domain** wird wie folgt angezeigt. Dies ist eine systemspezifische Einstellung.

   ![Einstellungen im Produktionssystem überprüfen](../../assets/configuration/split-default-domain.png)
