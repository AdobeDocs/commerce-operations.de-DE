---
title: 'ACSD-62758: Problem mit der Videowiedergabe auf konfigurierbaren Produktseiten wurde behoben'
description: Wenden Sie den ACSD-62758-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Produktvideos auf konfigurierbaren Produktdetailseiten nicht korrekt gerendert werden, wenn URLs vorab ausgewählte Farbfeldoptionen enthalten.
feature: Catalog Management
role: Admin, Developer
exl-id: 084b497d-4471-4458-bc1d-2a452bfe2662
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-62758: Problem mit der Videowiedergabe auf konfigurierbaren Produktseiten wurde behoben

Der Patch ACSD-62758 behebt das Problem, dass Produktvideos auf konfigurierbaren Produktdetailseiten nicht korrekt gerendert werden, wenn URLs vorab ausgewählte Farbfeldoptionen enthalten. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-62758. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Produktvideos werden auf konfigurierbaren Produktdetailseiten nicht korrekt gerendert, wenn die URL vorab ausgewählte Farbfeldoptionen enthält, was dazu führt, dass anstelle des Videos ein statisches Bild angezeigt wird.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu [!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product].
1. Wählen Sie das Attribut **[!UICONTROL Color]** aus und bearbeiten Sie es.
1. Aktualisieren Sie die folgenden Einstellungen:
   1. Legen Sie [!UICONTROL Catalog Input Type for Store Owner] auf [!UICONTROL Visual Swatch] fest.
   1. Legen Sie **[!UICONTROL Update Product Preview Image]** auf **[!UICONTROL Yes]** fest.
1. Erstellen Sie einige Optionen für dieses Attribut.
1. Erstellen Sie eine neue Kategorie und fügen Sie ihr ein neues konfigurierbares Produkt hinzu, indem Sie das Attribut **[!UICONTROL Color]** verwenden.
1. Fügen Sie dem übergeordneten Produkt ein einzelnes zufälliges Bild hinzu.
1. Bearbeiten Sie die neu erstellten konfigurierbaren untergeordneten Produkte und fügen Sie ihrer Mediensammlung ein Video hinzu:
   1. Klicken Sie auf **[!UICONTROL Add Video]** und verwenden Sie die URL für das Testvideo: https://vimeo.com/12860646.
1. Speichern Sie das Produkt, löschen Sie den Cache und indizieren Sie den Store erneut.
1. Öffnen Sie das neu erstellte Produkt in der Storefront, wählen Sie eine der Farbfeldoptionen aus und überprüfen Sie, ob das Video korrekt geladen wird, wenn die Player-Schaltfläche angezeigt wird.
1. Das Video sollte erwartungsgemäß geladen werden und die Player-Schaltfläche sollte angezeigt werden.
1. Klicken Sie nun mit der rechten Maustaste auf eine der Farbfeldoptionen, wählen Sie **[!UICONTROL Inspect]** aus und suchen Sie die Attribut-ID und die Option-ID. Kopieren Sie die Produkt-URL und fügen Sie Folgendes an das Ende an: `www.product-url.com/producit-test#attribute_id=option_id`. Dadurch wird die Option für Musterabschnitte vorab ausgewählt. Öffnen Sie die aktualisierte URL in einem neuen Fenster.

<u>Erwartete Ergebnisse</u>:

Das Video sollte korrekt geladen werden, ähnlich wie bei manueller Auswahl einer Farbfeld -Option.

<u>Tatsächliche Ergebnisse</u>:

Anstelle des Videos wird ein statisches Bild angezeigt. Konsolenfehler werden protokolliert und weisen auf einen Fehler bei der Videoinitialisierung hin.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.

