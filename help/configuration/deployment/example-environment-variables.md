---
title: Beispiel mit Umgebungsvariablen
description: Sehen Sie sich ein Beispiel dafür an, wie Sie mithilfe von Umgebungsvariablen gemeinsame, systemspezifische und sensible Werte in Ihrem Entwicklungssystem festlegen.
exl-id: 98438674-e7f8-4143-9a76-3cc8bf0a73dc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 0%

---

# Beispiel mit Umgebungsvariablen

In diesem Beispiel wird gezeigt, wie Sie in Ihrem Entwicklungssystem gemeinsame, systemspezifische und vertrauliche Werte festlegen und dann alle Werte in Ihrem Produktionssystem mithilfe einer Kombination der freigegebenen Konfiguration festlegen. `config.php`und PHP-Umgebungsvariablen.

Diese Konfigurationseinstellungen können von Entwicklungs- und Produktionssystemen gemeinsam verwendet werden:

MwSt.-Nummer und Store-Name von **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**

Diese Konfigurationseinstellungen sind entweder systemspezifisch oder vertraulich, wie angegeben:

- E-Mails an senden (sensibel) von **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Kontakte**
- Standard-E-Mail-Domäne (systemspezifisch) von **Stores** > Einstellungen > **Konfiguration** > Kunden > **Kundenkonfiguration** > **Neue Kontooptionen erstellen**

Sie können dasselbe Verfahren verwenden, um alle Einstellungen in den folgenden Referenzen zu konfigurieren:

- [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](../reference/config-reference-sens.md)
- [Referenz zu Zahlungskonfigurationspfaden](../reference/config-reference-payment.md)
- [Referenz zu allgemeinen Konfigurationspfaden](../reference/config-reference-general.md)
- [Referenz zu den Konfigurationspfaden für Commerce Enterprise B2B-Erweiterungen](../reference/config-reference-b2b.md)

## Bevor Sie beginnen

Richten Sie zunächst die Dateisystemberechtigungen und den Eigentümer ein, wie hier beschrieben: [Voraussetzungen für Entwicklungs-, Build- und Produktionssysteme](../deployment/prerequisites.md).

## Annahmen

Dieses Thema enthält ein Beispiel für die Änderung der Konfiguration des Produktionssystems. Sie können bei Bedarf verschiedene Konfigurationsoptionen auswählen.

Für die Zwecke dieses Beispiels gehen wir von Folgendem aus:

- Verwenden Sie die Git-Quellsteuerung.
- Das Entwicklungssystem ist in einem Git-Remote-Repository mit dem Namen `mconfig`
- Ihre Git-Arbeitsverzweigung heißt `m2.2_deploy`

## Schritt 1: Konfiguration im Entwicklungssystem festlegen

So legen Sie die standardmäßige Gebietsschema- und Gewichtseinheiten in Ihrem Entwicklungssystem fest:

1. Melden Sie sich beim Administrator an.
1. Klicks **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.
1. Wenn mehrere Websites verfügbar sind, verwenden Sie die **Store-Ansicht** in der oberen linken Ecke, um zu einer anderen Website zu wechseln, wie in der folgenden Abbildung dargestellt.

   ![Wechseln von Websites](../../assets/configuration/split-deploy-switch-website.png)

1. Erweitern Sie im rechten Bereich **Store-Informationen**.
1. Falls erforderlich, löschen Sie die **Use Default** Kontrollkästchen neben dem **MwSt. Nummer** -Feld.
1. Geben Sie eine Zahl in das Feld ein (beispielsweise `12345`).
1. Im **Speichername** ein Wert eingeben (wie `My Store`).
1. Klicks **Konfiguration speichern**.
1. Verwenden Sie die **Store-Ansicht** Liste zur Auswahl der **Standardkonfiguration** wie in der folgenden Abbildung dargestellt.

   ![Zur Standardkonfiguration wechseln](../../assets/configuration/split-deploy-default-config.png)

1. Klicken Sie im linken Navigationsbereich unter &quot;General&quot;auf **Kontakte**.
1. Löschen Sie die **Use Default** Kontrollkästchen neben dem **E-Mails an senden** -Feld.
1. Geben Sie eine E-Mail-Adresse in das Feld ein.
1. Klicks **Konfiguration speichern**.
1. Klicken Sie im linken Bereich auf Customers > **Kundenkonfiguration**.
1. Erweitern Sie im rechten Bereich **Neue Kontooptionen erstellen**.
1. Löschen Sie die **Systemwert verwenden** Kontrollkästchen neben dem **Standard-E-Mail-Domain** -Feld.
1. Geben Sie einen Domänennamen in das Feld ein.
1. Klicks **Konfiguration speichern**.
1. Wenn Sie dazu aufgefordert werden, leeren Sie den Cache.

## Schritt 2: Konfiguration aktualisieren

Nachdem Sie die Konfiguration in Admin geändert haben, schreiben Sie die freigegebene Konfiguration in eine Datei, wie in diesem Abschnitt beschrieben.

{{$include /help/_includes/config-save-config.md}}

Beachten Sie Folgendes: `app/etc/env.php` (die systemspezifische Konfiguration) aktualisiert wurde, checken Sie sie nicht in die Quell-Code-Verwaltung ein. Sie werden später in diesem Verfahren dieselben Konfigurationseinstellungen für Ihr Produktionssystem erstellen.

## Schritt 3: Aktualisieren Sie Ihr Build-System und generieren Sie Dateien.

Nachdem Sie Ihre Änderungen an der freigegebenen Konfiguration an die Quell-Code-Verwaltung übertragen haben, können Sie diese Änderungen in Ihrem Build-System abrufen, Code kompilieren und statische Dateien generieren. Der letzte Schritt besteht darin, diese Änderungen in Ihr Produktionssystem zu übernehmen.

{{$include /help/_includes/config-update-build-system.md}}

## Schritt 4: Produktionssystem aktualisieren

Der letzte Schritt im Prozess besteht darin, Ihr Produktionssystem zu aktualisieren. Sie müssen dies in zwei Teilen tun:

- Aktualisieren der sensiblen und systemspezifischen Einstellungen
- Aktualisieren der freigegebenen Einstellungen

### Aktualisieren der sensiblen und systemspezifischen Einstellungen

Um die sensiblen und systemspezifischen Einstellungen mithilfe von Umgebungsvariablen festzulegen, müssen Sie Folgendes wissen:

- Umfang der einzelnen Einstellungen

  Wenn Sie die Anweisungen in Schritt 1 befolgt haben, ist der Bereich für das Senden von E-Mails an global (d. h. der Bereich Standardkonfiguration ) und der Bereich für die Standard-E-Mail-Domäne ist website.

  Sie müssen den Code der Website kennen, um den Konfigurationswert Standard-E-Mail-Domäne festzulegen. Siehe [Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen verwenden](../reference/override-config-settings.md#environment-variables) für weitere Informationen zum Auffinden.

- Konfigurationspfad für jede Einstellung

  Die in diesem Beispiel verwendeten Konfigurationspfade:

  | Einstellungsname | Konfigurationspfad |
  |--------------|--------------|
  | E-Mails an senden | `contact/email/recipient_email` |
  | Standard-E-Mail-Domain | `customer/create_account/email_domain` |

  Alle sensiblen und systemspezifischen Konfigurationspfade finden Sie in [Referenz zu vertraulichen und systemspezifischen Konfigurationspfaden](../reference/config-reference-sens.md).

#### Konvertieren von Konfigurationspfaden in Variablennamen

Wie in [Umgebungsvariablen zum Überschreiben von Konfigurationseinstellungen verwenden](../reference/override-config-settings.md#environment-variables)festgelegt ist, lautet das Format der Variablen:

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

Der Wert von `<SCOPE>` is `CONFIG__DEFAULT__` für globalen Umfang oder `CONFIG__WEBSITES__<WEBSITE CODE>` für den Website-Bereich.

So finden Sie den Wert von `<SYSTEM__VARIABLE__NAME>`, ersetzen Sie jeden `/` im Konfigurationspfad mit zwei Unterstrichen.

Die Variablennamen folgen:

| Name | Konfigurationspfad | Variablenname |
|--------------|--------------|--------------|
| E-Mails an senden | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| Standard-E-Mail-Domain | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>Die vorherige Tabelle enthält einen Beispiel-Website-Code, `BASE`, für die Konfigurationseinstellung Standard-E-Mail-Domäne . Ersetzen `BASE` mit dem entsprechenden Website-Code für Ihren Store.

#### Variablen mithilfe von Umgebungsvariablen festlegen

Sie können die Variablenwerte im `index.php` unter Verwendung des folgenden Formats:

```php
$_ENV['VARIABLE'] = 'value';
```

**So legen Sie Variablenwerte fest**:

1. Melden Sie sich bei Ihrem Produktionssystem als Eigentümer des Dateisystems an oder wechseln Sie zu ihm.
1. Öffnen `<Commerce root dir>/pub/index.php` in einem Texteditor.
1. überall in `index.php`, legen Sie Werte für die Variablen ähnlich den folgenden fest:

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. Speichern Sie Ihre Änderungen in `pub/index.php` und beenden Sie den Texteditor.
1. Fahren Sie mit dem nächsten Abschnitt fort.

### Aktualisieren der freigegebenen Einstellungen

In diesem Abschnitt wird beschrieben, wie Sie alle Änderungen abrufen, die Sie an Ihren Entwicklungs- und Build-Systemen vorgenommen haben. Dadurch werden die freigegebenen Konfigurationseinstellungen (Speichername und MwSt.-Nummer) aktualisiert.

{{$include /help/_includes/config-update-prod-system.md}}

### Konfigurationseinstellungen in der Admin-Konsole überprüfen

In diesem Abschnitt wird beschrieben, wie Sie die Konfigurationseinstellungen in Ihrem Produktionssystem-Admin überprüfen können.

**Überprüfen der Konfigurationseinstellungen**:

1. Melden Sie sich beim Administrator Ihres Produktionssystems an.
1. Klicks **Stores** > Einstellungen > **Konfiguration** > Allgemein > **Allgemein**.
1. Verwenden Sie die **Store-Ansicht** Liste oben links, um zu einer anderen Website zu wechseln.

   Die freigegebenen Konfigurationsoptionen, die Sie im Entwicklungssystem festlegen, werden in etwa wie folgt angezeigt:

   ![Einstellungen im Produktionssystem überprüfen](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >Die **Speichername** -Feld im Website-Bereich bearbeitbar ist, aber wenn Sie zum Bereich &quot;Standardkonfiguration&quot;wechseln, kann er nicht bearbeitet werden. Dies ist das Ergebnis der Festlegung der Optionen im Entwicklungssystem. Der Wert von **MwSt. Nummer** im Website-Umfang nicht bearbeitbar ist.

1. Wechseln Sie, falls noch nicht geschehen, zum Bereich Standardkonfiguration .
1. Klicken Sie im linken Navigationsbereich unter &quot;General&quot;auf **Kontakte**.

   Die **E-Mails an senden** -Feld kann nicht bearbeitet werden, wie in der folgenden Abbildung dargestellt. Dies ist eine sensible Einstellung.

   ![Einstellungen im Produktionssystem überprüfen](../../assets/configuration/split-deploy-verify-contacts.png)

1. Klicken Sie im linken Bereich auf Customers > **Kundenkonfiguration**.
1. Erweitern Sie im rechten Bereich **Neue Kontooptionen erstellen**.

   Der Wert der **Standard-E-Mail-Domain** wird wie folgt angezeigt. Dies ist eine systemspezifische Einstellung.

   ![Einstellungen im Produktionssystem überprüfen](../../assets/configuration/split-default-domain.png)
