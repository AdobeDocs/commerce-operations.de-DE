---
title: "ACSD-56635: Importierte Kunden werden dupliziert, wenn die Kontofreigabe auf [!DNL Global] festgelegt ist."
description: Wenden Sie den Patch ACSD-56635 an, um das Adobe Commerce-Problem zu beheben, bei dem der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn der Import verwendet wird und die Kontofreigabe auf  [!DNL Global] festgelegt ist.
feature: Customers, Attributes
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635: Importierte Kunden werden mit derselben E-Mail-Adresse dupliziert, wenn die Kontofreigabe auf [!DNL Global] gesetzt ist.

Der Patch ACSD-56635 behebt das Problem, dass der importierte Kunde mit derselben E-Mail-Adresse dupliziert wird, wenn der Import verwendet wird und die Kontofreigabe auf [!DNL Global] festgelegt ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48 installiert ist. Die Patch-ID ist ACSD-56635. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Importierte Kunden werden mit derselben E-Mail-Adresse dupliziert, wenn die Kontofreigabe auf [!DNL Global] festgelegt ist.

<u>Zu reproduzierende Schritte</u>:

1. Rufen Sie unter der Adobe Commerce (2.4-develop b2b) **[!UICONTROL Admin]** **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** auf.
1. Setzen Sie die Einstellung *[!UICONTROL Share Customer Accounts]* auf *[!DNL Global]*.
1. Erstellen Sie mehrere Websites und Stores:

   * ws1 > s11, s12 > sw11, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Erstellen Sie einen neuen Kunden unter der *Haupt-Website* vom Administrator mit der als <adb@yormail.com> verwendeten E-Mail-Adresse.
1. Navigieren Sie unter **[!UICONTROL Admin]** zu **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Wählen Sie **[!UICONTROL Customer Entity Type]** als *[!UICONTROL Customers Main File]* aus.
1. Verwenden Sie dieselbe E-Mail-Adresse wie <adb@yormail.com> auf einer anderen Website, z. B. ws1. Siehe Beispiel für eine CSV-Datei customer.csv im Folgenden.
1. Schließen Sie den Import ab, um den neuen Benutzer anzuzeigen, der unter der Website *ws1* erstellt wurde, und dieselbe E-Mail-Adresse anzuzeigen.

customer.csv-Inhalt:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Erwartete Ergebnisse</u>:

Der importierte Kunde mit derselben E-Mail-Adresse wird aktualisiert, anstatt dupliziert zu werden.

<u>Tatsächliche Ergebnisse</u>:

Bei Verwendung des Kundenimports werden doppelte Kunden mit derselben E-Mail-Adresse erstellt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
