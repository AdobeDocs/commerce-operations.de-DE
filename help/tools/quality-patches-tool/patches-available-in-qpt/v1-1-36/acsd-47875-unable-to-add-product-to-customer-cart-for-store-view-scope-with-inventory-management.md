---
title: "ACSD-47875: Kann kein Produkt zum Warenkorb hinzufügen, um den Umfang der Store-Ansicht mit Lagerbestandsverwaltung zu ermitteln"
description: Wenden Sie den Patch ACSD-47875 an, um das Adobe Commerce-Problem zu beheben, bei dem ein Produkt von Admin für einen bestimmten Umfang mit Lagerbestandsverwaltung nicht zu einem Kundenkorb hinzugefügt werden kann.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-47875: Produkt kann nicht zum Warenkorb hinzugefügt werden, um den Umfang der Store-Ansicht mit Lagerbestandsverwaltung zu ermitteln.

Der Patch ACSD-47875 behebt das Problem, dass ein Produkt vom Administrator für einen bestimmten Umfang mit Lagerbestandsverwaltung nicht zu einem Kundenkorb hinzugefügt werden kann. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.36 installiert ist. Die Patch-ID ist ACSD-47875. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Admin-Benutzer können ein Produkt nicht mit der Funktion &quot;**[!UICONTROL Manage Shopping Cart]**&quot;im Admin für einen bestimmten Umfang der Store-Ansicht mit installierter MSI zum Warenkorb hinzufügen.

<u>Voraussetzungen</u>:

[!DNL Adobe Commerce Inventory Management (MSI)] -Module werden installiert und aktiviert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine Website, einen Store und eine Store-Ansicht.
1. Erstellen Sie eine zusätzliche Quelle außer *Standard*.
1. Erstellen Sie ein neues Lager und weisen Sie es der neuen Website und der neuen Quelle zu.
1. Erstellen Sie einen neuen Kunden für die neue Website.
1. Weisen Sie ein Produkt nur der neuen Website zu. Heben Sie die Zuweisung von der Standardwebsite auf.

   * Weisen Sie die neue Quelle zu und legen Sie die Menge *über 0* für die neue Quelle und die Menge *0* für die Standardquelle fest.

1. Rufen Sie die Seite &quot;**[!UICONTROL Customer Edit]**&quot;im Admin auf. Klicken Sie auf **[!UICONTROL Manage Shopping Cart]**.
1. Ändern Sie den Umfang der Store-Ansicht in die neue Store-Ansicht.
1. Gehen Sie zum Abschnitt &quot;**[!UICONTROL Products]**&quot;und suchen Sie nach dem Produkt.
1. Wählen Sie das Produkt aus und klicken Sie auf **[!UICONTROL Add selections to my cart]**.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird dem Warenkorb hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

* Der folgende Fehler wird ausgegeben: *Produkt, das Sie hinzufügen möchten, ist nicht verfügbar.*
* Das Produkt wird nicht zum Warenkorb hinzugefügt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
