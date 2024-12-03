---
title: 'ACSD-47704: Gebündeltes Produkt zeigt nur den Preis von Lagerprodukten an'
description: Wenden Sie den Patch ACSD-47704 an, um das Adobe Commerce-Problem zu beheben, bei dem ein gebündeltes Produkt nur den Preis von in Lagerprodukten anzeigt.
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
exl-id: 7f05ceed-869c-4d1a-91fd-0122dc98e65e
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# ACSD-47704: Gebündeltes Produkt zeigt nur den Preis von Lagerprodukten an

Der Patch ACSD-47704 behebt das Problem, dass die Preise für Kundensegmente zwischen Kundengruppen falsch zwischengespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 installiert ist. Die Patch-ID ist ACSD-47704. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6 - p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Preis eines gebündelten Produkts, für das dynamische Preise aktiviert sind, ist falsch, da nur Artikel auf Lager enthalten sind.

<u>Zu reproduzierende Schritte</u>:

1. Wechseln Sie zum Commerce Admin-Bedienfeld.
1. Gehen Sie zu **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. Setzen Sie den dynamischen Preis **[UICONROL Dynamisch Price]** auf **[!UICONTROL Yes]**.
1. Bundle-Elemente:
   * Setzen Sie **[!UICONTROL Ship bundle items]** auf **[!UICONTROL Together]**
   * Wählen Sie **[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Kontrollkästchen &quot;Erforderlich markieren&quot;
      * Fügen Sie jedes einfache Produkt hinzu, das auf Lager ist, z. B. Joust Duffle Bag SKU 24-MB01. Beachten Sie vor dem Hinzufügen des Produkts seinen Preis - 34 USD
   * Standardmenge: 1
   * Wählen Sie **[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Kontrollkästchen &quot;Erforderlich markieren&quot;
      * Fügen Sie ein einfaches Produkt hinzu, das auf Lager ist, das sich von dem im vorherigen Schritt hinzugefügten Produkt unterscheidet, z. B. - Strive Shoulder Pack 24-MB04. Beachten Sie vor dem Hinzufügen des Produkts seinen Preis - 32 USD
      * Standardmenge: 1
1. Produkt speichern.
1. Gehen Sie zur Storefront und suchen Sie nach dem Produkt, das Sie in den vorherigen Schritten erstellt haben. Beachten Sie den Preis - 66 USD
(66 = 32 + 34).
Derzeit entspricht der Preis des Bundle-Produkts der Summe der Preise seiner Optionen.
1. Wechseln Sie zum Commerce Admin-Bedienfeld. Gehen Sie zu **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. Suchen Sie zuvor nach einem der einfachen Produkte, die dem Bundle-Produkt als Option zugewiesen wurden:
SKU 24-MB01 und ein Preis von 34 USD.
1. Ändern Sie die Menge auf 0.
1. Speichern Sie das Produkt.
1. Gehen Sie zur Storefront und suchen Sie nach dem Bundle-Produkt, das in den vorherigen Schritten erstellt wurde. Beachten Sie den Preis - 32 USD. Zuvor war der Preis 66 USD, was der Summe von 34 USD von 24-MB01 SKU und 32 USD von 24-MB04 SKU entsprach. Nachdem das Produkt 24 MB01 nicht mehr vorrätig ist, wird der Bundle-Preis als 32 USD angezeigt. Es handelt sich um den Preis des anderen Produkts, bei dem es sich um eine Option auf Lager handelt.

<u>Erwartete Ergebnisse</u>:

Der Preis von Bundle-Produkten mit aktivierter dynamischer Preisgestaltung wird konsistent berechnet, unabhängig davon, ob die Optionen vorrätig sind oder nicht.

<u>Tatsächliche Ergebnisse</u>:

Der Preis des Bundle-Produkts, für das dynamische Preise aktiviert sind, wird falsch berechnet. Es werden nur die auf Lager befindlichen Optionen berücksichtigt, was dazu führt, dass ein niedrigerer Wert als der tatsächliche angezeigt wird, wenn eine der Optionen nicht mehr vorrätig ist.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
