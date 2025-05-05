---
title: 'ACSD-60673: [!UICONTROL Cart Price Rule] Problem behoben für mehrere Zahlungsmethoden an der Kasse'
description: Wenden Sie den Patch ACSD-60673 an, um das Adobe Commerce-Problem zu beheben, bei dem die Rabatte von einem [!UICONTROL Cart Price Rule], der eine Zahlungsmethode-Bedingung verwendet, nicht immer in den Gesamtwerten aufgeführt sind.
feature: Price Rules
role: Admin, Developer
exl-id: 2fe27959-5e5f-4d25-9f56-b0f8319fd562
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673: [!UICONTROL Cart Price Rule] Problem behoben für mehrere Zahlungsmethoden an der Kasse

Mit dem Patch ACSD-60673 wird das Problem behoben, dass die Rabatte von einem [!UICONTROL Cart Price Rule], der eine Zahlungsmethode-Bedingung verwendet, nicht immer in den Gesamtwerten aufgeführt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-60673. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die [!UICONTROL Cart Price Rule] für mehrere Zahlungsmethoden an der Kasse gilt nicht korrekt für die spezifische Zahlungsmethode.

<u>Voraussetzungen</u>

Stellen Sie sicher, dass in der **[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]** und **[!UICONTROL Bank Transfer]** aktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. **[!UICONTROL Multiple Payment Methods]** aktivieren.
1. Erstellen Sie eine *[!UICONTROL Cart Price Rule]*.
   * **[!UICONTROL Conditions]** festlegen : Zahlungsmethode auf **[!UICONTROL Money Order]** (oder Banküberweisung)
   * Wählen Sie **[!UICONTROL Actions]** = *25%* Rabatt auf alle Produkte
1. Erstellen eines virtuellen Produkts.
1. Um ein neues Angebot und *[!UICONTROL Status]* zu kopieren, gehen Sie zur Storefront und löschen Sie Cookies.
1. Fügen Sie das virtuelle Produkt zum Warenkorb hinzu.
1. Fahren Sie mit *Checkout* fort.
1. Klicken Sie auf die Zahlungsmethode, die in der *[!UICONTROL Cart Price Rule]* definiert wurde.
1. Aktualisieren Sie Ihre *[!UICONTROL Billing Address]*.
1. Stellen Sie sicher, dass der Rabatt im Gesamtbetrag sichtbar ist.
1. Klicken Sie auf das Kontrollkästchen, um die Zahlungsmethode zu ändern.
1. Überprüfen Sie, ob der Rabatt sichtbar ist.

<u>Erwartete Ergebnisse</u>:

Der Rabatt wird in &quot;*&quot; angezeigt* nachdem Sie auf das Kontrollkästchen geklickt haben, um zu einer anwendbaren Zahlungsmethode zu wechseln.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt ist in den &quot;*&quot; nicht*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
