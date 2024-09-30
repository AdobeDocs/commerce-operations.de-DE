---
title: "ACSD-59229: Fehlzuordnung von Kundengruppendaten aufgrund eines veralteten X-Magento-Vary-Werts"
description: Wenden Sie den Patch ACSD-59229 an, um das Adobe Commerce-Problem zu beheben, bei dem gruppenbezogene Kundeninformationen aufgrund eines veralteten X-Magento-Vary-Werts in der Anfrage im falschen Segment gespeichert werden.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-59229: Fehlzuweisung von Kundengruppendaten aufgrund eines veralteten X-Magento-Vary-Werts

Der Patch ACSD-59229 behebt das Problem, bei dem gruppenbezogene Kundeninformationen aufgrund eines veralteten X-Magento-Vary-Werts in der Anfrage im falschen Segment gespeichert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-59229. Bitte beachten Sie, dass das Problem in Version 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Kundengruppenbezogene Informationen werden aufgrund eines veralteten X-Magento-Vary -Werts in der Anfrage im falschen Segment gespeichert.

<u>Voraussetzungen</u>:

Stellen Sie sicher, dass Adobe Commerce B2B mit Beispieldaten installiert und [!DNL Varnish] konfiguriert ist.

<u>Zu reproduzierende Schritte</u>:

1. Richten Sie erweiterte Preise für den [!DNL SKU 24-MB01] ein:
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *Großhandel* = *$200*
      * *Händler* = *$30*

1. Erstellen Sie zwei Kundenkonten.
1. Weisen Sie beide Kunden der Gruppe **Großhandel** zu.
1. Öffnen Sie zwei verschiedene Browser-Sitzungen und melden Sie sich bei jedem Kunden an.
1. Navigieren Sie für jeden Kunden zur Produktseite **[!UICONTROL 24-MB01]** und überprüfen Sie, ob der angezeigte Preis *$200* ist.
1. Ändern Sie die Kundengruppe für einen Kunden in **Einzelhandel**.
1. Löschen Sie den Cache mit dem Befehl: `bin/magento cache:flush full_page`.
1. Aktualisieren Sie die Produktseite für jeden Kunden.

<u>Erwartete Ergebnisse</u>:

1. Der Einzelhandelskunde kann den richtigen Preis von *$30* für das Produkt sehen.
1. Der Großhandelskunde kann den richtigen Preis von *$200* für das Produkt sehen.

<u>Tatsächliche Ergebnisse</u>:

1. Der Einzelhandelskunde kann den richtigen Preis von *$30* für das Produkt sehen.
1. Der Großhandelskunde sieht einen falschen Preis von *$30* (Einzelhandelspreis) für das Produkt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
