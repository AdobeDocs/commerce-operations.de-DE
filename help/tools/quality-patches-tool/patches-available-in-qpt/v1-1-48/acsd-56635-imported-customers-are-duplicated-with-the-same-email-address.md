---
title: 'ACSD-56635: Importierte Kunden werden dupliziert, wenn die Kontofreigabe auf festgelegt ist [!DNL Global]'
description: Wenden Sie den Patch ACSD-56635 an, um das Adobe Commerce-Problem zu beheben, bei dem der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn der Import mit der Einstellung „Kontofreigabe“ auf [!DNL Global] festgelegt wird.
feature: Customers, Attributes
role: Admin, Developer
exl-id: 73abec4a-03b0-45d4-bfc6-f3c6862e733c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-56635: Importierte Kunden werden mit derselben E-Mail-Adresse dupliziert, wenn die Kontofreigabe auf [!DNL Global] festgelegt ist

Mit dem Patch ACSD-56635 wird das Problem behoben, dass der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn der Import verwendet wird und die Kontofreigabe auf [!DNL Global] festgelegt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 installiert ist. Die Patch-ID ist ACSD-56635. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Importierte Kunden werden mit derselben E-Mail-Adresse dupliziert, wenn die Kontofreigabe auf [!DNL Global] festgelegt ist.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie im Adobe Commerce-**[!UICONTROL Admin]** (2.4-Developer B2B) zu **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Stellen Sie die *[!UICONTROL Share Customer Accounts]* auf *[!DNL Global]* ein.
1. Erstellen mehrerer Websites und Stores:

   * WS1 > S11, S12 > SW111, SW122
   * ws2 > s21, s22 > sw211, sw212

1. Erstellen Sie einen neuen Kunden unter der *Haupt-Website* von der Administratorin bzw. dem Administrator mit der als <adb@yormail.com> verwendeten E-Mail-Adresse.
1. Navigieren Sie unter **[!UICONTROL Admin]** zu **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Wählen Sie **[!UICONTROL Customer Entity Type]** als *[!UICONTROL Customers Main File]* aus.
1. Verwenden Sie dieselbe E-Mail-Adresse wie <adb@yormail.com> auf einer anderen Website, z. B. ws1. Siehe die CSV-Beispieldatei customer.csv unten.
1. Schließen Sie den Import ab, um den neuen Benutzer anzuzeigen, der unter der *ws1*-Website mit derselben E-Mail-Adresse erstellt wurde.

customer.csv-Inhalt:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Erwartete Ergebnisse</u>:

Der importierte Kunde mit derselben E-Mail-Adresse wird aktualisiert, anstatt dupliziert zu werden.

<u>Tatsächliche Ergebnisse</u>:

Bei Verwendung des Kundenimports werden doppelte Kunden mit derselben E-Mail-Adresse erstellt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
