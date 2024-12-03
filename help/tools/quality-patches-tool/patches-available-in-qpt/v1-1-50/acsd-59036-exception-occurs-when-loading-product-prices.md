---
title: 'ACSD-59036: Beim Laden von Produktpreisen tritt eine Ausnahme auf, wenn sowohl die untere als auch die obere Grenze auf 0 USD gesetzt sind'
description: Wenden Sie den Patch ACSD-59036 an, um das Adobe Commerce-Problem zu beheben, bei dem beim Laden von Produktpreisen eine Ausnahme auftritt, wobei sowohl die untere als auch die obere Grenze auf *$0* festgelegt sind.
feature: Categories, Products, Storefront, Search
role: Admin, Developer
exl-id: a7d05108-0b03-4eb4-84ab-0dc5601530cb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# ACSD-59036: Beim Laden von Produktpreisen tritt eine Ausnahme auf, wenn sowohl die untere als auch die obere Grenze auf *$0* gesetzt sind

Der Patch ACSD-59036 behebt das Problem, dass beim Laden von Produktpreisen eine Ausnahme auftritt, wobei sowohl die untere als auch die obere Grenze auf *$0* gesetzt sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 installiert ist. Die Patch-ID ist ACSD-59036. Bitte beachten Sie, dass dieses Problem in Adobe Commerce 2.4.8 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine Ausnahme tritt beim Laden von Produktpreisen auf, wobei sowohl die untere als auch die obere Grenze auf *$0* festgelegt sind.

Das Problem tritt auf, da der Algorithmus beim Laden der Abfrage mit Preisbereichen keine NULL-Werte berücksichtigt. Um dies zu beheben, können wir überprüfen, ob sowohl der untere als auch der obere Bereich NULL sind. Weisen Sie dann für beide Begrenzungen den Wert *0* zu. Dadurch soll verhindert werden, dass Fehler ausgegeben werden.

<u>Zu reproduzierende Schritte</u>:

1. Erstellen Sie einfache *13* Produkte.
1. Weisen Sie alle *13* -Produkte einer Kategorie zu.
1. Setzen Sie den Preis eines Produkts auf *$1322.94*.
1. Setzen Sie den Preis aller anderen Produkte auf *$0*.
1. Konfigurieren Sie [!DNL OpenSearch] als Suchmaschine.
1. Gehen Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** und setzen Sie die **[!UICONTROL PLP]** -Anzahl auf *16*.
1. Setzen Sie **[!UICONTROL Price Navigation Step Calculation]** auf *Automatisch (gleich Produktzahlen)*.
1. Führen Sie die vollständige Neuindizierung aus.
1. Öffnen Sie die Seite &quot;*[!UICONTROL Category]*&quot;.

<u>Erwartete Ergebnisse</u>:

Auf der Seite *[!UICONTROL Category]* werden alle Produkte angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Es tritt ein Fehler auf:

```JSON
report.CRITICAL: OpenSearch\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]"}],"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [filter]","caused_by":{"type":"x_content_parse_exception","reason":"[1:193] [bool] failed to parse field [must]","caused_by":{"type":"illegal_argument_exception","reason":"field name is null or empty"}}},"status":400} in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Connections/Connection.php:664
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
