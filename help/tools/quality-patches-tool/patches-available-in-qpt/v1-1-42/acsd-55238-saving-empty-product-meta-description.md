---
title: 'ACSD-55238: Leere Beschreibung der Produktmetadaten speichern'
description: Wenden Sie den Patch ACSD-55238 an, um das Adobe Commerce-Problem zu beheben, bei dem eine Produktbeschreibung, die einen von oder  [!DNL Page Builder]  anderen HTML-Editor generierten HTML-Code enthält, immer in der Metabeschreibung angezeigt wird und es keine Möglichkeit gibt, sie auf „leer“ festzulegen.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 39ccf1bb-a71a-47a0-b252-e6331e2df9b0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-55238: Leere Beschreibung der Produktmetadaten speichern

Mit dem Patch ACSD-55238 wird das Problem behoben, dass eine Produktbeschreibung mit einem von einem HTML-Editor generierten HTML-Code immer in der Meta-Beschreibung angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 installiert ist. Die Patch-ID ist ACSD-55238. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine Produktbeschreibung, die HTML-Code enthält, der von [!DNL Page Builder] oder einem anderen HTML-Editor generiert wurde, wird immer in der Metabeschreibung angezeigt, und es gibt keine Möglichkeit, sie auf „leer“ festzulegen.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** und erstellen Sie einen neuen Block mit beliebigen Inhalten.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** und erstellen Sie ein neues Produkt. Legen Sie die Meta-Beschreibung auf „leer“ fest.
1. Fügen Sie den oben erstellten Block mithilfe von *[!DNL Page Builder]* auf der Registerkarte *[!UICONTROL Content]* hinzu und speichern Sie das Produkt.
1. Öffnen Sie das Produkt in der Storefront und überprüfen Sie die `meta name = "description"` seines Dokumentelements.

<u>Erwartete Ergebnisse</u>:

Die Metabeschreibung ist leer.

<u>Tatsächliche Ergebnisse</u>:

Wenn ein Produkt einen -Block in der Beschreibung enthält, wird er für die Beschreibung der Produktmeta verwendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
