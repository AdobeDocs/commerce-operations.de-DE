---
title: 'ACSD-52398: Die angeforderte Menge ist nicht verfügbar, wenn versucht wird, die Menge des gebündelten Produkts zu aktualisieren'
description: Wenden Sie den ACSD-52398 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die angeforderte Menge nicht verfügbar ist, wenn Sie versuchen, die Menge eines gebündelten Produkts im Warenkorb in der Storefront zu aktualisieren.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 75fa5f96-22e7-40a2-8b8a-f44452e5124d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52398: Die angeforderte Menge ist nicht verfügbar, wenn versucht wird, die Menge des gebündelten Produkts zu aktualisieren

Mit dem Patch ACSD-52398 wird das Problem behoben, dass die angeforderte Menge nicht verfügbar ist, wenn versucht wird, die Menge eines gebündelten Produkts im Warenkorb in der Storefront zu aktualisieren. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52398. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die angeforderte Menge ist nicht verfügbar, wenn versucht wird, die Menge eines gebündelten Produkts im Warenkorb in der Storefront zu aktualisieren.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei einfache Produkte mit Menge *1* und *10*.
1. Erstellen Sie ein gebündeltes Produkt mit den einfachen Produkten.
1. Fügen Sie das gebündelte Produkt zum Warenkorb hinzu.
1. Bearbeiten Sie das Produkt und versuchen Sie, die Menge für die Option, bei der *10* Elemente verfügbar sind, auf *3* zu aktualisieren.

<u>Erwartete Ergebnisse</u>:

Es liegt kein Fehler vor. Die Menge wird erfolgreich aktualisiert, da für diese Option *10* Artikel auf Lager sind.

<u>Tatsächliche Ergebnisse</u>:

Folgender Fehler wird ausgegeben: *Die angeforderte Menge ist nicht verfügbar*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
