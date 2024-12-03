---
title: 'ACSD-48212: Beim Produktimport wird das Produkt der falschen Quelle zugewiesen.'
description: Wenden Sie den Patch ACSD-48212 an, um das Adobe Commerce-Problem zu beheben, bei dem der Produktimport das Produkt der falschen Quelle zuordnet.
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48212: Beim Produktimport wird das Produkt der falschen Quelle zugewiesen.

Der Patch ACSD-48212 behebt das Problem, dass der Produktimport das Produkt der falschen Quelle zuordnet. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID lautet ACSD-48212. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Der Produktimport weist das Produkt der falschen Quelle zu.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie eine sekundäre Inventarquelle.
1. Erstellen Sie ein Produkt nur mit der standardmäßigen Inventarquelle.
1. Exportieren Sie das Produkt.
1. Führen Sie `bin/magento cron:run` aus.
1. Öffnen Sie **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Wählen Sie das Produkt aus dem Raster aus.
1. Heben Sie die Zuweisung des Lagers über das Menü *[!UICONTROL mass action]* auf.
1. Führen Sie `bin/magento cron:run` aus.
1. Weisen Sie die sekundäre Quelle über das Menü *[!UICONTROL mass action]* zu.
1. Führen Sie `bin/magento cron:run` aus.
1. Löschen Sie das Produkt über das Menü &quot;*[!UICONTROL mass action]*&quot;.
1. Führen Sie `bin/magento cron:run` aus.
1. Importieren Sie das Produkt mit der zuvor exportierten CSV-Datei.
1. Überprüfen Sie die Quellzuweisung.

<u>Erwartete Ergebnisse</u>:

Das Produkt wird nur der Standardquelle zugewiesen.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wird sowohl der Standard- als auch der sekundären Quelle zugewiesen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
