---
title: 'MDVA-39384: Benutzerdefiniertes Kundenattribut für Unternehmensbenutzer kann nicht gespeichert werden'
description: Der Patch MDVA-39384 behebt das Problem, dass das benutzerdefinierte Kundenattribut für einen Unternehmensbenutzer nicht gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39384. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.
feature: Attributes, B2B, Companies
role: Developer
exl-id: 0ccaa4c5-ca43-4b25-963b-b9a547ecc71f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-39384: Benutzerdefiniertes Kundenattribut für Unternehmensbenutzer kann nicht gespeichert werden

Der Patch MDVA-39384 behebt das Problem, dass das benutzerdefinierte Kundenattribut für einen Unternehmensbenutzer nicht gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39384. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit den neuen Versionen des Quality Patches Tool angewendet werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Benutzerdefiniertes Kundenattribut für einen Unternehmensbenutzer wird nicht gespeichert.

<u>Voraussetzungen</u>:

B2B-Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zu **Stores** > Einstellungen > **Konfiguration** > **B2B-Funktionen** und legen Sie die Option **Unternehmen aktivieren** auf &quot;Ja&quot;fest.
1. Erstellen Sie ein benutzerdefiniertes Kundenattribut:
   * Erforderliche Werte: Ja (optional, aktivieren Sie sie, damit der Validierungsfehler angezeigt wird).
   * In Storefront anzeigen: Ja.
   * Forms zur Verwendung in: Alle in der Liste verfügbar.
1. Erstellen Sie ein Unternehmen und melden Sie sich als Unternehmensadministrator an.
1. Navigieren Sie in Ihrem Konto zu Unternehmensstruktur .
1. Klicken Sie auf den Link **Benutzer hinzufügen** .
1. Füllen Sie das Formular einschließlich des benutzerdefinierten Attributs aus.
1. Klicken Sie auf **Speichern**.

<u>Erwartete Ergebnisse</u>:

Die benutzerdefinierten Attributwerte werden beim neuen Unternehmensbenutzer gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Die benutzerdefinierten Attributwerte werden NICHT beim neuen Unternehmensbenutzer gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zum Werkzeug für Qualitätsmuster finden Sie unter:

* [Qualitäts-Patches-Tool veröffentlicht: ein neues Tool, um Qualitäts-Patches selbst bereitzustellen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe des Qualitätspatches-Tools](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!DNL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
