---
title: Abrufen Ihrer Authentifizierungsschlüssel
description: Führen Sie diese Schritte aus, um Anmeldeinformationen für den Zugriff auf Adobe Commerce Composer-Pakete auf repo.magento.com abzurufen.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: fc63ca58cd2ff7c5ec597751980a39bfbe68aa5f
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Abrufen Ihrer Authentifizierungsschlüssel

Das `repo.magento.com`-Repository ist der Speicherort, in dem Adobe Commerce und Composer-Pakete von Drittanbietern gespeichert werden und eine Authentifizierung erfordern. Verwenden Sie Ihr Commerce Marketplace-Konto, um ein Paar 32-stelliger *Authentifizierungsschlüssel) für* Zugriff auf das Repository zu generieren.

Für die Zugriffsberechtigung auf Adobe Commerce-Pakete müssen Sie Schlüssel verwenden, die mit einer MAGEID verknüpft sind, der Zugriff auf diese Pakete gewährt wurde. Die MAGEID ist in der Regel der Primäre Ansprechpartner im Adobe Commerce-Konto und möglicherweise nicht immer der Projektbesitzer des Adobe Commerce on Cloud Infrastructure-Projekts.

>[!TIP]
>
>Wenn Sie auf [Fehler](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html?lang=de) stoßen, sind Sie möglicherweise nicht berechtigt, auf das Paket zuzugreifen, oder die Zugriffsberechtigung ist aufgrund einer ausstehenden Rechnung in Ihrem Konto abgelaufen.
>
>* Wenn Sie der Primäre Ansprechpartner für das Konto sind, stellen Sie sicher, dass im Konto keine ausstehende Rechnung aufgeführt ist.
>* Wenn die vom Primären Ansprechpartner bereitgestellten Schlüssel nicht funktionieren und keine ausstehenden Rechnungen für das Konto vorhanden sind, sollte sich der Primäre Ansprechpartner an den [Adobe Commerce-Support](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=de#submit-ticket) wenden, um Unterstützung zu erhalten.

So erstellen Sie Authentifizierungsschlüssel:

1. Melden Sie sich bei der [Commerce Marketplace](https://commercemarketplace.adobe.com/) an. Wenn Sie noch kein Konto haben, klicken Sie auf **Registrieren**.

1. Klicken Sie oben rechts auf der Seite auf Ihren Kontonamen und wählen Sie **Mein Profil** aus.

1. Klicken Sie **der Registerkarte** Marketplace“ auf „Zugriffsschlüssel“.

   ![Sichere Zugriffsschlüssel für Commerce Marketplace abrufen](../../assets/installation/cloud_access-key.png)

1. Klicken Sie **Neuen Zugriffsschlüssel erstellen**. Geben Sie einen bestimmten Namen für die Schlüssel ein (z. B. den Namen des Entwicklers, der die Schlüssel erhält) und klicken Sie auf **OK**.

1. Ihrem Konto sind jetzt neue öffentliche und private Schlüssel zugeordnet, auf die Sie klicken können, um sie zu kopieren. Speichern Sie diese Informationen oder lassen Sie die Seite offen, wenn Sie mit Ihrem Projekt arbeiten. Verwenden Sie den **Öffentlichen Schlüssel** als Benutzernamen und den **Privaten Schlüssel** als Kennwort.

## Verwalten von Authentifizierungsschlüsseln

Sie können Authentifizierungsschlüssel auch deaktivieren oder löschen. Beispielsweise können Sie Schlüssel aus Sicherheitsgründen deaktivieren oder löschen, nachdem jemand Ihr Unternehmen verlassen hat.

* So deaktivieren Sie Schlüssel: Klicken Sie auf **Deaktivieren**. Dies ist möglich, wenn die Verwendung der Schlüssel ausgesetzt werden soll.
* So aktivieren Sie einen zuvor deaktivierten Schlüssel: Klicken Sie **Aktivieren**.
* Löschen von Schlüsseln: Klicken Sie auf **Löschen**.

### SSH-Zugriffstoken verwalten

Um Adobe Commerce-Versionen mit SSH herunterzuladen, müssen Sie ein Zugriffstoken für Downloads generieren. So generieren Sie ein Token:

1. Melden Sie sich bei Ihrem [magento.com-Konto an](https://account.magento.com/customer/account/login).
1. Klicken **oben auf** Seite auf „Mein Konto“.
1. Klicken Sie auf **Kontoeinstellungen** > **Download-Zugriffstoken**.

   ![Greifen Sie auf Ihre Schlüssel zu](../../assets/installation/connect_keys1.png)

1. Klicken Sie **Neues Token erstellen**, um ein vorhandenes Token zu ersetzen und zu deaktivieren.

Sie müssen Ihre MAGEID plus Ihr Token verwenden, um eine Version herunterzuladen. Ihre MAGEID wird oben links auf Ihrer Kontoseite angezeigt.

Beispiel:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Verwenden Sie Ihre Authentifizierungsschlüssel für:

* [Abrufen des Metapakets (Integratoren, Packager)](../composer.md)
* [Klonen Sie das GitHub-Repository](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (nur für mitwirkende Entwickler)
* [Aktualisieren und Verwalten von Modulen](../../upgrade/modules/upgrade.md)
