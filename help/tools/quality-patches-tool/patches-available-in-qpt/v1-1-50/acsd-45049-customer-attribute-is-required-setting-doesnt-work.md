---
title: 'ACSD-45049: Die Einstellung des Kundenattributs „Ist erforderlich“ funktioniert nicht gemäß dem Website-Umfang in Admin'
description: Wenden Sie den ACSD-45049-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem das Kundenattribut "[!UICONTROL Is required]" nicht ordnungsgemäß gemäß dem Website-Umfang in Admin überschrieben wird.
feature: Attributes, Customers
role: Admin, Developer
exl-id: 368af877-a3ec-431f-8f41-5d51354be571
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-45049: Die Einstellung des *[!UICONTROL Is required]* funktioniert nicht gemäß dem Website-Umfang in Admin

Mit dem Patch ACSD-45049 wird das Problem behoben, dass die Einstellung des Kundenattributs *[!UICONTROL Is required]* gemäß dem Website-Umfang in Admin nicht ordnungsgemäß funktioniert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/usage.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-45049. Beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p7 und 2.4.5 - 2.4.5-p9

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Einstellung des Kundendatenattributs funktioniert nicht ordnungsgemäß, wie im Website-Umfang in „Admin *[!UICONTROL Is required]* festgelegt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Websites.
1. Öffnen Sie **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**.
1. Erstellen Sie ein neues Attribut, setzen Sie **[!UICONTROL Is value required]** = *No*.
1. Wechseln Sie zur Standard-Website und ändern Sie **[!UICONTROL Is value required]** = *Ja*. Die andere Website hat den Standardwert.
1. Erstellen Sie aus der Admin-Liste einen neuen Kunden für die nicht standardmäßige Website.

<u>Erwartete Ergebnisse</u>:

Das Attribut ist für die nicht standardmäßige Website nicht erforderlich.

<u>Tatsächliche Ergebnisse</u>:

* Das Attribut ist für die nicht standardmäßige Website erforderlich, wenn ein Kunde in Admin erstellt wird.
* Das Attribut ist bei der Registrierung eines Kunden in der Storefront für die nicht standardmäßige Website nicht erforderlich.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
