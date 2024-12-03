---
title: 'ACSD-48807: Produktüberprüfungen nicht nach Storebericht gefiltert'
description: Wenden Sie den Patch ACSD-48807 an, um das Adobe Commerce-Problem zu beheben, bei dem Produktüberprüfungen nicht durch die Storeübersicht über GraphQL gefiltert werden.
feature: Admin Workspace, Products
role: Admin
exl-id: ce2cf5a1-a650-4eaa-8caf-f34dd0111c36
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-48807: Produktüberprüfungen nicht nach Storebericht gefiltert

Der Patch ACSD-48807 behebt das Problem, dass Produktübersichten nicht durch die Storeübersicht über GraphQL gefiltert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID lautet ACSD-48807. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Produktüberprüfungen werden nicht nach Storebericht über GraphQL gefiltert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen zusätzlichen Store.
1. Erstellen Sie ein Kundenkonto und melden Sie sich an.
1. Erstellen Sie im Standardspeicher eine Überprüfung für ein Produkt.
1. Wechseln Sie zu einem anderen Store und erstellen Sie eine weitere Überprüfung für ein Produkt.
1. Genehmigen Sie beide Überprüfungen in Adobe Commerce Admin.
1. Senden Sie eine GraphQL-Kundenabfrage, um Produktüberprüfungen abzurufen, während Sie die in Schritt 1 in der Kopfzeile erstellte Storeüberprüfung angeben.
1. Beobachten Sie die Antwort.

<u>Erwartete Ergebnisse</u>:

In der Antwort wird nur die Produktüberprüfung für den angegebenen Store zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Beide Überprüfungen werden in der Antwort zurückgegeben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
