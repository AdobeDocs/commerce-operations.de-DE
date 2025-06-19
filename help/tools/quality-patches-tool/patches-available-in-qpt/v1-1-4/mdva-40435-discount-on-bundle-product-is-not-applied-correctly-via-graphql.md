---
title: 'MDVA-40435: Rabatt auf Paketprodukt wird nicht korrekt über GraphQL angewendet'
description: Der MDVA-40435 Patch löst das Problem, dass der Rabatt auf ein gebündeltes Produkt nicht korrekt über GraphQL angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40435. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: GraphQL, Orders, Personalization, Products
role: Admin
exl-id: 001be138-5d09-455d-a597-57115cd21a25
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-40435: Rabatt auf Paketprodukt wird nicht korrekt über GraphQL angewendet

Der MDVA-40435 Patch löst das Problem, dass der Rabatt auf ein gebündeltes Produkt nicht korrekt über GraphQL angewendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 installiert ist. Die Patch-ID lautet MDVA-40435. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Rabatt auf ein gebündeltes Produkt wird nicht korrekt über GraphQL angewendet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Warenkorb-Preisregel mit einem Gutscheincode für einen festen Rabatt von 5 USD.
1. Erstellen Sie einen leeren Warenkorb über GraphQL.
1. Fügen Sie über GraphQL ein gebündeltes Produkt zum Warenkorb hinzu.
1. Wenden Sie den Gutscheincode über GraphQL auf den Festbetrag (5$) an.
1. Rufen Sie die Warenkorbinformationen über GraphQL ab.

<u>Erwartete Ergebnisse</u>:

„Rabatte“ ist $5.

<u>Tatsächliche Ergebnisse</u>:

„Rabatte“ ist NULL.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
