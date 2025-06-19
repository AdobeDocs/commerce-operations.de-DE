---
title: 'ACSD-51645: Speichern einer neuen Warenkorb-Preisregel, wenn die Erweiterung Magento_OfflineShipping deaktiviert ist'
description: Wenden Sie den Patch ACSD-51645 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Speichern einer neuen Warenkorb-Preisregel ein Fehler auftritt, wenn die Erweiterung Magento_OfflineShipping deaktiviert ist.
exl-id: ce747ae4-6d2f-41c0-ba75-7da72be359c7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51645: Speichern einer neuen Warenkorb-Preisregel, wenn die Erweiterung Magento_OfflineShipping deaktiviert ist

Der Patch ACSD-51645 behebt das Problem, dass beim Speichern einer neuen Warenkorb-Preisregel ein Fehler auftritt, wenn die Erweiterung Magento_OfflineShipping deaktiviert ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51645. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Es wird ein Fehler beim Speichern einer neuen Warenkorb-Preisregel angezeigt, wenn die `Magento_OfflineShipping` deaktiviert ist.

<u>Schritte zur Reproduktion</u>:

1. Deaktivieren Sie das `Magento_OfflineShipping`.
1. Melden Sie sich bei &quot;**&quot;**.
1. Navigieren Sie zu **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. Erstellen Sie eine neue **[!UICONTROL Cart Price Rule]**.
1. Füllen Sie die erforderlichen Felder aus.
1. Speichern Sie die **[!UICONTROL Cart Price Rule]**.

<u>Erwartete Ergebnisse</u>:

Die Warenkorb-Preisregel wurde erfolgreich gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt auf:
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>) im [!DNL Quality Patches Tool].
