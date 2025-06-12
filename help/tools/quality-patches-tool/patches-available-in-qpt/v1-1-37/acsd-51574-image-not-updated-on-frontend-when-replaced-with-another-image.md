---
title: 'ACSD-51574: Bild wird im Frontend nicht aktualisiert, wenn es durch ein anderes Bild ersetzt wird'
description: Wenden Sie den Patch ACSD-51574 an, um das Adobe Commerce-Problem zu beheben, bei dem das Bild nicht im Frontend aktualisiert wird, nachdem es durch ein anderes Bild ersetzt wurde.
feature: Configuration
role: Admin
exl-id: 199674fc-c3b3-4fee-9061-f0546833c1cd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-51574: Bild wird im Frontend nicht aktualisiert, wenn es durch ein anderes Bild ersetzt wird

Mit dem Patch ACSD-51574 wird das Problem behoben, dass das Bild im Frontend nicht aktualisiert wird, nachdem es durch ein anderes Bild ersetzt wurde. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-51574. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Bild wird im Frontend nicht aktualisiert, nachdem es durch ein anderes Bild ersetzt wurde.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt mit einigen Bildern.
1. Bearbeiten Sie das Produkt und laden Sie ein Bild mit einem bekannten Namen hoch (Beispiel: *image.jpg*).
1. Speichern Sie das Produkt.
1. Bearbeiten Sie das Produkt erneut und löschen Sie die alte Version des Bildes und laden Sie die neue Version des Bildes mit demselben Namen hoch. **Stellen Sie sicher, dass die neue Version sichtbar anders ist, um das Problem anzuzeigen.**
1. Speichern Sie das Produkt. Sowohl Admin als auch Frontend zeigen die Bilder an.
1. Bearbeiten Sie das Produkt erneut und laden Sie dasselbe neue Bild erneut hoch (mit demselben Namen).
1. Speichern Sie das Produkt und überprüfen Sie die Produktseite im Frontend.

<u>Erwartete Ergebnisse</u>:

Bei dem zum zweiten Mal hochgeladenen Bild sollte es sich um das neue Bild handeln, zusammen mit dem umbenannten Bildnamen.

<u>Tatsächliche Ergebnisse</u>:

Das beim zweiten Hochladen hochgeladene Bild ist die zuvor gelöschte ältere Version des Bildes, anstelle des gleichen neuen Bildes.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
