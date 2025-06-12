---
title: 'ACSD-47004: MwSt. nicht auf Rechnungsadresse ohne MwSt.-Kennung erhoben'
description: Wenden Sie den Patch ACSD-47004 an, um das Adobe Commerce-Problem zu beheben, bei dem auf eine Rechnungsadresse ohne MwSt.-Kennung keine MwSt. angewendet wird.
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
exl-id: 72a64937-1c04-4fc2-bc61-fd2056e24419
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 1%

---

# ACSD-47004: MwSt. nicht auf Rechnungsadresse ohne MwSt.-Kennung erhoben

Mit dem Patch ACSD-47004 wird das Problem behoben, dass keine MwSt. auf eine Rechnungsadresse ohne MwSt.-Kennung angewendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47004. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Auf eine Rechnungsadresse ohne MwSt.-Kennung wird keine MwSt. erhoben.

<u>Schritte zur Reproduktion</u>:

1. Öffnen Sie die [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** und legen Sie die **[!UICONTROL Enable Automatic Assignment to Customer Group]** auf *[!UICONTROL Yes]* fest.
1. Legen Sie verschiedene Gruppen für MwSt.-ID-Validierungen fest. Beispiel:

   ![VAT-ID-validations](/help/assets/tools/vat-id-validations.png)

1. Registrieren Sie einen neuen Kunden.
1. Eine neue Standardadresse ohne MwSt. hinzufügen. Beispiel:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Vergewissern Sie sich, dass die Gruppe des Kunden [!UICONTROL General] bleibt.
1. Bearbeiten Sie diese Adresse und fügen Sie eine gültige MwSt.-Nummer hinzu:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Stellen Sie sicher, dass die Gruppe des Kunden auf [!UICONTROL Retailer] geändert wurde.
1. Bearbeiten Sie die Adresse und entfernen Sie die MwSt.-Nummer:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Erwartete Ergebnisse</u>:

Die Kundengruppe wird automatisch in die [!UICONTROL General] geändert.

<u>Tatsächliche Ergebnisse</u>:

Die Kundengruppe wird nicht automatisch in die [!UICONTROL General] geändert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
