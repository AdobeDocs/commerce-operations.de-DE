---
title: '"ACSD-51408: Bestellelementstatus falsch auf [!UICONTROL backordered] gesetzt'
description: Wenden Sie den Patch ACSD-51408 an, um das Adobe Commerce-Problem zu beheben, bei dem der Bestellelementstatus fälschlicherweise auf [!UICONTROL backordered] festgelegt ist.
feature: B2B, Orders
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-51408: Bestellelementstatus falsch auf *[!UICONTROL backordered]* gesetzt

Der Patch ACSD-51408 behebt das Problem, bei dem der Bestellelementstatus fälschlicherweise auf [!UICONTROL backordered] gesetzt ist. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.33 installiert ist. Die Patch-ID ist ACSD-51408. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p1

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Status des Bestellelements ist falsch auf *[!UICONTROL backordered]* eingestellt.

<u>Voraussetzungen</u>:

Die Module Adobe Commerce B2B und Inventory management (MSI) sind installiert.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Website-, Store- und Store-Ansicht.
1. Erstellen Sie eine neue Quelle.
1. Erstellen Sie ein neues Lager, das mit der in Schritt 1 erstellten neuen Website verknüpft ist, und weisen Sie die in Schritt 2 erstellte Quelle zu.
1. Erstellen Sie ein Unternehmen und weisen Sie es der in Schritt 1 erstellten neuen Website zu.
1. Erstellen Sie einen neuen Kunden und weisen Sie ihn dem in Schritt 4 erstellten Unternehmen zu.
1. Erstellen Sie ein Produkt, weisen Sie es der neuen Website zu und legen Sie **[!UICONTROL default stock]** = *0* und die **[!UICONTROL new stock]** auf einen Wert fest, der größer als *0* ist.
1. Aktivieren Sie **[!UICONTROL backorders]**.
1. Aktivieren Sie die Zahlungsmethode **[!UICONTROL Check/Money Order]** für den neuen Website-Umfang.
1. Aktivieren Sie den **[!UICONTROL Flat Rate shipping method]** für den neuen Website-Umfang.
1. Erstellen Sie eine neue Bestellung von **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]**.
1. Wählen Sie den neuen Kunden aus, der in Schritt 5 erstellt wurde.
1. Wählen Sie den in Schritt 1 erstellten neuen Store aus.
1. Wählen Sie das in Schritt 6 erstellte Produkt aus.
1. Füllen Sie die Bestellinformationen aus, einschließlich der Zahlungs- und Versandmethoden.
1. Übermitteln Sie die Bestellung.
1. Überprüfen Sie den *Elementstatus*.

<u>Erwartete Ergebnisse</u>

Der Artikel kann aus dem Bestand versandt werden. Der Elementstatus lautet *[!UICONTROL ordered]*.

<u>Tatsächliche Ergebnisse</u>

Der Elementstatus lautet *[!UICONTROL backordered]*.

>[!MORELIKETHIS]
>
>[Der Bestellelementstatus ist falsch auf *[!UICONTROL Ordered]* eingestellt, wenn der Produktbestand 0 ist.](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-33/acsd-51735-order-item-status-incorrectly-set.md)

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
