---
title: 'MDVA-40311: Fehler „Ungültiger Sicherheits- oder Formularschlüssel“ nach der Anmeldung bei Admin, wenn ein benutzerdefinierter Administratorpfad konfiguriert ist'
description: 'Mit dem Patch MDVA-40311 wird das Problem behoben, bei dem der Administrator eine Fehlermeldung erhält: *Ungültiger Sicherheits- oder Formularschlüssel. Bitte aktualisieren Sie die Seite* nach der Anmeldung bei der Administratorin bzw. dem Administrator, wenn der benutzerdefinierte Administratorpfad konfiguriert und der geheime Schlüssel aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Die Patch-ID lautet MDVA-40311. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.'
feature: Admin Workspace, Compliance, Security
role: Admin
exl-id: dce4914b-e32e-4af0-be24-e55680191fa3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-40311: Fehler „Ungültiger Sicherheits- oder Formularschlüssel“ nach der Anmeldung bei Admin, wenn ein benutzerdefinierter Administratorpfad konfiguriert ist

Der Patch MDVA-40311 behebt das Problem, dass der Admin-Benutzer eine Fehlermeldung erhält: *Ungültige Sicherheit oder Formularschlüssel. Bitte aktualisieren Sie die Seite* nachdem Sie sich beim Administrator angemeldet haben, wenn der benutzerdefinierte Administratorpfad konfiguriert und der geheime Schlüssel aktiviert ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 installiert ist. Die Patch-ID lautet MDVA-40311. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator erhält eine Fehlermeldung: *Ungültiger Sicherheits- oder Formularschlüssel. Bitte aktualisieren Sie die Seite* nachdem Sie sich beim Administrator angemeldet haben, wenn der benutzerdefinierte Administratorpfad konfiguriert und der geheime Schlüssel aktiviert ist.

<u>Schritte zur Reproduktion</u>:

* Melden Sie sich als Admin-Benutzer mit einem gültigen Benutzernamen und Kennwort an.

<u>Erwartete Ergebnisse</u>:

Der Benutzer kann sich ohne Fehlermeldung anmelden.

<u>Tatsächliche Ergebnisse</u>:

*Ungültiger Sicherheit- oder Formularschlüssel. Bitte Seite aktualisieren* Fehlermeldung wird angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
