---
title: "ACSD-50276: Das Formular zur Kundenregistrierung funktioniert nicht auf der Storefront, wenn das Kundenattribut mit Mehrfachauswahl erstellt wird."
description: Wenden Sie den Patch ACSD-50276 an, um das Adobe Commerce-Problem zu beheben, bei dem das Anmeldeformular für Kunden auf der Storefront nicht funktioniert, wenn ein Kundenattribut mit mehreren Auswahlen erstellt wird.
feature: Attributes, Storefront
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-50276: Das Formular zur Kundenregistrierung funktioniert nicht auf der Storefront, wenn das Kundenattribut mit Mehrfachauswahl erstellt wird

Der Patch ACSD-50276 behebt das Problem, dass das Formular zur Kundenregistrierung auf der Storefront nicht funktioniert, wenn ein Kundenattribut mit Mehrfachauswahl erstellt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-50276. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Formular zur Kundenregistrierung funktioniert nicht auf der Storefront, wenn ein Kundenattribut mit mehreren Auswahlen erstellt wird.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein neues Kundenattribut mit Mehrfachauswahl mit den folgenden Einstellungen:

   * *[!UICONTROL Required = Yes]*
   * *[!UICONTROL Show on storefront = Yes]*, wählen Sie *[!UICONTROL Customer registration form]* aus.

1. Öffnen Sie das Formular zur Kundenregistrierung auf der Storefront.

<u>Erwartete Ergebnisse</u>:

Das Formular zur Kundenregistrierung wurde erfolgreich geladen.

<u>Tatsächliche Ergebnisse</u>:

* Das Formular zur Kundenregistrierung wird nicht geladen.
* Der folgende Fehler wird protokolliert:

  ```PHP
  report. CRITICAL: Exception: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in vendor/magento/module-custom-attribute-management/Block/Form/Renderer/Multiselect.php
  ```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
