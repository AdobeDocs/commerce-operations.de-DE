---
title: 'ACSD-48807: Produktbewertungen nicht nach Storeview gefiltert'
description: Wenden Sie den ACSD-48807 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Produktbewertungen nicht nach Storeview über GraphQL gefiltert werden.
feature: Admin Workspace, Products
role: Admin
exl-id: ce2cf5a1-a650-4eaa-8caf-f34dd0111c36
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-48807: Produktbewertungen nicht nach Storeview gefiltert

Mit dem Patch ACSD-48807 wird das Problem behoben, dass Produktbewertungen nicht nach Storeview über GraphQL gefiltert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID ist ACSD-48807. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produktbewertungen werden nicht nach Storeview über GraphQL gefiltert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine zusätzliche Storeview.
1. Kundenkonto erstellen und sich anmelden.
1. Erstellen Sie in der standardmäßigen Store-Vorschau eine Überprüfung für ein Produkt.
1. Wechseln Sie zu einer anderen Storeview und erstellen Sie eine weitere Review für ein Produkt.
1. Genehmigen Sie beide Überprüfungen in Adobe Commerce Admin.
1. Senden Sie eine GraphQL-Kundenabfrage zum Abrufen von Produktüberprüfungen, während Sie die in Schritt 1 erstellte Storereview in der Kopfzeile angeben.
1. Beobachten Sie die Antwort.

<u>Erwartete Ergebnisse</u>:

In der Antwort wird nur die Produktüberprüfung für die angegebene Storeview zurückgegeben.

<u>Tatsächliche Ergebnisse</u>:

Beide Überprüfungen werden in der Antwort zurückgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
