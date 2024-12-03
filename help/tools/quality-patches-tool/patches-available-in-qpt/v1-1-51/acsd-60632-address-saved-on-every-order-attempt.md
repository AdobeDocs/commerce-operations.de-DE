---
title: 'ACSD-60632: Bei jedem Bestellversuch gespeicherte Adresse'
description: Wenden Sie den Patch ACSD-60632 an, um das Adobe Commerce-Problem zu beheben, bei dem bei jedem Bestellplatzierungsversuch eine neue Adresse gespeichert wird, unabhängig davon, ob die Bestellung erfolgreich erstellt wurde oder nicht.
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632: Bei jedem Bestellversuch gespeicherte Adresse

Der Patch ACSD-60632 behebt das Problem, dass bei jedem Bestellplatzierungsversuch eine neue Adresse gespeichert wird, unabhängig davon, ob die Bestellung erfolgreich erstellt wurde oder nicht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 installiert ist. Die Patch-ID ist ACSD-60632. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Jedes Mal, wenn eine Bestellplatzierung versucht wird, wird ein neuer Adresseintrag im System gespeichert, unabhängig davon, ob die Bestellung erfolgreich erstellt wurde.

<u>Zu reproduzierende Schritte</u>:

1. **[!DNL PayPal Payflow Link]** Zahlungsmethode aktivieren:
   * Auf einem lokalen Computer kann das System keine API-Aufrufe von [!DNL PayPal Payflow Link] ohne echte IP-Adresse empfangen.
1. Erstellen Sie ein einfaches Produkt.
1. Erstellen Sie einen registrierten Kunden ohne Adresse.
1. Fügen Sie das Produkt zum Warenkorb hinzu.
1. Fahren Sie mit dem Checkout fort.
1. Füllen Sie die Adresse aus. Stellen Sie sicher, dass in diesem Schritt die erste Adresse erstellt wurde.
1. Wählen Sie auf der Seite *[!UICONTROL Review and Payments]* das Optionsfeld **[!UICONTROL Credit Card (Payflow Link)]** aus.
1. Klicken Sie auf **[!UICONTROL Continue]**:
   * Die Checkout-Seite kehrt zum Schritt *[!UICONTROL Review and Payments]* mit der vorausgefüllten Adresse und der erwarteten Fehlermeldung zurück.
1. Wählen Sie erneut das Optionsfeld *[!UICONTROL Credit Card (Payflow Link)]* aus.
1. Klicken Sie auf **[!UICONTROL Continue]**.

<u>Erwartete Ergebnisse</u>:

Beim zweiten Bestellplatzierungsversuch wird keine neue Adresse erstellt.

<u>Tatsächliche Ergebnisse</u>:

Nach jedem Bestellplatzierungsversuch wird eine neue Adresse erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
