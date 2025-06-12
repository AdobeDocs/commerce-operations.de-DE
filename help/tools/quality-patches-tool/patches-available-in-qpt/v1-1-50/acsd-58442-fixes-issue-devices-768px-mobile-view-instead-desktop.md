---
title: 'ACSD-58442: Es wird das Problem behoben, bei dem Geräte mit einer Breite von 768 Pixel als Mobilgeräte behandelt werden, sodass Menü und Kopfzeile in der Mobilansicht geladen werden und nicht auf dem Desktop'
description: Wenden Sie den Patch ACSD-58442 an, um das Adobe Commerce-Problem zu beheben, bei dem Geräte mit einer Breite von 768 Pixel als Mobilgeräte behandelt werden, sodass das Menü und die Kopfzeile in einer Mobilansicht anstatt auf dem Desktop geladen werden.
feature: Storefront
role: Admin, Developer
exl-id: 86ea64aa-10fc-4fa3-9902-918fb8983ca0
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-58442: Es wird das Problem behoben, bei dem Geräte mit einer Breite von 768 Pixel als Mobilgeräte behandelt werden, sodass Menü und Kopfzeile in der Mobilansicht geladen werden und nicht auf dem Desktop

Mit dem Patch ACSD-58442 wird das Adobe Commerce-Problem behoben, bei dem Geräte mit einer Breite von 768 Pixel als Mobilgeräte behandelt werden, sodass das Menü und die Kopfzeile in einer Mobilansicht anstelle eines Desktops geladen werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-58442. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das System behandelt Geräte mit einer Breite von 768 Pixel jetzt als Desktop, um sicherzustellen, dass das Menü und die Kopfzeile korrekt geladen werden. Zuvor wurden Geräte mit einer Breite von 768 Pixel als Mobilgeräte behandelt, wodurch das Menü und die Kopfzeile in einer Mobilansicht geladen wurden.

<u>Schritte zur Reproduktion</u>:

1. Laden Sie die Homepage auf einem iPad Mini oder verwenden Sie das Inspektions-Tool eines Browsers, um die Größe des Browsers auf eine Breite von *768 Pixel* zu ändern.
1. Öffnen Sie das Hauptmenü.

<u>Erwartete Ergebnisse</u>:

Menü und Kopfzeile werden als Desktopansicht geladen.

<u>Tatsächliche Ergebnisse</u>:

Menü und Kopfzeile werden als Mobilansicht geladen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
