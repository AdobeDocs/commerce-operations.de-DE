---
title: 'ACSD-48587: Produkt-Widget funktioniert nicht mit SKUs, die HTML-Zeichen enthalten'
description: Wenden Sie den Patch ACSD-48587 an, um das Adobe Commerce-Problem zu beheben, bei dem HTML-Sonderzeichen in den Übereinstimmungsregeln für Produkte verhindern, dass übereinstimmende Produkte angezeigt werden.
feature: Admin Workspace, CMS, Orders, Products
role: Admin
exl-id: c3e31835-03be-46b4-a080-09edf55b5b4e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48587: Produkt-Widget funktioniert nicht mit SKUs, die HTML-Zeichen enthalten

Der Patch ACSD-48587 behebt das Problem, dass HTML-Sonderzeichen in den Übereinstimmungsregeln für das Produkt-Widget verhindern, dass übereinstimmende Produkte angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48587. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
