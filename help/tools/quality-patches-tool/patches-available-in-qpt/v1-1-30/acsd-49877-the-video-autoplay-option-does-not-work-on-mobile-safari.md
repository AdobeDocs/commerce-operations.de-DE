---
title: 'ACSD-49877: Die automatische Videowiedergabe funktioniert nicht auf Mobilgeräten [!DNL Safari]'
description: Wenden Sie den Patch ACSD-49877 an, um das Adobe Commerce-Problem zu beheben, dass die Option für die automatische Videowiedergabe auf Mobilgeräten nicht funktioniert [!DNL Safari]  wenn das Video direkt mit einer Remote-Videodatei verknüpft ist.
feature: CMS
role: Admin
exl-id: aa2557e2-4bed-4004-b9bc-36c59f1e9cdc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-49877: Die automatische Videowiedergabe funktioniert nicht auf mobilen [!DNL Safari]

Mit dem ACSD-49877 wird das Problem behoben, dass die Option zur automatischen Wiedergabe auf mobilen [!DNL Safari] nicht funktioniert, wenn das Video direkt mit einer Remote-Videodatei verknüpft ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID ist ACSD-49877. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket [ !magento/quality-patches] auf die neueste Version und überprüfen Sie die Kompatibilität auf der [[!DNL Quality Patches Tool]: Nach Patches suchen]. Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die automatische Videowiedergabe funktioniert nicht auf mobilen [!DNL Safari], wenn das Video direkt mit einer Remote-Videodatei und nicht mit einem Streaming-Service verknüpft ist.

<u>Voraussetzungen</u>:
[!DNL Page Builder] Module werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue CMS-Seite und bearbeiten Sie die **[!UICONTROL Content Value]** mit [!DNL Page Builder].
1. Fügen Sie *Inhalt* Element „Tab“ hinzu und fügen Sie ein *Videoelement* innerhalb von &quot;*&quot;*.
1. Klicken Sie nun auf die Zahnradschaltfläche, um das *Videoelement* zu bearbeiten.
1. Fügen Sie dem Feld [!UICONTROL Video URL] einen Link zu einer MP4-Videodatei hinzu.
1. Markieren Sie das **[!UICONTROL Autoplay]** Feld als *Ja*.
1. Klicken Sie auf **[!UICONTROL Save]**.
1. Öffnen Sie die kürzlich erstellte Seite in [!DNL Safari] mit einer iPhone.

<u>Erwartete Ergebnisse</u>

Die Option zur automatischen Wiedergabe funktioniert bei [!DNL Safari] mit einer iPhone.

<u>Tatsächliche Ergebnisse</u>

Die Option zur automatischen Wiedergabe funktioniert nicht bei [!DNL Safari], die eine iPhone verwenden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
