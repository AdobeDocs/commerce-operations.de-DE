---
title: 'ACSD-49835: [!UICONTROL Use Default Value] Kontrollkästchen wird nicht gespeichert'
description: Wenden Sie den Patch ACSD-49835 an, um das Adobe Commerce-Problem zu beheben, bei dem das Kontrollkästchen [!UICONTROL Use Default Value] nicht ordnungsgemäß auf einer Store-Ebene für ein Attribut mit Mehrfachauswahl gespeichert wird.
feature: Storefront
role: Admin
exl-id: e8d5a95f-b17d-49fc-a6d3-e03554667438
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ACSD-49835: [!UICONTROL Use Default Value] Kontrollkästchen wird nicht gespeichert

Der Patch ACSD-49835 behebt das Problem, dass das Kontrollkästchen [!UICONTROL Use Default Value] nicht ordnungsgemäß auf einer Store-Ebene für ein Attribut mit Mehrfachauswahl gespeichert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID lautet ACSD-49835. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Das Kontrollkästchen [!UICONTROL Use Default Value] wird für ein Attribut mit Mehrfachauswahl nicht ordnungsgemäß auf Store-Ebene gespeichert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine **[!UICONTROL Multiple-select Attribute]** in **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** und fügen Sie sie einem Attributsatz hinzu.
1. Gehen Sie zu einer **[!UICONTROL Product]** und speichern Sie **[!UICONTROL Values]** in **[!UICONTROL All Store Views (Default Scope)]**.
1. Wechseln Sie zu einem bestimmten **[!UICONTROL Store View Scope]** und speichern Sie das Produkt.
1. Gehen Sie zu **[!UICONTROL Store View Scope]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Use Default Value]** .

<u>Erwartete Ergebnisse</u>:

Attributwerte mit Mehrfachauswahl werden beim Aktivieren des Kontrollkästchens [!UICONTROL Use Default Value] im Feld [!UICONTROL Store View Scope] ordnungsgemäß gespeichert.

<u>Tatsächliche Ergebnisse</u>:

Attributwerte mit Mehrfachauswahl werden beim Aktivieren des Kontrollkästchens [!UICONTROL Use Default Value] im Feld [!UICONTROL Store View Scope] nicht ordnungsgemäß gespeichert.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
