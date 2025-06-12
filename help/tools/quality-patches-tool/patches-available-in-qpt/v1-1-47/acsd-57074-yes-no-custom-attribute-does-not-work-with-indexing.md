---
title: 'ACSD-57074: *Ja/Nein* benutzerdefiniertes Attribut mit dem Präfix „price_*" im Attribut „attribute_code“ funktioniert nicht mit der Indizierung'
description: Wenden Sie den Patch ACSD-57074 an, um das Adobe Commerce-Problem zu beheben, bei dem das benutzerdefinierte Attribut *Ja/Nein* mit dem Präfix „price_*" im Attribut „attribute_code“ nicht mit der Indizierung funktioniert.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: 718b8f2d-4d3d-4755-8a91-5c2f97114813
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57074: *Ja/Nein* Benutzerdefiniertes Attribut mit `price_*` Präfix in `attribute_code` Attribut funktioniert nicht mit der Indizierung

Mit dem Patch ACSD-57074 wird das Problem behoben, dass das benutzerdefinierte Attribut *Ja/Nein* mit `price_*` Präfix im Attribut `attribute_code` bei der Indizierung nicht funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.47 installiert ist. Die Patch-ID ist ACSD-57074. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das *Ja/Nein* benutzerdefinierte Attribut mit `price_*` Präfix im `attribute_code` funktioniert nicht bei der Indizierung.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein benutzerdefiniertes Produktattribut mit den folgenden Optionen:
   * *[!UICONTROL Catalog Input Type]*: *Ja/Nein*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *Ja*
1. Weisen Sie das -Attribut dem standardmäßigen Attributsatz zu.
1. Erstellen Sie ein Produkt mit dem Attribut , das wir erstellt haben.
1. Weisen Sie das soeben erstellte Produkt einer Kategorie zu.
1. Vollständige Neuindizierung ausführen.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird in der zugewiesenen Kategorie angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird nicht auf der Kategorieseite auf der Vorderseite angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
