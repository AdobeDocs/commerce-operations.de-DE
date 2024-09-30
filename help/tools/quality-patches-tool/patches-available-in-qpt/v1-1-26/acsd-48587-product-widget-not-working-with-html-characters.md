---
title: "ACSD-48587: Produkt-Widget funktioniert nicht mit SKUs, die HTML-Zeichen enthalten."
description: Wenden Sie den Patch ACSD-48587 an, um das Adobe Commerce-Problem zu beheben, bei dem HTML-Sonderzeichen in den Übereinstimmungsregeln für Produkte-Widgets verhindern, dass sie übereinstimmende Produkte anzeigen.
feature: Admin Workspace, CMS, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48587: Produkt-Widget funktioniert nicht mit SKUs mit HTML-Zeichen

Der Patch ACSD-48587 behebt das Problem, dass HTML-Sonderzeichen in den Übereinstimmungsregeln für Produkte-Widgets verhindern, dass sie übereinstimmende Produkte anzeigen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID lautet ACSD-48587. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produkt-Widget funktioniert nicht mit SKUs, die *&quot;&amp;&quot;* -Symbole enthalten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt, das *&quot;&amp;&quot;* in der SKU enthält (z. B. s000&amp;01).
1. Bearbeiten Sie den Inhalt einer CMS-Seite im *Seitenaufbau*.
1. Hinzufügen eines Produkt-Widgets.
1. Bearbeiten Sie das Widget und legen Sie **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]** fest.
1. Geben Sie die SKU ein, die *&quot;&amp;&quot;* enthält, in das Feld Produkt-SKUs.
1. Speichern Sie den Inhalt und die CMS-Seite.
1. Überprüfen Sie den Inhalt der *CMS-Seite* für die Vorschau des *Seitenaufbaus* und des Produkt-Storefront.

<u>Erwartete Ergebnisse</u>:

Das Produkt mit &quot;*&quot;&amp;&quot;* in der SKU wird in der Seitenaufbau-Vorschau und auf der Storefront angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt mit &quot;*&quot;&amp;&quot;* in der SKU wird nicht in der Seitenaufbau-Vorschau angezeigt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
