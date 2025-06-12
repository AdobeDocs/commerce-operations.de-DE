---
title: 'ACSD-60632: Bei jedem Bestellversuch gespeicherte Adresse'
description: Wenden Sie den Patch ACSD-60632 an, um das Adobe Commerce-Problem zu beheben, bei dem bei jedem Bestellplatzierungsversuch eine neue Adresse gespeichert wird, unabhängig davon, ob die Bestellung erfolgreich erstellt wurde oder nicht.
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632: Bei jedem Bestellversuch gespeicherte Adresse

Mit dem Patch ACSD-60632 wird das Problem behoben, dass bei jedem Bestellplatzierungsversuch eine neue Adresse gespeichert wird, unabhängig davon, ob die Bestellung erfolgreich erstellt wurde oder nicht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 installiert ist. Die Patch-ID ist ACSD-60632. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei jedem Versuch einer Bestellplatzierung wird im System ein neuer Adresseintrag gespeichert, unabhängig davon, ob die Bestellung erfolgreich erstellt wurde.

<u>Schritte zur Reproduktion</u>:

1. **[!DNL PayPal Payflow Link]** Zahlungsmethode aktivieren:
   * Auf einem lokalen Computer kann das System ohne eine echte IP keine API-Aufrufe von [!DNL PayPal Payflow Link] empfangen.
1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie einen registrierten Kunden ohne Adresse.
1. Fügen Sie das Produkt zum Warenkorb hinzu.
1. Zur Kasse gehen.
1. Geben Sie die Adresse ein. Stellen Sie sicher, dass bei diesem Schritt die erste Adresse erstellt wird.
1. Wählen Sie auf der Seite *[!UICONTROL Review and Payments]* das Optionsfeld **[!UICONTROL Credit Card (Payflow Link)]** aus.
1. Klicken Sie auf **[!UICONTROL Continue]**:
   * Die Checkout-Seite kehrt zum *[!UICONTROL Review and Payments]* Schritt mit der vorausgefüllten Adresse und der erwarteten Fehlermeldung zurück.
1. Wählen Sie erneut *[!UICONTROL Credit Card (Payflow Link)]* Optionsfeld aus.
1. Klicken Sie auf **[!UICONTROL Continue]**.

<u>Erwartete Ergebnisse</u>:

Beim zweiten Platzierungsversuch wird keine neue Adresse erstellt.

<u>Tatsächliche Ergebnisse</u>:

Nach jedem Bestell-Platzierungsversuch wird eine neue Adresse erstellt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=de) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
