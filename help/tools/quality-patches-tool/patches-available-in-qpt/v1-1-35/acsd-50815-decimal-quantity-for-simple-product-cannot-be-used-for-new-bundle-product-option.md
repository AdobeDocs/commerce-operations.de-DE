---
title: 'ACSD-50815: Dezimalzahl für einfaches Produkt kann nicht für neue gebündelte Produktoption verwendet werden'
description: Wenden Sie den Patch ACSD-50815 an, um das Adobe Commerce-Problem zu beheben, bei dem die Dezimalzahl für ein einfaches Produkt nicht für eine neue gebündelte Produktoption verwendet werden kann.
feature: Products
role: Admin
exl-id: 5cd69abe-bd88-497d-9696-804c787b73ef
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-50815: Dezimalzahl für einfaches Produkt kann nicht für neue gebündelte Produktoption verwendet werden

Mit dem Patch ACSD-50815 wird das Problem behoben, dass die Dezimalmenge für ein einfaches Produkt nicht für eine neue gebündelte Produktoption verwendet werden kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 installiert ist. Die Patch-ID ist ACSD-50815. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Dezimalzahl für ein einfaches Produkt kann nicht für eine neue gebündelte Produktoption verwendet werden.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Administrator an.
1. Erstellen Sie ein neues einfaches Produkt.
   * Legen Sie im **[!UICONTROL Advanced Inventory]**-Fenster [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes] fest.
   * Speichern Sie das einfache Produkt.
1. Erstellen Sie ein neues gebündeltes Produkt.
1. Beliebige Option hinzufügen.
1. Fügen Sie dieser Option das einfache Produkt hinzu.
1. Legen Sie eine Dezimalzahl für das einfache Produkt in der Option für gebündelte Produkte fest. Beispiel: 1.5.

<u>Erwartete Ergebnisse</u>:

Es ist möglich, eine Dezimalzahl festzulegen. Keine Fehler angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Der Fehler *Bitte eine gültige Zahl in dieses Feld eingeben* wird angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
