---
title: 'ACSD-49179: Der Bestellbericht zeigt falsche Beträge für verschiedene Geschäfte an.'
description: Wenden Sie den Patch ACSD-49179 an, um das Adobe Commerce-Problem zu beheben, bei dem im Bestellbericht falsche Beträge angezeigt werden, wenn verschiedene Währungen für verschiedene Geschäfte verwendet werden.
feature: Admin Workspace, Orders
role: Admin
exl-id: b10653ef-c4b1-40df-8bfe-7da755db621b
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# ACSD-49179: Der Bestellbericht zeigt falsche Beträge für verschiedene Geschäfte an

Der Patch ACSD-49179 behebt das Problem, dass im Bestellbericht falsche Beträge angezeigt werden, wenn verschiedene Währungen für verschiedene Geschäfte verwendet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID lautet ACSD-49179. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Bestellbericht zeigt bei unterschiedlichen Währungen für verschiedene Geschäfte falsche Beträge an.

<u>Zu reproduzierende Schritte</u>:

1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** und legen Sie [!UICONTROL Catalog Price Scope] = [!UICONTROL Website] fest.
1. Erstellen Sie eine zusätzliche Website-, Store- und Store-Ansicht.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL General]** > **[!UICONTROL Currency Setup]** > **[!UICONTROL Currency Options]** und legen Sie Folgendes fest:
   * Standardkonfiguration:
      * Basiswährung: USD
      * Standardanzeigewährung: USD
      * Zulässige Währungen: EUR, USD und THB (Thailändischer Baht)
   * Hauptwebsite:
      * Basiswährung: EUR
      * Standardanzeigewährung: EUR
      * Zulässige Währungen: EUR
   * Zusätzliche neue Website:
      * Basiswährung: THB (Thailändischer Baht)
      * Standardanzeigewährung: THB (Thailändischer Baht)
      * Zulässige Währungen: THB (Thailändischer Baht)
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Currency]** > **[!UICONTROL Currency Rates]** und legen Sie die leeren Konversionsraten für die THB fest (setzen Sie die Raten auf 1.0000).
1. Erstellen Sie ein Produkt, weisen Sie es beiden Websites zu und bestellen Sie dieses Produkt auf der zuvor erstellten zusätzlichen Website.
1. Stellen Sie sicher, dass die Bestellung den Status *Verarbeitung* aufweist (Rechnung).
1. Gehen Sie im Backend zu **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
1. Klicken Sie auf die Warnung **[!UICONTROL Yellow]** , um die Statistiken zu aktualisieren.
1. Legen Sie den Umfang des Berichts auf der zuvor erstellten zusätzlichen Website fest und legen Sie den Filter wie folgt fest:
   * [!UICONTROL Date Used]: [!UICONTROL Created]
   * [!UICONTROL Period]: [!UICONTROL Day]
   * [!UICONTROL From and To]: Am selben Tag, an dem die Testreihenfolge platziert wurde
   * [!UICONTROL Order Status]: [!UICONTROL Any]
   * [!UICONTROL Empty rows]: [!UICONTROL No]
   * [!UICONTROL Show Actual Values]: [!UICONTROL No]

<u>Erwartete Ergebnisse</u>:

Der Gesamtumsatz zeigt den korrekten Betrag an, der in die Währung der Website konvertiert wurde.

<u>Tatsächliche Ergebnisse</u>:

Die Summe ist null.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
