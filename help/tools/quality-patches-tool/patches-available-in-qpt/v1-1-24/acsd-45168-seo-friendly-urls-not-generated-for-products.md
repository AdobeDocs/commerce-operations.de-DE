---
title: 'ACSD-45168: SEO-freundliche URLs werden nicht für Produkte generiert, bei denen url_key-Attribute überschrieben wurden'
description: Wenden Sie den Patch „ACSD-45168“ an, um das Adobe Commerce-Problem zu beheben, dass SEO-freundliche URLs für Produkte, bei denen url_key-Attribute auf Store-Ansichtsebene überschrieben wurden, nicht generiert werden.
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
exl-id: 7d908307-f60c-4758-ad0f-f108ebb94558
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-45168: SEO-freundliche URLs werden nicht für Produkte generiert, bei denen url_key-Attribute überschrieben wurden

Der Patch ACSD-45168 behebt das Problem, dass SEO-freundliche URLs nicht für Produkte generiert werden, bei denen url_key-Attribute auf Store-Ansichtsebene überschrieben wurden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-45168. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

SEO-freundliche URLs werden nicht für Produkte generiert, bei denen url_key-Attribute auf Store-Ansichtsebene überschrieben wurden.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie die Konfiguration wie folgt fest, indem Sie zu **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** gehen:
   * [!UICONTROL Use Categories Path for Product URLs] = *Ja*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Ja*
1. Bereinigen Sie den Konfigurations-Cache.
1. Erstellen Sie zwei Kategorien: [!UICONTROL Category 1] und [!UICONTROL Category 2].
1. Erstellen Sie zwei Produkte: [!UICONTROL Product 1] in [!UICONTROL Category 1], [!UICONTROL Product 2] in [!UICONTROL Category 1].
1. Ändern Sie den Bereich für [!UICONTROL Default Store View] in [!UICONTROL Product 1] .
1. Deaktivieren Sie die optionale URL-[!UICONTROL Key] in [!UICONTROL Search Engine Optimization].
1. Speichern Sie das Produkt.
1. Wechseln Sie zurück zu [!UICONTROL All Store Views].
1. Fügen Sie [!UICONTROL Product 1] zu [!UICONTROL Category 2] hinzu und fügen Sie [!UICONTROL Product 2] zu [!UICONTROL Category 2] hinzu.
1. Überprüfen Sie die `url_rewrite` Tabelle oder [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Erwartete Ergebnisse</u>:

Die SEO-freundliche URL für [!UICONTROL Category 2] wird für [!UICONTROL Product 1] erstellt.

<u>Tatsächliche Ergebnisse</u>:

Die SEO-freundliche URL für [!UICONTROL Category 2] fehlt für [!UICONTROL Product 1], da das URL-Schlüsselattribut für den Bereich der Store-Ansicht überschrieben wurde.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > ](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur

## Verwandtes Lesen

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] Handbuch
* [Best Practices zum Ändern von Datenbanktabellen](https://experienceleague.adobe.com/de/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) im Commerce-Implementierungs-Playbook

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
