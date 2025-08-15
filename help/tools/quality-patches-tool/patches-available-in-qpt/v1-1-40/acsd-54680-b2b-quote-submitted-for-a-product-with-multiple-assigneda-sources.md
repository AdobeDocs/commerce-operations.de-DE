---
title: 'ACSD-54680: B2B-Angebot für ein Produkt mit mehreren zugewiesenen Quellen kann nicht verarbeitet werden'
description: Wenden Sie den Patch ACSD-54680 an, um das Adobe Commerce-Problem zu beheben, bei dem das B2B-Angebot für ein Produkt mit mehreren zugewiesenen Quellen nicht verarbeitet werden kann.
feature: B2B
role: Admin, Developer
exl-id: c5307785-a4c6-4d0c-9009-0d0caee97b3d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-54680: B2B-Quote für ein Produkt mit mehreren zugewiesenen Quellen kann nicht verarbeitet werden.

Der Patch von ACSD-54680 behebt das Problem, dass das B2B-Angebot für ein Produkt mit mehreren zugewiesenen Quellen nicht verarbeitet werden kann. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.40 installiert ist. Die Patch-ID ist ACSD-54680. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

B2B-Angebot für ein Produkt mit mehreren zugewiesenen Quellen kann nicht verarbeitet werden.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** und erstellen Sie zwei neue Quellen: **Source 1** und **Source 2**.
1. Gehen Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** und erstellen Sie einen neuen Stock: **Stock A**, weisen Sie ihn der Haupt-Website zu und weisen Sie ihm **Source 1** und **Source 2** zu.
1. Erstellen Sie ein einfaches Produkt, weisen Sie **Source 1** und **Source 2** zu und legen Sie für jede Quelle *= 2* fest. (Die verkaufsfähige Menge des Erzeugnisses sollte daher *4* betragen.)
1. Erstellen Sie ein Unternehmenskonto.
1. Wechseln Sie zur **[!UICONTROL Storefront]** und melden Sie sich beim Unternehmenskonto an.
1. Fügen Sie das einfache Produkt mit der Menge = *4* zum Warenkorb hinzu.
1. Öffnen Sie die *[!UICONTROL Shopping cart]* und klicken Sie auf **[!UICONTROL Request a quote]** Schaltfläche .
1. Fügen Sie einen Kommentar und einen Anführungsnamen hinzu und klicken Sie auf **[!UICONTROL Send a Request]** Schaltfläche.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Kürzlich gesendetes Angebot öffnen.

<u>Erwartete Ergebnisse</u>:

Die angeführten Artikel enthalten das bestellte Produkt.

<u>Tatsächliche Ergebnisse</u>:

Der Seitenabschnitt für angeführte Elemente ist leer, und es ist nicht möglich, das Angebot zu verarbeiten.
`var/log/system.log` enthält

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
