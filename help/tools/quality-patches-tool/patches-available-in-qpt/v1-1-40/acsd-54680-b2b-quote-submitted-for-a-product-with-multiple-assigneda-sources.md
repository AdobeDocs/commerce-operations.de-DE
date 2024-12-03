---
title: 'ACSD-54680: B2B-Anführungszeichen für ein Produkt mit mehreren zugewiesenen Quellen kann nicht verarbeitet werden'
description: Wenden Sie den Patch ACSD-54680 an, um das Adobe Commerce-Problem zu beheben, bei dem das B2B-Angebot für ein Produkt mit mehreren zugewiesenen Quellen nicht verarbeitet werden kann.
feature: B2B
role: Admin, Developer
exl-id: c5307785-a4c6-4d0c-9009-0d0caee97b3d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-54680: B2B-Zitat für ein Produkt mit mehreren zugewiesenen Quellen kann nicht verarbeitet werden.

Der Patch ACSD-54680 behebt das Problem, dass das B2B-Zitat für ein Produkt mit mehreren zugewiesenen Quellen nicht verarbeitet werden kann. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.40 installiert ist. Die Patch-ID ist ACSD-54680. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.6 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

B2B-Anführungszeichen für ein Produkt mit mehreren zugewiesenen Quellen kann nicht verarbeitet werden.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** und erstellen Sie zwei neue Quellen: **Source 1** und **Source 2**.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** und erstellen Sie einen neuen Lager: **Stock A**, weisen Sie ihn der Hauptwebsite zu und weisen Sie ihm **Source 1** und **Source 2** zu.
1. Erstellen Sie ein einfaches Produkt, weisen Sie **Source 1** und **Source 2** zu und legen Sie für jede Quelle &quot;Menge = *2*&quot;fest. (Die Verkaufsmenge des Produkts sollte daher *4* betragen.)
1. Erstellen Sie ein Unternehmenskonto.
1. Gehen Sie zu &quot;**[!UICONTROL Storefront]**&quot;und melden Sie sich beim Unternehmenskonto an.
1. Fügen Sie das einfache Produkt zum Warenkorb mit qty = *4* hinzu.
1. Öffnen Sie den *[!UICONTROL Shopping cart]* und klicken Sie auf die Schaltfläche **[!UICONTROL Request a quote]** .
1. Fügen Sie einen Kommentar- und einen Anführungsnamen hinzu und klicken Sie auf die Schaltfläche **[!UICONTROL Send a Request]** .
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Vor Kurzem veröffentlichte Zitat öffnen.

<u>Erwartete Ergebnisse</u>:

Die zitierten Artikel enthalten das bestellte Produkt.

<u>Tatsächliche Ergebnisse</u>:

Die im Abschnitt &quot;Seite&quot;aufgeführten Elemente sind leer, und das Anführungszeichen kann nicht verarbeitet werden.
`var/log/system.log` contains

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
