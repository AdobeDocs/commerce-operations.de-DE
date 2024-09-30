---
title: "ACSD-56616: Storefront-Anzeige gebündelter Produkte bei einfacher Lagerhaltung"
description: Wenden Sie den Patch ACSD-56616 an, um das Adobe Commerce-Problem zu beheben, bei dem gebündelte Produkte unerwartet auf der Storefront angezeigt werden, wenn alle zugehörigen einfachen Produkte nicht vorrätig sind.
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-56616: Storefront-Anzeige von gebündelten Produkten während einfacher Lagerknappheit.

Der Patch ACSD-56616 behebt das Problem, dass gebündelte Produkte unerwartet auf der Storefront angezeigt werden, wenn alle verknüpften einfachen Produkte nicht vorrätig sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56616. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Falsche Anzeige von gebündelten Produkten in Storefront bei einfacher Lagerhaltung.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine neue Website/einen neuen Store/eine neue Storefront.
1. Erstellen Sie eine neue Quelle.
1. Erstellen Sie ein neues Lager und weisen Sie es der neu erstellten Website zu.
1. Konfigurieren Sie Indexer, um sie planmäßig zu aktualisieren.
1. Generieren Sie zwei einfache Produkte, S1 (qty = 1) und S2 (qty = 1), und weisen Sie sie dem neuen Lager und der neuen Website zu.
1. Erstellen Sie das Produkt *bundled1* und verknüpfen Sie es mit der neuen Website, indem Sie es in die Kategorie *CAT* eintragen.
1. Definieren Sie zwei erforderliche Dropdown-Optionen und verknüpfen Sie das einfache Produkt *S1* mit Option1 und *S2* mit Option2.
1. Speichern Sie die Produkte.
1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** und aktivieren Sie *Speichercode zu URL hinzufügen* = *Ja*.
1. Öffnen Sie die Storefront und kaufen Sie das gebündelte Produkt.
1. Führen Sie zweimal cron aus.
1. Kehren Sie zur Kategorie *CAT* zurück.

<u>Erwartete Ergebnisse</u>:

Das Produkt *bundle1* ist nicht mehr vorrätig.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt *bundle1* ist mit Preis = *$0* sichtbar.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
