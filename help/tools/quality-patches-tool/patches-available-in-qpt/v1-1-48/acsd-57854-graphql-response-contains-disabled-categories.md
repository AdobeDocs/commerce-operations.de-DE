---
title: "ACSD-57854: *GraphQL* Antwort enthält deaktivierte Kategorien, die nicht in Kategorieaggregationen aufgeführt werden sollten"
description: Wenden Sie den Patch ACSD-57854 an, um das Adobe Commerce-Problem zu beheben, bei dem die * GraphQL*-Antwort deaktivierte Kategorien enthält, die nicht in den Kategorieaggregationen aufgeführt werden sollten.
feature: GraphQL
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-57854: *GraphQL* -Antwort enthält deaktivierte Kategorien, die nicht in den Kategorieaggregationen aufgeführt werden sollten

Der Patch ACSD-57854 behebt das Problem, dass die Antwort *GraphQL* deaktivierte Kategorien enthält, die nicht in den Kategorieaggregationen aufgeführt werden sollten. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.48 installiert ist. Die Patch-ID ist ACSD-57854. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

*GraphQL* -Antwort enthält deaktivierte Kategorien, die nicht in den Kategorieaggregationen aufgeführt werden sollten.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie zwei Kategorien.
1. Erstellen Sie ein Produkt (Adobe-Produkt testen) und weisen Sie es beiden Kategorien zu.
1. Deaktivieren Sie eine der erstellten Kategorien.
1. Verwenden Sie die Produkte *GraphQL* , um das Produkt zu suchen.
1. Überprüfen Sie die Liste der Produktkategorien in der Antwort *GraphQL* .

<u>Erwartete Ergebnisse</u>:

Die deaktivierten Kategorien werden nicht in der Antwort *GraphQL* aufgeführt.

<u>Tatsächliche Ergebnisse</u>:

Die deaktivierten Kategorien werden in der Antwort &quot;Kategorieaggregation *GraphQL*&quot;aufgeführt.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
