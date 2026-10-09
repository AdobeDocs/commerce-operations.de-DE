---
title: 'ACSD-61322: Produkte, die nicht [!UICONTROL Shared Catalogue] zugewiesen sind, sind in der XML-Sitemap enthalten'
description: Wenden Sie den Patch ACSD-61322 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte/Kategorien, die nicht der [!UICONTROL Shared Catalog] für die Standardgruppe (Allgemein) zugewiesen sind, weiterhin in der XML-Sitemap enthalten sind.
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 48c59cc5-3c2e-5df1-8756-f5c139a28932
    internal-label: Site Navigation
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%
---
# ACSD-61322: Produkte, die nicht [!UICONTROL Shared Catalogue] zugewiesen sind, sind in der XML-Sitemap enthalten

Mit dem Patch ACSD-61322 wird das Problem behoben, dass Produkte/Kategorien, die nicht der [!UICONTROL Shared Catalog] für die Standardgruppe (Allgemein) zugewiesen sind, weiterhin in der XML-Sitemap enthalten sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 installiert ist. Die Patch-ID ist ACSD-61322. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.8 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produkte/Kategorien, die nicht der [!UICONTROL Shared Catalog] für die Gruppe Standard (Allgemein) zugewiesen sind, sind weiterhin in der XML-Sitemap enthalten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einige Kategorien und fügen Sie Produkte hinzu (z. B. Kategorie 1 mit Kategorie 2).
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** und aktivieren Sie *[!UICONTROL Company and Shared Catalog]*.
1. Wechseln Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** und ändern Sie den Standardkatalog.
1. Wählen Sie im Dropdown-Menü **[!UICONTROL Select]** die Option **[!UICONTROL Set Pricing and Structure]** aus und klicken Sie auf **[!UICONTROL Configure]**.
1. Heben Sie unter *Kategorie 1 > Kategorie 2* Auswahl einiger Produkte auf, die nicht im [!UICONTROL Shared Catalog] enthalten sein sollten.
1. Klicken Sie auf **[!UICONTROL Next]** und generieren Sie den Katalog.
1. Erstellen Sie in der Storefront ein Kundenkonto.
1. Gehen Sie zur Kategorie *Kategorie 1 > Kategorie 2*. Es werden nur die Produkte angezeigt, die der [!UICONTROL Shared Catalog] zugewiesen wurden.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]** und erstellen Sie eine neue Sitemap.
1. Öffnen Sie die `sitemap.xml` in der Storefront.
1. Suchen Sie nach den Produkten, die Sie nicht in die [!UICONTROL Shared Catalog] aufgenommen haben.

<u>Erwartete Ergebnisse</u>:

Die Sitemap enthält keine Links zu Produkten und Kategorien, die der [!UICONTROL Shared Catalog] nicht zugewiesen sind.

<u>Tatsächliche Ergebnisse</u>:

Die Sitemap enthält Links zu Produkten und Kategorien, die der [!UICONTROL Shared Catalog] nicht zugewiesen sind.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
