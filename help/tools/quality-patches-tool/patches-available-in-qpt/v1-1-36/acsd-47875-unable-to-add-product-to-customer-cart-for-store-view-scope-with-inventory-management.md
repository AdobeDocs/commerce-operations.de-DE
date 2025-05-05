---
title: 'ACSD-47875: Produkt kann nicht zum Warenkorb hinzugefügt werden, um den Umfang der Store-Ansicht bei der Bestandsverwaltung zu ermitteln.'
description: Wenden Sie den Patch ACSD-47875 an, um das Adobe Commerce-Problem zu beheben, dass ein Produkt nicht von Admin aus zu einem Warenkorb hinzugefügt werden kann, um einen bestimmten Bereich von Store-Ansichten bei der Bestandsverwaltung zu verwenden.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: 10862e09-d561-4ed5-ab6f-cf002fae6850
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ACSD-47875: Produkt kann nicht zum Warenkorb hinzugefügt werden, um den Umfang der Store-Ansicht bei der Bestandsverwaltung zu ermitteln.

Mit dem Patch ACSD-47875 wird das Problem behoben, dass ein Produkt für einen bestimmten Store-Ansichtsumfang bei der Bestandsverwaltung nicht vom Administrator zu einem Kundenwagen hinzugefügt werden kann. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.36 installiert ist. Die Patch-ID ist ACSD-47875. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Admin-Benutzer können mit der Funktion &quot;**[!UICONTROL Manage Shopping Cart]**&quot; in der Admin-Liste für einen bestimmten Store-Ansichtsumfang bei installiertem MSI kein Produkt zum Warenkorb hinzufügen.

<u>Voraussetzungen</u>:

[!DNL Adobe Commerce Inventory Management (MSI)] Module sind installiert und aktiviert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Website, einen Store und eine Store-Ansicht.
1. Erstellen Sie eine andere zusätzliche Quelle als *Standard*.
1. Erstellen Sie ein neues Lager und weisen Sie es der neuen Website und der neuen Quelle zu.
1. Erstellen Sie einen neuen Kunden für die neue Website.
1. Weisen Sie der neuen Website nur ein Produkt zu, und heben Sie die Zuweisung zur Standardwebsite auf.

   * Weisen Sie die neue Quelle zu und legen Sie *Menge über 0* für die neue Quelle und *0* für die Standardquelle fest.

1. Navigieren Sie zur Seite **[!UICONTROL Customer Edit]** im Admin-Bereich. Klicken Sie auf **[!UICONTROL Manage Shopping Cart]**.
1. Ändern Sie den Bereich für die Store-Ansicht in die neue Store-Ansicht.
1. Gehen Sie zum Abschnitt **[!UICONTROL Products]** und suchen Sie nach dem Produkt.
1. Wählen Sie das Produkt aus und klicken Sie auf **[!UICONTROL Add selections to my cart]**.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird dem Warenkorb hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

* Es wird der folgende Fehler ausgegeben: *Das Produkt, das Sie hinzufügen möchten, ist nicht verfügbar.*
* Das Produkt wird nicht zum Warenkorb hinzugefügt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
