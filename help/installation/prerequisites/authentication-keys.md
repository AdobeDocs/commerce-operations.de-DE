---
title: Abrufen der Authentifizierungsschlüssel
description: Führen Sie diese Schritte aus, um Anmeldeinformationen für den Zugriff auf Adobe Commerce- und Magento Open Source Composer-Pakete auf repo.magento.com abzurufen.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Abrufen der Authentifizierungsschlüssel

Die `repo.magento.com` Repository ist der Speicherort, an dem Adobe Commerce- und Magento Open Source- sowie Drittanbieter-Composer-Pakete gespeichert werden und Authentifizierung erfordern. Verwenden Sie Ihr Commerce Marketplace-Konto, um ein 32-stelliges Paar zu generieren. *Authentifizierungsschlüssel* , um auf das Repository zuzugreifen.

>[!NOTE]
>
>Für die Zugriffsberechtigung auf Adobe Commerce- und Magento Open Source-Packages müssen Sie Schlüssel verwenden, die mit einem MAGEID verknüpft sind, dem Zugriff auf diese Packages gewährt wurde. Der MAGEID ist normalerweise der **Rechnungskontakte** auf dem Adobe Commerce-Konto und möglicherweise nicht immer der **Projektinhaber** des Adobe Commerce-Projekts zur Cloud-Infrastruktur. Bei Auftreten von [errors](https://support.magento.com/hc/en-us/articles/360040296392), haben Sie möglicherweise keine Berechtigung für den Zugriff auf das Paket oder die Zugriffsberechtigung ist aufgrund einer ausstehenden Rechnung auf dem Konto abgelaufen. Kontakt [Adobe Commerce-Support](https://support.magento.com/hc/en-us) für Unterstützung bei Ihrer MAGEID.

So erstellen Sie Authentifizierungsschlüssel:

1. Melden Sie sich bei der [Commerce Marketplace](https://marketplace.magento.com). Wenn Sie kein Konto haben, klicken Sie auf **registrieren**.
1. Klicken Sie oben rechts auf der Seite auf Ihren Kontonamen und wählen Sie **Mein Profil**.

1. Klicken **Zugriffsschlüssel** auf der Registerkarte Marketplace .

   ![Sichere Zugriffsschlüssel auf Commerce Marketplace abrufen](../../assets/installation/cloud_access-key.png)

1. Klicken **Erstellen eines neuen Zugriffsschlüssels**. Geben Sie einen bestimmten Namen für die Schlüssel ein (z. B. den Namen des Entwicklers, der die Schlüssel erhält) und klicken Sie auf **OK**.

1. Neue öffentliche und private Schlüssel sind jetzt mit Ihrem Konto verknüpft, auf das Sie klicken können, um es zu kopieren. Speichern Sie diese Informationen oder lassen Sie die Seite bei der Arbeit mit Ihrem Projekt geöffnet. Verwenden Sie die **Öffentlicher Schlüssel** als Benutzernamen und **Privater Schlüssel** als Passwort.

## Authentifizierungsschlüssel verwalten

Sie können auch Authentifizierungsschlüssel deaktivieren oder löschen. Beispielsweise können Sie Schlüssel aus Sicherheitsgründen deaktivieren oder löschen, nachdem ein Benutzer Ihre Organisation verlassen hat.

* So deaktivieren Sie Schlüssel: Klicken **Deaktivieren**. Sie können dies tun, wenn Sie die Verwendung Ihrer Schlüssel aussetzen möchten.
* So aktivieren Sie einen zuvor deaktivierten Schlüssel: Klicken **Aktivieren**.
* So löschen Sie Schlüssel: Klicken **Löschen**.

### SSH-Zugriffstoken verwalten

Um Adobe Commerce-Versionen mit SSH herunterzuladen, müssen Sie ein Zugriffstoken für Downloads generieren. So generieren Sie ein Token:

1. Melden Sie sich bei Ihrer [magento.com-Konto](https://account.magento.com/customer/account/login).
1. Klicken **Mein Konto** oben auf der Seite.
1. Klicken **Kontoeinstellungen** > **Download-Zugriffs-Token**.

   ![Auf die Schlüssel zugreifen](../../assets/installation/connect_keys1.png)

1. Klicken **Neues Token generieren** , um ein vorhandenes Token zu ersetzen und zu deaktivieren.

Sie müssen Ihr MAGEID und Ihr Token verwenden, um eine Version herunterzuladen. Ihre MAGEID wird oben links auf Ihrer Kontoseite angezeigt.

Beispiel:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Verwenden Sie Ihre Authentifizierungsschlüssel für:

* [Abrufen des Metapakets (Integratoren, Packager)](../composer.md)
* [GitHub-Repository klonen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (nur beitragende Entwickler)
* [Module aktualisieren und verwalten](../../upgrade/modules/upgrade.md)
