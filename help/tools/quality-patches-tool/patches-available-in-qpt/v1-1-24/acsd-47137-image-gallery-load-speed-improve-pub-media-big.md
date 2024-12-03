---
title: 'ACSD-47137: Bildgalerie-Ladegeschwindigkeit verbessern `pub/media` Ordner groß'
description: Wenden Sie den Patch ACSD-47137 an, um die Ladegeschwindigkeit der Bildergalerie zu verbessern, wenn der Ordner "pub/media"sehr groß ist.
feature: Cache, Catalog Management, Categories, Media
role: Admin
exl-id: 8a5dd930-1940-486e-96db-ee1b166cf312
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-47137: Erhöhen Sie die Ladegeschwindigkeit der Bildergalerie, wenn `pub/media` Ordner groß ist.

Der Patch ACSD-47137 verbessert die Ladegeschwindigkeit der Bildergalerie, wenn der Ordner `pub/media` sehr groß ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47137. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Die Ladegeschwindigkeit der Bildergalerie ist langsam, wenn der Ordner `pub/media` sehr groß ist.

<u>Zu reproduzierende Schritte</u>:

1. Navigieren Sie zu Adobe Commerce Admin > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** zu _Nein_.
1. Bereinigen Sie den Konfigurationscache.
1. Melden Sie sich ab und melden Sie sich erneut als Administrator an.
1. Wechseln Sie in der Admin-Seitenleiste zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** und wählen Sie die Stammkategorie aus.
1. Erweitern Sie den Abschnitt **[!UICONTROL Content]** und klicken Sie auf **[!UICONTROL Select from Gallery]**.

Beim Laden der Seite sendet Adobe Commerce eine `media_gallery/directories/gettree` -Anfrage, um die Ordnerstruktur der Medien zu laden.

<u>Erwartete Ergebnisse</u>:

Die `media_gallery/directories/gettree` -Anfrage sollte Inhalt nur aus den erforderlichen Verzeichnissen laden, außer die gesamte Pfadliste aus dem Ordner `pub/media/` in Schleife zu unterteilen.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der `media_gallery/directories/gettree` -Anfrage dauert lange, wenn der Ordner `pub/media/` viele Inhalte enthält.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
