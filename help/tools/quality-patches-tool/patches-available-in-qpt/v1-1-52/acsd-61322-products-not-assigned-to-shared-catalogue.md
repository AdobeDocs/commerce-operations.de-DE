---
title: "ACSD-61322: Nicht [!UICONTROL Shared Catalogue] zugewiesene Produkte sind in der XML-Sitemap enthalten."
description: Wenden Sie den Patch ACSD-61322 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte/Kategorien, die nicht der Gruppe "[!UICONTROL Shared Catalog]"für die Standardgruppe (Allgemein) zugewiesen sind, weiterhin in der XML-Sitemap enthalten sind.
feature: Site Navigation, B2B
role: Admin, Developer
source-git-commit: 1eed4f1f6484112a0ec728659aa4b79855bf9612
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-61322: Nicht [!UICONTROL Shared Catalogue] zugewiesene Produkte sind in der XML-Sitemap enthalten

Der Patch ACSD-61322 behebt das Problem, dass Produkte/Kategorien, die nicht der Gruppe &quot;[!UICONTROL Shared Catalog]&quot;für die Standardgruppe (Allgemein) zugewiesen sind, weiterhin in der XML-Sitemap enthalten sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-61322. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Produkte/Kategorien, die nicht der Gruppe [!UICONTROL Shared Catalog] für die Standardgruppe (Allgemein) zugewiesen sind, sind weiterhin in der XML-Sitemap enthalten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einige Kategorien und fügen Sie Produkte hinzu (z. B. Kategorie 1 mit Kategorie 2).
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** und aktivieren Sie *[!UICONTROL Company and Shared Catalog]*.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** und ändern Sie den Standardkatalog.
1. Wählen Sie im Dropdownmenü **[!UICONTROL Select]** die Option **[!UICONTROL Set Pricing and Structure]** aus und klicken Sie auf **[!UICONTROL Configure]**.
1. Heben Sie unter der Kategorie *Kategorie 1 > Kategorie 2* die Auswahl einiger Produkte auf, die nicht in der Kategorie [!UICONTROL Shared Catalog] enthalten sein sollten.
1. Klicken Sie auf &quot;**[!UICONTROL Next]**&quot;und generieren Sie den Katalog.
1. Erstellen Sie in der Storefront ein Kundenkonto.
1. Gehen Sie zur Kategorie *Kategorie 1 > Kategorie 2* . Es werden nur die Produkte angezeigt, die den [!UICONTROL Shared Catalog] zugewiesen wurden.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]** und generieren Sie eine neue Sitemap.
1. Öffnen Sie die `sitemap.xml` in der Storefront.
1. Suchen Sie nach den Produkten, die Sie nicht in den [!UICONTROL Shared Catalog] eingeschlossen haben.

<u>Erwartete Ergebnisse</u>:

Die Sitemap enthält keine Links zu Produkten und Kategorien, die nicht der [!UICONTROL Shared Catalog] zugewiesen sind.

<u>Tatsächliche Ergebnisse</u>:

Die Sitemap enthält Links zu Produkten und Kategorien, die nicht der [!UICONTROL Shared Catalog] zugewiesen sind.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.