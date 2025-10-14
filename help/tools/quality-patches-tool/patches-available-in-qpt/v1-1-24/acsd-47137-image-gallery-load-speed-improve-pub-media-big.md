---
title: 'ACSD-47137: Verbesserung der Ladegeschwindigkeit des Ordners „pub/media“ der Bildergalerie'
description: Wenden Sie den Patch ACSD-47137 an, um die Ladegeschwindigkeit der Bildergalerie zu verbessern, wenn der Ordner „pub/media“ sehr groß ist.
feature: Cache, Catalog Management, Categories, Media
role: Admin
exl-id: 8a5dd930-1940-486e-96db-ee1b166cf312
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-47137: Beschleunigung des Ladevorgangs von Bildergalerien, wenn `pub/media` Ordner groß ist

Der Patch ACSD-47137 verbessert die Ladegeschwindigkeit der Bildergalerie, wenn der `pub/media` sehr groß ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 installiert ist. Die Patch-ID ist ACSD-47137. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Ladegeschwindigkeit der Bildergalerie ist langsam, wenn der `pub/media` sehr groß ist.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** zu _No_.
1. Bereinigen Sie den Konfigurations-Cache.
1. Melden Sie sich ab und melden Sie sich erneut als Administrator an.
1. Navigieren Sie in der Seitenleiste Admin zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** und wählen Sie die Stammkategorie aus.
1. Erweitern Sie den Abschnitt **[!UICONTROL Content]** und klicken Sie auf **[!UICONTROL Select from Gallery]**.

Beim Laden der Seite sendet Adobe Commerce `media_gallery/directories/gettree` Anfrage zum Laden der Medienordnerhierarchie.

<u>Erwartete Ergebnisse</u>:

Die `media_gallery/directories/gettree`-Anfrage sollte nur Inhalte aus den erforderlichen Verzeichnissen laden, anstatt die gesamte Pfadliste in eine Schleife aus dem `pub/media/` Ordner zu verschieben.

<u>Tatsächliche Ergebnisse</u>:

Das Laden der `media_gallery/directories/gettree`-Anfrage dauert sehr lange, wenn der `pub/media/` Ordner viele Inhalte enthält.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
