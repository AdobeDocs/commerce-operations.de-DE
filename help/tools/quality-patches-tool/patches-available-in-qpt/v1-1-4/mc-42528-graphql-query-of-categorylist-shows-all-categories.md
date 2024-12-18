---
title: 'MC-42528: GraphQL-Abfrage der categoryList zeigt alle Kategorien an'
description: Der Patch MC-42528 löst das Problem, dass die GraphQL-Abfrage von „categoryList“ sowohl zugewiesene als auch nicht zugewiesene Kategorien zurückgibt, wenn die Navigationskategorie einer bestimmten Kategorie auf „Ablehnen“ eingestellt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MC-42528. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
exl-id: 0611a7ff-9d55-4d95-9d4e-9ce1d9096bb6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MC-42528: GraphQL-Abfrage der categoryList zeigt alle Kategorien an

Der Patch MC-42528 löst das Problem, dass die GraphQL-Abfrage von `categoryList` sowohl zugewiesene als auch nicht zugewiesene Kategorien zurückgibt, wenn die Navigationskategorie einer bestimmten Kategorie auf „Ablehnen“ eingestellt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MC-42528. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

GraphQL-Abfrage von `categoryList` gibt sowohl zugewiesene als auch nicht zugewiesene Kategorien zurück.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Kategorien, CAT1 und CAT2, und weisen Sie jeder Kategorie wenige Produkte zu.
1. Erstellen Sie einen privaten freigegebenen Katalog.
1. Erstellen Sie einen Unternehmensbenutzer und weisen Sie ihn dem erstellten freigegebenen Katalog zu.
1. Weisen Sie CAT 1 dem benutzerdefinierten Katalog zu und legen Sie die Kategorieberechtigung für die Kundengruppe des privaten Katalogs auf die Kategorie „Durchsuchen zulassen“ fest.
1. Legen Sie die Kategorieberechtigung für CAT2 für die Kundengruppe des privaten Katalogs auf die Browsing-Kategorie „Ablehnen“ fest.
1. Führen Sie die `categoryList`- oder `categories` GraphQL-Abfrage als Firmenbenutzer aus.

<u>Erwartete Ergebnisse</u>:

In der Antwort wird nur CAT1 angezeigt.

<u>Tatsächliche Ergebnisse</u>:

In der Antwort werden alle Kategorien angezeigt, unabhängig von den Browserberechtigungen der Kategorie.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
