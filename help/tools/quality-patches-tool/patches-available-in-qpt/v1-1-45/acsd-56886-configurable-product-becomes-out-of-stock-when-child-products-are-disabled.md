---
title: 'ACSD-56886: Konfigurierbares Produkt ist nicht mehr vorrätig, wenn untergeordnete Produkte deaktiviert sind'
description: Wenden Sie den ACSD-56886-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem das konfigurierbare Produkt nicht mehr vorrätig ist, wenn Produkte deaktiviert sind.
feature: Products
role: Admin, Developer
exl-id: 5e9c1fd4-b56a-42c0-83e7-75e868213124
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-56886: Konfigurierbares Produkt ist nicht mehr vorrätig, wenn untergeordnete Produkte deaktiviert sind

Mit dem Patch ACSD-56886 wird das Problem behoben, dass das konfigurierbare Produkt nicht mehr vorrätig ist, wenn untergeordnete Produkte deaktiviert sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56886. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das konfigurierbare Produkt ist nicht mehr vorrätig, wenn untergeordnete Produkte deaktiviert sind.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich als Administrator an.
1. Setzen Sie alle Indexer im **[!UICONTROL Update By Schedule]**.
1. Erstellen Sie das folgende konfigurierbare Produkt:

   * Name = *TEST CONFIGURABLE 1*
   * Attribut = *color*
   * Werte = *rot* und *schwarz*
   * Preis des **roten** untergeordneten Produkts = *$100*;
   * Preis des „schwarzen“ untergeordneten Produkts = *$200*.

1. Erstellen Sie das folgende geplante Update für das konfigurierbare Produkt:

   * Startdatum = *3* Minuten von jetzt.
   * Enddatum = *5* Minuten nach Startdatum.
   * Produktname = *TEST CONFIGURABLE 1 bearbeitet*.
   * Deaktivieren Sie das **rote** untergeordnete Produkt im **konfigurierbar** Abschnitt.

1. Warten Sie auf das Startdatum.
1. Öffnen Sie die konfigurierbaren Produktdetails in der Storefront.

<u>Erwartete Ergebnisse</u>:

Das konfigurierbare Produkt wird als &quot;**vorrätig** mit der **So niedrig wie 200“**.

<u>Tatsächliche Ergebnisse</u>:

Das konfigurierbare Produkt wird als &quot;**&quot;**.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
