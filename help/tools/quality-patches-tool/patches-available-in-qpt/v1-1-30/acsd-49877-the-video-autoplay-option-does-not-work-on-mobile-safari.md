---
title: "ACSD-49877: Video-Autoplay funktioniert nicht auf Mobilgeräten [!DNL Safari]"
description: Wenden Sie den Patch ACSD-49877 an, um das Adobe Commerce-Problem zu beheben, bei dem die Option für die automatische Videowiedergabe auf Mobilgeräten nicht funktioniert [!DNL Safari] , wenn das Video direkt mit einer Remote-Videodatei verknüpft ist.
feature: CMS
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-49877: Video-Autoplay funktioniert nicht auf Mobilgeräten [!DNL Safari]

ACSD-49877 behebt das Problem, dass die automatische Wiedergabe auf dem Mobilgerät [!DNL Safari] nicht funktioniert, wenn das Video direkt mit einer Remote-Videodatei verknüpft ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.30 installiert ist. Die Patch-ID lautet ACSD-49877. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket [!magento/quality-patches] auf die neueste Version und überprüfen Sie die Kompatibilität mit dem Paket [[!DNL Quality Patches Tool]: Suchen Sie nach Patches]. Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die automatische Videowiedergabe funktioniert nicht auf dem Mobilgerät [!DNL Safari], wenn das Video direkt mit einer Remote-Videodatei und nicht mit einem Streaming-Dienst verknüpft ist.

<u>Voraussetzungen</u>:
[!DNL Page Builder] -Module sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue CMS-Seite und bearbeiten Sie die **[!UICONTROL Content Value]** mit [!DNL Page Builder].
1. Fügen Sie dem Inhalt ein Element *Tab* hinzu und fügen Sie ein *Videoelement* in die Registerkarte *5} ein.*
1. Klicken Sie nun auf die Zahnradschaltfläche, um das *Videoelement* zu bearbeiten.
1. Fügen Sie dem Feld [!UICONTROL Video URL] einen Link zu einer MP4-Videodatei hinzu.
1. Markieren Sie das Feld **[!UICONTROL Autoplay]** als *Ja*.
1. Klicken Sie auf **[!UICONTROL Save]**.
1. Öffnen Sie die kürzlich erstellte Seite unter [!DNL Safari] mithilfe einer iPhone.

<u>Erwartete Ergebnisse</u>

Die Option für die automatische Wiedergabe funktioniert bei [!DNL Safari] mit einer iPhone.

<u>Tatsächliche Ergebnisse</u>

Die Option für die automatische Wiedergabe funktioniert nicht bei [!DNL Safari], wenn eine iPhone verwendet wird.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
