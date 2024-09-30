---
title: "ACSD-56979: Produktbilder wurden nach Löschen der Staging-Aktualisierung entfernt"
description: Wenden Sie den Patch ACSD-56979 an, um das Adobe Commerce-Problem zu beheben, bei dem Produktbilder nach dem Löschen eines Staging-Updates entfernt werden
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56979: Produktbilder wurden nach dem Löschen der Staging-Aktualisierung entfernt

Der Patch ACSD-56979 behebt das Problem, dass Produktbilder nach dem Löschen eines Staging-Updates entfernt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 installiert ist. Die Patch-ID ist ACSD-56979. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce- und Magento Open Source-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Produktbilder werden nach dem Löschen eines Staging-Updates entfernt.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie in der Commerce Admin-Seitenleiste zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und erstellen Sie ein Produkt.
1. Laden Sie unter &quot;**[!UICONTROL Images and Videos]**&quot;ein Bild hoch und speichern Sie das Produkt.
1. Wählen Sie im Feld **[!UICONTROL Scheduled Changes]** die Option **[!UICONTROL Schedule New Update]** aus.
   1. Wählen Sie ein Startdatum für einige Minuten in der Zukunft aus.
   1. Wählen Sie kein Enddatum aus.
1. Wählen Sie im Feld **[!UICONTROL Scheduled Changes]** den Link **[!UICONTROL View/Edit]** aus.
1. Gehen Sie zu **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]** und wählen Sie **[!UICONTROL Done]** aus.
1. Aktualisieren Sie die Seite.

<u>Erwartete Ergebnisse</u>:

Da die Aktualisierung vor dem geplanten Startdatum entfernt wird, sollte das Produkt unverändert bleiben.

<u>Tatsächliche Ergebnisse</u>:

Der Bildinhalt geht verloren und zeigt Null Byte an.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
