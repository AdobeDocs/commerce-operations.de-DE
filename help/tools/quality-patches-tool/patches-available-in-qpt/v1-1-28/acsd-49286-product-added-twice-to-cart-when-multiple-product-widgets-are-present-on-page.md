---
title: 'ACSD-49286: Produkt zweimal zum Warenkorb hinzugefügt, wenn mehrere Produkt-Widgets vorhanden sind'
description: Wenden Sie den Patch ACSD-49286 an, um das Adobe Commerce-Problem zu beheben, bei dem das Produkt zweimal zum Warenkorb hinzugefügt wird, wenn mehrere Produkt-Widgets auf der Seite vorhanden sind.
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
exl-id: 03fdaafe-5566-4b75-a0eb-e0cba3dad3e7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286: Produkt zweimal zum Warenkorb hinzugefügt, wenn mehrere Produkt-Widgets vorhanden sind

Der Patch ACSD-49286 behebt das Problem, dass das Produkt zweimal zum Warenkorb hinzugefügt wird, wenn mehrere Produkt-Widgets auf der Seite vorhanden sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID lautet ACSD-49286. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Produkt wird einem Warenkorb zweimal hinzugefügt, wenn auf der Seite mehrere Produkt-Widgets vorhanden sind.

<u>Zu reproduzierende Schritte</u>:

1. Melden Sie sich bei admin an und gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Klicken Sie im Inhaltsabschnitt auf **[!UICONTROL Edit]** mit [!DNL Page Builder].
1. Fügen Sie **[!UICONTROL Content]** zwei Zeilenelemente hinzu.
1. Fügen Sie Produkte in beide Zeilenelemente ein.
1. Legen Sie in der ersten Zeile das Produkterscheinungsbild auf &quot;[!UICONTROL Product Grid]&quot;fest und wählen Sie eine beliebige anzuzeigende Kategorie aus.
1. Legen Sie in der zweiten Zeile das Produkterscheinungsbild auf &quot;[!UICONTROL Product Carousel]&quot;fest und wählen Sie eine andere anzuzeigende Kategorie aus.
1. Gehen Sie zur Storefront **[!UICONTROL Home Page]** und fügen Sie ein Produkt aus dem Produktraster hinzu.
1. Fügen Sie ein weiteres Produkt aus [!UICONTROL Product Carousel] hinzu.

<u>Erwartete Ergebnisse</u>:

Die Produktmenge sollte sich nach dem Hinzufügen eines Produkts zum Warenkorb von [!UICONTROL Product Grid] nicht verdoppeln.

<u>Tatsächliche Ergebnisse</u>:

Die Produktmenge verdoppelt sich nach dem Hinzufügen eines Produkts zum Warenkorb von [!UICONTROL Product Grid].

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure. 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
