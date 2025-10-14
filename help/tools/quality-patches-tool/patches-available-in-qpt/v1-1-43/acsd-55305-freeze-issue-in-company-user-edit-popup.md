---
title: 'ACSD-55305: Popup-Einfrieren bei Bearbeitung durch Firmenbenutzer in [!UICONTROL My Account]'
description: Wenden Sie den Patch ACSD-55305 an, um das Adobe Commerce-Problem zu beheben, bei dem [!UICONTROL Edit Company User] Popup-Fenster auf der Seite [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] mit einem Lader auf dem Bildschirm einfriert.
feature: Companies, B2B
role: Admin, Developer
exl-id: eeb2b136-022f-42d5-85e2-85537f4677d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-55305: Popup-Einfrieren bei Bearbeitung durch Firmenbenutzer in [!UICONTROL My Account]

Mit dem Patch ACSD-55305 wird das Problem behoben, dass [!UICONTROL Edit Company User] Popup-Fenster auf der Seite [!UICONTROL My Account]> [!UICONTROL Company Structure] mit einem Lader auf dem Bildschirm einfriert. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 installiert ist. Die Patch-ID ist ACSD-55305. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Versuch, das Popup *[!UICONTROL Edit Company User]* auf der Seite *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* zu verwenden, tritt ein Fehler auf, da es mit einem auf dem Bildschirm angezeigten Lader einfriert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine B2B-Firma.
1. Erstellen Sie ein Attribut mit Mehrfachauswahl für Kunden.
1. Weisen Sie dem neu erstellten Attribut für den Unternehmensadministrator einen Wert zu.
1. Melden Sie sich als Unternehmensadministrator an.
1. Wechseln Sie zur [!UICONTROL account dashboard] und navigieren Sie zur **[!UICONTROL Company Structure]**.
1. Wählen Sie den Benutzer aus.
1. Klicken Sie auf **[!UICONTROL Edit Selected]**.

<u>Erwartete Ergebnisse</u>:

Das Formular-Popup wird korrekt angezeigt und bietet die Möglichkeit, Unternehmensinformationen zu bearbeiten.

<u>Tatsächliche Ergebnisse</u>:

Das Formular-Popup wird ohne Bearbeitungsmöglichkeit angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
