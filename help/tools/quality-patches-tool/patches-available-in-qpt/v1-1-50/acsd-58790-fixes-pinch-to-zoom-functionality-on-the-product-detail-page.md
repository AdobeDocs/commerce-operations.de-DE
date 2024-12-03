---
title: 'ACSD-58790: Behebt die Pinch-to-Zoom-Funktion auf den Produktdetailseiten-Bildern in der Mobile-Ansicht auf [!DNL Chrome]'
description: ACSD-58790 behebt das Adobe Commerce-Problem, bei dem das Bild in der Mobile-Ansicht auf [!DNL Chrome] nicht wie erwartet vergrößert wurde.
feature: Storefront
role: Admin, Developer
exl-id: 46b324bf-c2a0-4086-87ee-96e8c4883494
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-58790: Behebt die Pinch-to-Zoom-Funktion auf den Produktdetailseiten-Bildern in der Mobile-Ansicht auf [!DNL Chrome]

Der Patch ACSD-58790 behebt das Adobe Commerce-Problem, bei dem das Bild in der mobilen Ansicht auf [!DNL Chrome] nicht wie erwartet vergrößert wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-58790. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Korrekturen der Funktion zum Zoomen durch Pinch-to-Zoom auf den Produktdetailseiten-Bildern in der Mobile-Ansicht auf [!DNL Chrome].

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein Produkt mit einem Bild.
1. Öffnen Sie das Produkt über einen [!DNL Chrome] -Browser.
1. Klicken Sie auf das Bild und vergewissern Sie sich, dass das Bild beim Doppelklick vergrößert wird.
1. Wechseln Sie mithilfe der [!DNL Chrome] -Entwicklertools zur Mobile-Ansicht.
1. Klicken Sie auf das Bild.
1. Doppeltippen Sie.

<u>Erwartete Ergebnisse</u>:

Das Bild wird beim Doppelklick vergrößert.

<u>Tatsächliche Ergebnisse</u>:

Das Bild wird beim Doppelklicken nicht vergrößert. Dieses Problem tritt in der Mobile-Ansicht speziell bei [!DNL Chrome] auf, da die Zoom-Funktion wie in [!DNL Firefox] erwartet funktioniert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
