---
title: "ACSD-54983: Firmenbenutzer UID mit GraphQL ist mit inaktivem Benutzer nicht verfügbar"
description: Wenden Sie den Patch ACSD-54983 an, um das Adobe Commerce-Problem zu beheben, bei dem es nicht möglich ist, den Unternehmensbenutzer UID mit GraphQL-Anfrage abzurufen, wenn der Benutzerstatus auf "Inaktiv"festgelegt ist.
feature: GraphQL
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54983: Unternehmensbenutzer UID mit GraphQL ist nicht für inaktive Benutzer verfügbar

Der Patch ACSD-54983 behebt das Problem, bei dem es nicht möglich ist, den Unternehmensbenutzer UID mit GraphQL-Anfrage abzurufen, wenn der Benutzerstatus auf &quot;Inaktiv&quot;gesetzt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 installiert ist. Die Patch-ID ist ACSD-54983. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Unternehmensbenutzer UID mit GraphQL-Anfrage kann nicht abgerufen werden, wenn der Benutzerstatus auf &quot;Inaktiv&quot;festgelegt ist.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Unternehmen mit einem Administrator-Benutzer. Beispiel: company@test.com.
1. Erstellen Sie einen neuen Kunden.
1. Weisen Sie den neuen Kunden einem Unternehmen zu.
1. Holen Sie sich einen **[!UICONTROL company admin token]**.
1. Rufen Sie mit dem Wert &quot;**[!UICONTROL company admin token]**&quot;die Unternehmensstruktur ab. Siehe [Zurückgeben der Unternehmensstruktur](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) in unserer Entwicklerdokumentation.
1. Die Antwort enthält nur *AKTIVE* -Kunden mit ihren IDs.
1. Aktualisieren Sie den Unternehmensbenutzer auf *INACTIVE*.
1. Rufen Sie die Unternehmensstruktur erneut ab.

<u>Erwartete Ergebnisse</u>:

Sie können den Unternehmensbenutzer UID abrufen, wenn der Status auf &quot;Inaktiv&quot;festgelegt ist.

<u>Tatsächliche Ergebnisse</u>:

Die inaktiven Kunden sind nicht in der Liste enthalten. Der Unternehmensbenutzer UID kann nicht abgerufen werden, wenn der Status auf &quot;Inaktiv&quot;festgelegt ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
