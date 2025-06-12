---
title: 'ACSD-46809: Beim Zuweisen einer großen Anzahl von Produktquellen wird ein Fehler ausgegeben'
description: Wenden Sie den ACSD-46809 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Benutzende einen Fehler erhalten, wenn sie eine große Anzahl von Produktquellen zuweisen.
feature: Products
role: Admin
exl-id: 4225f49b-84a1-4641-a05b-ba6ada6e83be
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---

# ACSD-46809: Beim Zuweisen einer großen Anzahl von Produktquellen wird ein Fehler ausgegeben

Mit dem Patch ACSD-46809 wird das Problem behoben, dass beim Zuweisen einer großen Anzahl von Produktquellen ein Fehler auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46809. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der/die Benutzende erhält einen Fehler, wenn eine große Anzahl von Produktquellen zugewiesen wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie mehr als 200 benutzerdefinierte Quellen.
1. Navigieren Sie zu Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Bearbeiten Sie ein beliebiges Produkt.
1. Weisen Sie diesem Produkt gleichzeitig 200 Quellen zu.

<u>Erwartete Ergebnisse</u>:

200 Quellen werden dem Produkt ohne Fehler zugewiesen

<u>Tatsächliche Ergebnisse</u>:

*Irgendetwas ist schiefgelaufen* wird ein Fehler angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
