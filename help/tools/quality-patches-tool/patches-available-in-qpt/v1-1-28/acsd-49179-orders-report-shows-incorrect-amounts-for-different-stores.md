---
title: 'ACSD-49179: Der Bericht „Bestellungen“ zeigt falsche Beträge für verschiedene Geschäfte an.'
description: Wenden Sie den Patch ACSD-49179 an, um das Adobe Commerce-Problem zu beheben, bei dem im Bestellbericht falsche Beträge angezeigt werden, wenn für verschiedene Stores unterschiedliche Währungen verwendet werden.
feature: Admin Workspace, Orders
role: Admin
exl-id: b10653ef-c4b1-40df-8bfe-7da755db621b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-49179: Der Bericht „Bestellungen“ zeigt falsche Beträge für verschiedene Geschäfte an

Mit dem Patch ACSD-49179 wird das Problem behoben, dass im Bestellbericht falsche Beträge angezeigt werden, wenn für verschiedene Geschäfte unterschiedliche Währungen verwendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID ist ACSD-49179. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Im Bestellbericht werden falsche Beträge angezeigt, wenn für verschiedene Geschäfte unterschiedliche Währungen verwendet werden.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** und setzen Sie [!UICONTROL Catalog Price Scope] = [!UICONTROL Website].
1. Erstellen Sie eine zusätzliche Website-, Store- und Store-Ansicht.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** und legen Sie Folgendes fest:
   * Standardkonfiguration:
      * Basiswährung: USD
      * Standardanzeigewährung: USD
      * Zulässige Währungen: EUR, USD und THB (Thailändischer Baht)
   * Haupt-Website:
      * Basiswährung: EUR
      * Standardanzeigewährung: EUR
      * Zulässige Währungen: EUR
   * Zusätzliche neue Website:
      * Basiswährung: THB (Thai Baht)
      * Standardanzeigewährung: THB (Thai Baht)
      * Zulässige Währungen: THB (Thai Baht)
1. Navigieren Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** und legen Sie die leeren Konversionsraten für den THB fest (legen Sie die Raten auf 1.0000 fest).
1. Erstellen Sie ein Produkt, weisen Sie es beiden Websites zu, und geben Sie eine Bestellung mit diesem Produkt auf der zuvor erstellten zusätzlichen Website auf.
1. Stellen Sie sicher, dass sich die Bestellung im Status *Verarbeitung* befindet (Fakturieren Sie sie).
1. Navigieren Sie im Backend zu **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Klicken Sie auf die **[!UICONTROL Yellow]** Warnung, um die Statistiken zu aktualisieren.
1. Legen Sie den Umfang des Berichts auf der zuvor erstellten zusätzlichen Website fest und stellen Sie den Filter wie folgt ein:
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: Der Tag, an dem die Testbestellung aufgegeben wurde
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u>Erwartete Ergebnisse</u>:

Verkaufssumme zeigt den korrekten Betrag an, der in die Währung der Website umgerechnet wird.

<u>Tatsächliche Ergebnisse</u>:

Die Summe ist null.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
