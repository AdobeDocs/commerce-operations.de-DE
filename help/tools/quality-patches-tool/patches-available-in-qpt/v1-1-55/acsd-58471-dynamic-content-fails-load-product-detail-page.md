---
title: "ACSD-58471: Dynamischer Inhalt wird nicht auf der Produktdetailseite geladen, wenn die zugehörigen Katalogpreisregeln geplant wurden"
description: Wenden Sie den Patch ACSD-58471 an, um das Adobe Commerce-Problem zu beheben, bei dem dynamische Inhalte nicht auf der Produktdetailseite geladen werden können, wenn die zugehörigen Katalogpreisregeln geplant wurden.
feature: Catalog Management
role: Admin, Developer
exl-id: 6ff68b74-67fc-400c-aa79-a1274fd19708
source-git-commit: 28390659fe180180c9b2c8d16239008a1f8a510b
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-58471: Dynamischer Inhalt wird nicht auf der Produktdetailseite geladen, wenn die zugehörigen Katalogpreisregeln geplant wurden

Der Patch ACSD-58471 behebt das Problem, dass dynamische Inhalte nicht auf der Produktdetailseite geladen werden können, wenn die zugehörigen Katalogpreisregeln geplant wurden. Das System zeigt nun auf der Produktdetailseite korrekt dynamische Inhalte an, die mit geplanten Katalogpreisregeln verknüpft sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 installiert ist. Die Patch-ID ist ACSD-58471. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.5.0 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Dynamische Inhalte werden nicht auf der Produktdetailseite geladen, wenn Katalogpreisregeln geplant sind.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einen dynamischen Block in der Commerce [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**.
1. Erstellen Sie einen statischen Block in [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**. Verwenden Sie Widgets, um Inhalte hinzuzufügen.
1. Erstellen Sie ein Produkt und fügen Sie der Beschreibung den CMS-Baustein hinzu.
1. Erstellen Sie eine Katalogregel mit einer geplanten Aktualisierung und weisen Sie das Produkt und den erstellten dynamischen Block unter **[!UICONTROL Marketing]** > Promotions > **[!UICONTROL Catalog Products Rules]** zu.
1. Führen Sie den Cron aus und vergewissern Sie sich, dass auf der Produktdetailseite der dynamische Inhalt nach der geplanten Startzeit angezeigt wird.
1. Erstellen Sie eine Katalogregel ohne geplante Aktualisierung und weisen Sie das Produkt und den erstellten dynamischen Block unter **[!UICONTROL Marketing]** > Promotions > **[!UICONTROL Catalog Products Rules]** zu.
1. Führen Sie den Cron aus und überprüfen Sie, ob die Seite mit den Produktdetails den dynamischen Inhalt nach der geplanten Zeit anzeigt.


<u>Erwartete Ergebnisse</u>:

Dynamische Inhalte werden nach der geplanten Startzeit geladen.

<u>Tatsächliche Ergebnisse</u>:

Dynamische Inhalte werden nicht geladen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für Qualitäts-Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
