---
title: Abrufen der Authentifizierungsschlüssel
description: Führen Sie diese Schritte aus, um Anmeldeinformationen für den Zugriff auf Adobe Commerce Composer-Pakete unter repo.magento.com abzurufen.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Abrufen der Authentifizierungsschlüssel

Im `repo.magento.com`-Repository werden Adobe Commerce- und Drittanbieter-Composer-Pakete gespeichert und müssen authentifiziert werden. Verwenden Sie Ihr Commerce Marketplace-Konto, um ein 32-stelliges *Authentifizierungsschlüssel*-Paar für den Zugriff auf das Repository zu generieren.

Für die Zugriffsberechtigung auf Adobe Commerce-Pakete müssen Sie Schlüssel verwenden, die mit einem MAGEID verknüpft sind, dem Zugriff auf diese Pakete gewährt wurde. Die MAGEID ist in der Regel der Primäre Ansprechpartner für das Adobe Commerce-Konto und ist möglicherweise nicht immer Projektinhaber des Adobe Commerce-Projekts für Cloud-Infrastruktur.

>[!TIP]
>
>Wenn Sie auf [errors](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html) stoßen, haben Sie möglicherweise keine Berechtigung zum Zugriff auf das Paket oder die Zugriffsberechtigung ist aufgrund einer ausstehenden Rechnung auf Ihrem Konto abgelaufen.
>
>* Wenn Sie die Primäre Kontaktperson im Konto sind, stellen Sie sicher, dass auf dem Konto keine ausstehende Rechnung aufgeführt ist.
>* Wenn die vom Primären Kontakt bereitgestellten Schlüssel nicht funktionieren und keine ausstehenden Rechnungen auf dem Konto vorliegen, sollte sich der Primäre Kontakt an den [Adobe Commerce-Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) wenden, um Hilfe zu erhalten.

So erstellen Sie Authentifizierungsschlüssel:

1. Melden Sie sich bei [Commerce Marketplace](https://commercemarketplace.adobe.com/) an. Wenn Sie kein Konto haben, klicken Sie auf **Registrieren**.

1. Klicken Sie oben rechts auf der Seite auf Ihren Kontonamen und wählen Sie **Mein Profil** aus.

1. Klicken Sie auf der Registerkarte &quot;Marketplace&quot;auf **Zugriffsschlüssel** .

   ![Sichern Sie sich Ihre sicheren Zugriffsschlüssel auf Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Klicken Sie auf **Neuen Zugriffsschlüssel erstellen**. Geben Sie einen bestimmten Namen für die Schlüssel ein (z. B. den Namen des Entwicklers, der die Schlüssel erhält) und klicken Sie auf **OK**.

1. Neue öffentliche und private Schlüssel sind jetzt mit Ihrem Konto verknüpft, auf das Sie klicken können, um es zu kopieren. Speichern Sie diese Informationen oder lassen Sie die Seite bei der Arbeit mit Ihrem Projekt geöffnet. Verwenden Sie den **öffentlichen Schlüssel** als Ihren Benutzernamen und den **privaten Schlüssel** als Ihr Kennwort.

## Authentifizierungsschlüssel verwalten

Sie können auch Authentifizierungsschlüssel deaktivieren oder löschen. Beispielsweise können Sie Schlüssel aus Sicherheitsgründen deaktivieren oder löschen, nachdem ein Benutzer Ihre Organisation verlassen hat.

* Zum Deaktivieren von Schlüsseln klicken Sie auf **Deaktivieren**. Sie können dies tun, wenn Sie die Verwendung Ihrer Schlüssel aussetzen möchten.
* So aktivieren Sie einen zuvor deaktivierten Schlüssel: Klicken Sie auf **Aktivieren**.
* Löschen von Schlüsseln: Klicken Sie auf **Löschen**.

### SSH-Zugriffstoken verwalten

Um Adobe Commerce-Versionen mit SSH herunterzuladen, müssen Sie ein Zugriffstoken für Downloads generieren. So generieren Sie ein Token:

1. Melden Sie sich bei Ihrem [magento.com Konto](https://account.magento.com/customer/account/login) an.
1. Klicken Sie oben auf der Seite auf **Mein Konto** .
1. Klicken Sie auf **Kontoeinstellungen** > **Downloads Zugriffstoken**.

   ![Auf Ihre Schlüssel zugreifen](../../assets/installation/connect_keys1.png)

1. Klicken Sie auf **Neues Token generieren** , um ein vorhandenes Token zu ersetzen und zu deaktivieren.

Sie müssen Ihr MAGEID und Ihr Token verwenden, um eine Version herunterzuladen. Ihre MAGEID wird oben links auf Ihrer Kontoseite angezeigt.

Beispiel:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Verwenden Sie Ihre Authentifizierungsschlüssel für:

* [Abrufen des Metapakets (Integratoren, Packager)](../composer.md)
* [Klonen Sie das GitHub-Repository](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (nur beitragende Entwickler)
* [Module aktualisieren und verwalten](../../upgrade/modules/upgrade.md)
