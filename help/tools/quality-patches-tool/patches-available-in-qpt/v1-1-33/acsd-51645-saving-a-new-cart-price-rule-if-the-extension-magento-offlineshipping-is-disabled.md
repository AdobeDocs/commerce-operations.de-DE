---
title: 'ACSD-51645: Speichern einer neuen Warenkorbpreisregel, wenn die Erweiterung Magento_OfflineShipping deaktiviert ist'
description: Wenden Sie den Patch ACSD-51645 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Speichern einer neuen Warenkorbpreisregel ein Fehler auftritt, wenn die Erweiterung Magento_OfflineShipping deaktiviert ist.
exl-id: ce747ae4-6d2f-41c0-ba75-7da72be359c7
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51645: Speichern einer neuen Warenkorbpreisregel, wenn die Erweiterung Magento_OfflineShipping deaktiviert ist

Der Patch ACSD-51645 behebt das Problem, dass beim Speichern einer neuen Warenkorbpreisregel ein Fehler auftritt, wenn die Erweiterung Magento_OfflineShipping deaktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51645. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Erhalten Sie beim Speichern einer neuen Warenkorbpreisregel einen Fehler, wenn die Erweiterung `Magento_OfflineShipping` deaktiviert ist.

<u>Zu reproduzierende Schritte</u>:

1. Deaktivieren Sie das Modul `Magento_OfflineShipping` .
1. Melden Sie sich bei **Admin** an.
1. Gehen Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. Erstellen Sie eine neue **[!UICONTROL Cart Price Rule]**.
1. Füllen Sie die erforderlichen Felder aus.
1. Speichern Sie die **[!UICONTROL Cart Price Rule]**.

<u>Erwartete Ergebnisse</u>:

Die Preisregel für Warenkorb wurde erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt auf:
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) im [!DNL Quality Patches Tool] -Handbuch.
