---
title: 'ACSD-58471: Dynamische Inhalte können nicht auf der Produktdetailseite geladen werden, wenn die zugehörigen Katalogpreisregeln geplant wurden'
description: Wenden Sie den Patch ACSD-58471 an, um das Adobe Commerce-Problem zu beheben, bei dem dynamischer Inhalt nicht auf der Produktdetailseite geladen werden kann, wenn die zugehörigen Katalogpreisregeln geplant wurden.
feature: Catalog Management
role: Admin, Developer
exl-id: 6ff68b74-67fc-400c-aa79-a1274fd19708
source-git-commit: 28390659fe180180c9b2c8d16239008a1f8a510b
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-58471: Dynamische Inhalte können nicht auf der Produktdetailseite geladen werden, wenn die zugehörigen Katalogpreisregeln geplant wurden

Der Patch ACSD-58471 löst das Problem, dass dynamische Inhalte nicht auf der Produktdetailseite geladen werden, wenn die zugehörigen Katalogpreisregeln geplant wurden. Das System zeigt nun auf der Produktdetailseite die dynamischen Inhalte, die mit den Preisregeln für geplante Kataloge verknüpft sind, korrekt an. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58471. Dieses Problem wird voraussichtlich in Adobe Commerce 2.5.0 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Dynamische Inhalte werden nicht auf der Produktdetailseite geladen, wenn Katalogpreisregeln geplant sind.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie einen dynamischen Block in der Commerce-[!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**.
1. Erstellen Sie einen statischen Block unter [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**. Verwenden Sie Widgets, um Inhalte hinzuzufügen.
1. Erstellen Sie ein Produkt und fügen Sie den CMS-Block zur Beschreibung hinzu.
1. Erstellen Sie eine Katalogregel mit einer geplanten Aktualisierung und weisen Sie das Produkt und den erstellten dynamischen Block unter **[!UICONTROL Marketing]** > Promotions > **[!UICONTROL Catalog Products Rules]** zu.
1. Führen Sie das Cron aus und überprüfen Sie, ob die Produktdetailseite den dynamischen Inhalt nach der geplanten Startzeit anzeigt.
1. Erstellen Sie eine Katalogregel ohne geplante Aktualisierung und weisen Sie das Produkt und den erstellten dynamischen Block unter **[!UICONTROL Marketing]** > Promotions > **[!UICONTROL Catalog Products Rules]** zu.
1. Führen Sie das Cron aus und überprüfen Sie, ob die Produktdetailseite den dynamischen Inhalt nach der geplanten Zeit anzeigt.


<u>Erwartete Ergebnisse</u>:

Dynamische Inhalte werden nach der geplanten Startzeit geladen.

<u>Tatsächliche Ergebnisse</u>:

Dynamische Inhalte werden nicht geladen.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
