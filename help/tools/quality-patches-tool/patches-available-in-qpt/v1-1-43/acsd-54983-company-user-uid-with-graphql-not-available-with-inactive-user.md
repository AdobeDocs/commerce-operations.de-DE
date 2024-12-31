---
title: 'ACSD-54983: Firmenbenutzer UID mit GraphQL nicht verfügbar mit inaktivem Benutzer'
description: Wenden Sie den Patch ACSD-54983 an, um das Adobe Commerce-Problem zu beheben, bei dem es nicht möglich ist, den Firmenbenutzer UID mit einer GraphQL-Anfrage zu erhalten, wenn der Benutzerstatus auf „Inaktiv“ festgelegt ist.
feature: GraphQL
role: Admin, Developer
exl-id: b188270f-5454-41c9-8370-f4c396095297
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54983: Firmenbenutzer UID mit GraphQL nicht verfügbar mit inaktivem Benutzer

Mit dem Patch ACSD-54983 wird das Problem behoben, dass es nicht möglich ist, den Unternehmensbenutzer UID mit einer GraphQL-Anfrage zu erhalten, wenn der Benutzerstatus auf „Inaktiv“ gesetzt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 installiert ist. Die Patch-ID ist ACSD-54983. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Firmenbenutzer UID kann nicht mit der GraphQL-Anfrage abgerufen werden, wenn der Benutzerstatus auf „Inaktiv“ gesetzt ist.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Firma mit einem Administrator-Benutzer. Beispiel: company@test.com.
1. Neuen Kunden erstellen.
1. Weisen Sie den neuen Kunden einer Firma zu.
1. Hol einen **[!UICONTROL company admin token]**.
1. Rufen Sie mithilfe der **[!UICONTROL company admin token]** die Unternehmensstruktur ab. Siehe [Rückgabe der Unternehmensstruktur](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) in unserer Entwicklerdokumentation.
1. Die Antwort enthält nur *ACTIVE*-Kunden mit ihren IDs.
1. Aktualisieren Sie den Firmenbenutzer auf *INACTIVE*.
1. Rufen Sie die Unternehmensstruktur erneut ab.

<u>Erwartete Ergebnisse</u>:

Es ist möglich, den Firmenbenutzer UID abzurufen, wenn der Status auf Inaktiv gesetzt ist.

<u>Tatsächliche Ergebnisse</u>:

Die inaktiven Kunden sind nicht in der Liste. Der Unternehmensbenutzer UID kann nicht abgerufen werden, wenn der Status auf „Inaktiv“ gesetzt ist.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
