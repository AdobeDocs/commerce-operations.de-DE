---
title: 'ACSD-48587: Produkt-Widget funktioniert nicht mit SKUs, die HTML-Zeichen enthalten'
description: Wenden Sie den Patch ACSD-48587 an, um das Adobe Commerce-Problem zu beheben, bei dem HTML-Sonderzeichen in den Übereinstimmungsregeln für Produkte verhindern, dass übereinstimmende Produkte angezeigt werden.
feature: Admin Workspace, CMS, Orders, Products
role: Admin
exl-id: c3e31835-03be-46b4-a080-09edf55b5b4e
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ddbd0f6e-b569-5a04-8a70-55058777c373
    internal-label: CMS
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%
---
# ACSD-48587: Produkt-Widget funktioniert nicht mit SKUs, die HTML-Zeichen enthalten

Der Patch ACSD-48587 behebt das Problem, dass HTML-Sonderzeichen in den Übereinstimmungsregeln für das Produkt-Widget verhindern, dass übereinstimmende Produkte angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48587. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Produkt-Widget funktioniert nicht mit SKUs, die *&quot;&amp;&quot;*-Symbole enthalten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt, das *&quot;&amp;&quot;* in der SKU enthält (z. B. s000&amp;01).
1. Bearbeiten des Inhalts einer CMS-Seite im *Page Builder*.
1. Ein Produkt-Widget hinzufügen.
1. Bearbeiten Sie das Widget und legen Sie **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]** fest.
1. Geben Sie die SKU ein, die *&quot;&amp;&quot;* im Feld Produkt-SKUs enthält.
1. Speichern Sie den Inhalt und die CMS-Seite.
1. Überprüfen Sie den Inhalt der *CMS* Seite für die *Page Builder-Vorschau* und die Produkt-Storefront.

<u>Erwartete Ergebnisse</u>:

Das Produkt mit *&quot;&amp;&quot;* in der SKU wird in der Page Builder-Vorschau und in der Storefront angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt mit *&quot;&amp;&quot;* in der SKU wird in der Page Builder-Vorschau nicht angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
