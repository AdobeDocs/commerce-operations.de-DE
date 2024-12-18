---
title: 'ACSD-51114: Zufällige Produkte verschwanden aus großen Katalogen, wenn die asynchrone Indizierung aktiviert war'
description: Wenden Sie den Patch ACSD-51114 an, um das Adobe Commerce-Problem zu beheben. Zufällige Produkte verschwanden aus großen Katalogen, wenn die asynchrone Indizierung aktiviert wurde.
feature: Catalog Management, Categories, Products
role: Admin
exl-id: ab1816ef-fb09-46e7-8102-32865f806874
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-51114: Zufällige Produkte verschwanden aus großen Katalogen, wenn die asynchrone Indizierung aktiviert war

>[!NOTE]
>
>Dieser Patch ist veraltet.

Mit dem Patch ACSD-51114 wird das Problem behoben, dass zufällige Produkte aus großen Katalogen verschwanden, wenn die asynchrone Indizierung aktiviert war. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-51114. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]:Nach Patches suchen].Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Zufällige Produkte werden aus großen Katalogen ausgeblendet, wenn die asynchrone Indizierung aktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen Satz von 10 Produkten.
1. Setzen Sie alle Indexer auf den **[!UICONTROL Update on Save]**.
1. Erstellen Sie eine Kategorie und weisen Sie ihr alle Produkte zu.
1. Deaktivieren Sie alle Produkte.
1. Öffnen Sie die Kategorie und stellen Sie sicher, dass keine Produkte vorhanden sind.
1. Setzen Sie alle Indexer auf den **[!UICONTROL Update on Schedule]**.
1. Stellen Sie die `DEFAULT_BATCH_SIZE` in `lib/internal/Magento/Framework/Mview/View.php#L31` auf 2 ein.
1. Aktivieren Sie Produkte in der folgenden Reihenfolge: 1., 9., 2., 5., 10., 3.
1. Cron-Befehl ausführen.
1. Öffnen Sie die Kategorie erneut.

<u>Erwartete Ergebnisse</u>:

Alle aktivierten Produkte werden angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Es werden nicht alle aktivierten Produkte angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
