---
title: Abrufen der Authentifizierungsschlüssel
description: Führen Sie diese Schritte aus, um Anmeldeinformationen für den Zugriff auf Adobe Commerce- und Magento Open Source Composer-Pakete unter repo.magento.com abzurufen.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Abrufen der Authentifizierungsschlüssel

Die `repo.magento.com` Repository ist der Speicherort, an dem Adobe Commerce- und Magento Open Source- sowie Drittanbieter-Composer-Pakete gespeichert werden und Authentifizierung erfordern. Verwenden Sie Ihr Commerce Marketplace-Konto, um ein 32-Zeichen-Paar zu generieren. *Authentifizierungsschlüssel* , um auf das Repository zuzugreifen.

Für die Zugriffsberechtigung auf Adobe Commerce- und Magento Open Source-Packages müssen Sie Schlüssel verwenden, die mit einem MAGEID verknüpft sind, dem Zugriff auf diese Packages gewährt wurde. Die MAGEID ist in der Regel der Primäre Ansprechpartner für das Adobe Commerce-Konto und ist möglicherweise nicht immer Projektinhaber des Adobe Commerce-Projekts für Cloud-Infrastruktur.

>[!TIP]
>
>Bei Auftreten von [errors](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html), haben Sie möglicherweise keine Berechtigung für den Zugriff auf das Paket oder die Zugriffsberechtigung ist aufgrund einer ausstehenden Rechnung auf Ihrem Konto abgelaufen.
>
>* Wenn Sie die Primäre Kontaktperson im Konto sind, stellen Sie sicher, dass auf dem Konto keine ausstehende Rechnung aufgeführt ist.
>* Wenn die von der Primären Kontaktperson bereitgestellten Schlüssel nicht funktionieren und auf dem Konto keine ausstehenden Rechnungen vorliegen, wenden Sie sich an [Adobe Commerce-Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) für Unterstützung bei der Verwendung der MAGEID des Primären Kontakts.

So erstellen Sie Authentifizierungsschlüssel:

1. Melden Sie sich bei [Commerce Marketplace](https://marketplace.magento.com). Wenn Sie kein Konto haben, klicken Sie auf **registrieren**.
1. Klicken Sie oben rechts auf der Seite auf Ihren Kontonamen und wählen Sie **Mein Profil**.

1. Klicks **Zugriffsschlüssel** auf der Registerkarte Marketplace .

   ![Sichere Zugriffsschlüssel auf Commerce Marketplace abrufen](../../assets/installation/cloud_access-key.png)

1. Klicks **Erstellen eines neuen Zugriffsschlüssels**. Geben Sie einen bestimmten Namen für die Schlüssel ein (z. B. den Namen des Entwicklers, der die Schlüssel erhält) und klicken Sie auf **OK**.

1. Neue öffentliche und private Schlüssel sind jetzt mit Ihrem Konto verknüpft, auf das Sie klicken können, um es zu kopieren. Speichern Sie diese Informationen oder lassen Sie die Seite bei der Arbeit mit Ihrem Projekt geöffnet. Verwenden Sie die **Öffentlicher Schlüssel** als Benutzernamen und **Privater Schlüssel** als Passwort.

## Authentifizierungsschlüssel verwalten

Sie können auch Authentifizierungsschlüssel deaktivieren oder löschen. Beispielsweise können Sie Schlüssel aus Sicherheitsgründen deaktivieren oder löschen, nachdem ein Benutzer Ihre Organisation verlassen hat.

* Zum Deaktivieren von Schlüsseln klicken Sie auf **Deaktivieren**. Sie können dies tun, wenn Sie die Verwendung Ihrer Schlüssel aussetzen möchten.
* So aktivieren Sie einen zuvor deaktivierten Schlüssel: Klicken Sie auf **Aktivieren**.
* So löschen Sie Schlüssel: Klicken Sie auf **Löschen**.

### SSH-Zugriffstoken verwalten

Um Adobe Commerce-Versionen mit SSH herunterzuladen, müssen Sie ein Zugriffstoken für Downloads generieren. So generieren Sie ein Token:

1. Melden Sie sich bei Ihrer [magento.com account](https://account.magento.com/customer/account/login).
1. Klicks **Mein Konto** oben auf der Seite.
1. Klicks **Kontoeinstellungen** > **Download-Zugriffs-Token**.

   ![Auf die Schlüssel zugreifen](../../assets/installation/connect_keys1.png)

1. Klicks **Neues Token generieren** , um ein vorhandenes Token zu ersetzen und zu deaktivieren.

Sie müssen Ihr MAGEID und Ihr Token verwenden, um eine Version herunterzuladen. Ihre MAGEID wird oben links auf Ihrer Kontoseite angezeigt.

Beispiel:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Verwenden Sie Ihre Authentifizierungsschlüssel für:

* [Abrufen des Metapakets (Integratoren, Packager)](../composer.md)
* [GitHub-Repository klonen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (nur beitragende Entwickler)
* [Module aktualisieren und verwalten](../../upgrade/modules/upgrade.md)
