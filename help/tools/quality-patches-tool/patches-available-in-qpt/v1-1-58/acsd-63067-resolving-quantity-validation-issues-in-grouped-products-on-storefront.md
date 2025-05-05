---
title: 'ACSD-63067: Probleme bei der Mengenvalidierung in gruppierten Produkten in der Storefront beheben'
description: Wenden Sie den Patch ACSD-63067 an, um das Adobe Commerce-Problem zu beheben, bei dem alle Produktmengen in gruppierten Produkten fälschlicherweise als ungültig markiert sind, wenn nur ein Produkt eine falsche Menge hat.
feature: Storefront
role: Admin, Developer
source-git-commit: 7446f4d83932eedc6fa711ad09c6ee559d357f70
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067: Probleme bei der Mengenvalidierung in gruppierten Produkten in der Storefront beheben

Mit dem Patch ACSD-63067 wird das Problem behoben, dass alle Produktmengen in gruppierten Produkten fälschlicherweise als ungültig markiert werden, wenn nur ein Produkt eine falsche Menge aufweist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-63067. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei gruppierten Produkten führt eine ungültige Menge in einem der Unterprodukte dazu, dass alle Mengen fälschlicherweise als ungültig markiert werden. Darüber hinaus wird eine Validierungsmeldung für alle Produkte angezeigt, anstatt nur für das Produkt mit der ungültigen Menge.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein neues gruppiertes Produkt mit mindestens zwei einfachen Produkten als Optionen.
1. Öffnen Sie das Produkt in der Storefront.
1. Geben Sie eine ungültige Menge (Beispiel: -1) für eine der Optionen und eine gültige Menge (Beispiel: 1) für die verbleibenden Optionen ein.
1. Klicken Sie auf **[!UICONTROL Add to Cart]**.

<u>Erwartete Ergebnisse</u>:

Nur das Produkt mit der ungültigen Menge wird als ungültig markiert.

<u>Tatsächliche Ergebnisse</u>:

Alle Produktmengen werden als ungültig markiert und die Meldung *Bitte geben Sie die Menge des Produkts/der Produkte an). wird für alle Produkte angezeigt*.


## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
