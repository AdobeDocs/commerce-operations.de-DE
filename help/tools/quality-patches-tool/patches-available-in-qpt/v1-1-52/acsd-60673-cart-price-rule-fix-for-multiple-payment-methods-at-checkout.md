---
title: "ACSD-60673: [!UICONTROL Cart Price Rule] Problem behoben für mehrere Zahlungsmethoden beim Checkout"
description: Wenden Sie den Patch ACSD-60673 an, um das Adobe Commerce-Problem zu beheben, bei dem die Rabatte von einem [!UICONTROL Cart Price Rule], der eine Zahlungsmethodenbedingung verwendet, nicht immer in den Gesamtwerten aufgeführt sind.
feature: Price Rules
role: Admin, Developer
source-git-commit: 9334b0bb7aa32cd14622c6dcef799dffe7e35fdc
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673: [!UICONTROL Cart Price Rule] Problem behoben für mehrere Zahlungsmethoden beim Checkout

Der Patch ACSD-60673 behebt das Problem, dass die Rabatte von einem [!UICONTROL Cart Price Rule], der eine Zahlungsmethode-Bedingung verwendet, nicht immer in der Gesamtsumme aufgeführt sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 installiert ist. Die Patch-ID ist ACSD-60673. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die [!UICONTROL Cart Price Rule] für mehrere Zahlungsmethoden beim Checkout gilt nicht ordnungsgemäß für die jeweilige Zahlungsmethode.

<u>Voraussetzungen</u>

Stellen Sie sicher, dass in den Optionen **[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]** und **[!UICONTROL Bank Transfer]** aktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie **[!UICONTROL Multiple Payment Methods]**.
1. Erstellen Sie eine *[!UICONTROL Cart Price Rule]*.
   * Setzen Sie **[!UICONTROL Conditions]** : Zahlungsmethode auf **[!UICONTROL Money Order]** (oder Banküberweisung)
   * Wählen Sie für alle Produkte den Rabatt **[!UICONTROL Actions]** = *25%*
1. Erstellen eines virtuellen Produkts.
1. Um ein frisches Angebot und einen Gastkunden *[!UICONTROL Status]* zu kopieren, gehen Sie zur Storefront und löschen Sie die Cookies.
1. Fügen Sie das virtuelle Produkt zum Warenkorb hinzu.
1. Fahren Sie mit *Checkout* fort.
1. Klicken Sie auf die Zahlungsmethode, die in der *[!UICONTROL Cart Price Rule]* definiert wurde.
1. Aktualisieren Sie Ihre *[!UICONTROL Billing Address]*.
1. Stellen Sie sicher, dass der Rabatt in der Gesamtsumme sichtbar ist.
1. Klicken Sie auf das Kontrollkästchen, um die Zahlungsmethode zu ändern.
1. Überprüfen Sie, ob der Rabatt sichtbar ist.

<u>Erwartete Ergebnisse</u>:

Der Rabatt ist in *Gesamtsummen* sichtbar, nachdem auf das Kontrollkästchen geklickt wurde, um zu einer anwendbaren Zahlungsmethode zu wechseln.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt ist nicht in den *Gesamtwerten* sichtbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
