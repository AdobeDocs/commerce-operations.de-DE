---
title: "ACSD-49839: Freigegebene Katalogpreisstruktur und -struktur lösen einen Fehler aus"
description: Wenden Sie den Patch ACSD-49839 an, um das Adobe Commerce-Problem zu beheben, bei dem die gemeinsame Katalogpreisstruktur und -struktur einen Fehler im Admin auslöst, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU aufweisen.
feature: Admin Workspace, Catalog Management, Categories
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49839: Gemeinsame Katalogpreisstruktur und -struktur lösen einen Fehler aus

Der Patch ACSD-49839 behebt das Problem, dass die gemeinsame Katalogpreisstruktur und -struktur einen Fehler im Admin ausgibt, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU haben. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID lautet ACSD-49839. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die freigegebene Katalogpreisstruktur und -struktur gibt im Administrator einen Fehler aus, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU aufweisen.

<u>Zu reproduzierende Schritte</u>:

1. Legen Sie einige Produkt-SKUs mit einem Sonderzeichen fest, d. h. doppelte Anführungszeichen wie:
   *[Produkt&quot;12, Produkt&quot;14, Produkt&quot;15]*.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]** (z. B. *[Freigegebenen Katalog testen]*).
1. Weisen Sie alle **[!UICONTROL Products and Categories]** > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]** zu.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]**.
1. Markieren Sie *[!UICONTROL Root Catalog]* , um alle Kategorien und Produkte auszuwählen.
1. Beobachten Sie die AJAX Anforderungen im Netzwerkbereich.

<u>Erwartete Ergebnisse</u>:

Die gemeinsame Katalogpreisstruktur und -struktur gibt keinen Fehler im Admin aus, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU haben.

<u>Tatsächliche Ergebnisse</u>:

Die gemeinsame Katalogpreisstruktur und -struktur gibt im Admin einen Fehler aus, wenn Produkte einfache oder doppelte Anführungszeichen in der SKU haben.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
