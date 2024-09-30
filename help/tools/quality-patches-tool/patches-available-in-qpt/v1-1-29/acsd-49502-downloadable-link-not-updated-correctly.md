---
title: '"ACSD-49502: Downloadfähiger Link nach [!DNL staging] Update'' nicht korrekt aktualisiert'
description: Wenden Sie den Patch ACSD-49502 an, um das Adobe Commerce-Problem zu beheben, bei dem der herunterladbare Link nicht ordnungsgemäß aktualisiert wird, nachdem ein [!DNL staging] Update auf das herunterladbare Produkt angewendet wurde.
feature: Staging
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-49502: Download-Link nach [!DNL staging] Update nicht korrekt aktualisiert

Der Patch ACSD-49502 behebt das Problem, dass der herunterladbare Link nach der Anwendung eines [!DNL staging] -Updates auf das herunterladbare Produkt nicht korrekt aktualisiert wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 installiert ist. Die Patch-ID lautet ACSD-49502. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der herunterladbare Link wird nicht ordnungsgemäß aktualisiert, nachdem ein [!DNL staging] -Update auf das herunterladbare Produkt angewendet wurde.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie ein herunterladbares Produkt mit Links.
1. Erstellen Sie ein Kundenkonto und melden Sie sich an.
1. Fügen Sie das herunterladbare Produkt aus der Storefront in den Warenkorb.
1. Planen Sie in der **[!UICONTROL Admin]** ein neues Update für das herunterladbare Produkt und lassen Sie die geplante Aktualisierung abgeschlossen.
1. Führen Sie die Bestellung auf der Storefront aus.

<u>Erwartete Ergebnisse</u>:

Downloadbare Links werden beibehalten, wenn geplante Aktualisierungen verwendet werden, während zuvor hinzugefügte Produkte sich im Warenkorb befinden.

<u>Tatsächliche Ergebnisse</u>:

Herunterladbare Links fehlen sowohl unter den *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) des Kunden als auch auf den Bestellansichtsseiten in der **[!UICONTROL Admin]**.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
