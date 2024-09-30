---
title: "ACSD-51984: Nicht aktiviert [!UICONTROL Use Default Value] und nicht standardmäßige Produktfeldwerte werden nicht für die zweite Website-, Store- und Store-Ansicht gespeichert."
description: Wenden Sie den Patch ACSD-51984 an, um das Adobe Commerce-Problem zu beheben, bei dem die deaktivierten Werte für [!UICONTROL Use Default Value] und die nicht standardmäßigen Produktfeldwerte nicht für die zweite Website-, Store- und Store-Ansicht gespeichert werden.
feature: Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# ACSD-51984: Nicht angekreuzte *[!UICONTROL Use Default Value]* und nicht standardmäßige Produktfeldwerte werden nicht gespeichert

>[!NOTE]
>
>Dieser Patch ist veraltet und wurde durch den Patch [ACSD-54776](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-39/acsd-54776-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) ersetzt, der in der QPT-Version 1.1.39 hinzugefügt wurde.

Der Patch ACSD-51984 behebt das Problem, dass die deaktivierten Werte für **[!UICONTROL Use Default Value]** und nicht standardmäßige Produktfeldwerte nicht für die zweite Website-, Store- und Store-Ansicht gespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.35 installiert ist. Die Patch-ID ist ACSD-51984. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nicht aktivierte Werte für *[!UICONTROL Use Default Value]* und nicht standardmäßige Produktfelder werden nicht für die zweite Website-, Store- und Store-Ansicht gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zum Backend und navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** und erstellen Sie eine neue Website-, Store- und Store-Ansicht.
1. Wechseln Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, erstellen Sie ein einfaches Produkt, speichern Sie es und weisen Sie das Produkt beiden Websites aus dem **[!UICONTROL Product in Websites]** zu.
1. Ändern Sie den Umfang in die neu erstellte Store-Ansicht aus Schritt 2.
1. Gehen Sie zu **[!UICONTROL Search Engine Optimization]** und deaktivieren Sie die Kontrollkästchen **[!UICONTROL Use Default Value]** für [!UICONTROL Meta Title], [!UICONTROL Meta Keywords] und [!UICONTROL Meta Description].
1. Reinigen Sie den Text aus den Feldern: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* und *[!UICONTROL Meta Description]* und klicken Sie auf **[!UICONTROL Save]**.
1. Wechseln Sie erneut zu **[!UICONTROL Search Engine Optimization]** .

<u>Erwartete Ergebnisse</u>

Die Werte für die Felder und die Kontrollkästchen werden gespeichert.

<u>Tatsächliche Ergebnisse</u>

Die Werte für die Felder und die Kontrollkästchen werden nicht gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](</help/tools/quality-patches-tool/usage.md>) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.