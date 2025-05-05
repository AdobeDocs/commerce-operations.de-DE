---
title: 'ACSD-51240: Hochgeladene Datei fehlt bei der Registrierung über das Unternehmensregistrierungsformular'
description: Wenden Sie den Patch ACSD-51240 an, um das Adobe Commerce-Problem zu beheben, bei dem die hochgeladene Datei bei der Registrierung über das Unternehmensregistrierungsformular fehlt.
exl-id: 78e339d6-435e-4856-9f57-98bb955d093c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51240: Hochgeladene Datei fehlt bei der Registrierung über das Unternehmensregistrierungsformular

>[!NOTE]
>
>Dieser Patch wurde durch [ACSD-55628](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md) ersetzt.

Mit dem Patch ACSD-51240 wird das Problem behoben, dass die hochgeladene Datei bei der Registrierung über das Unternehmensregistrierungsformular fehlt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 installiert ist. Die Patch-ID ist ACSD-51240. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de>). Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Problem

Hochgeladene Datei fehlt bei der Registrierung über das Unternehmensregistrierungsformular.

<u>Schritte zur Reproduktion</u>:

1. **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *Ja*.
1. Erstellen Sie ein neues Kundenattribut **[!UICONTROL File]** Typs, legen Sie **[!UICONTROL Show in StoreFront]** = *Ja* fest und wählen Sie **[!UICONTROL all forms]** aus.
1. Erstellen Sie ein neues Unternehmen in der Storefront und laden Sie ein Bild für das neue Attribut hoch.
Öffnen Sie das Unternehmen und den Admin-Benutzer in der Storefront.

<u>Erwartete Ergebnisse</u>:

Die hochgeladene Datei wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die hochgeladene Datei wird weder auf der Firmenseite noch auf der Admin-Kundenseite in der [!UICONTROL Commerce Admin] angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
