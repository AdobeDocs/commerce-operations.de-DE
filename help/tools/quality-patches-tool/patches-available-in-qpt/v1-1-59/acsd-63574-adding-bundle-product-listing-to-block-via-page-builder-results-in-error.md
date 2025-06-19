---
title: 'ACSD-63574: Das Hinzufügen einer [!UICONTROL Bundle Product] zum Block via  [!DNL Page Builder]  zu einem Fehler'
description: Wenden Sie den Patch ACSD-63574 an, um das Adobe Commerce-Problem zu beheben, bei dem das Hinzufügen von **[!UICONTROL Bundle Product]** mit den Optionen „Checkbox“ oder „Multi Select“ zu einem Block über  [!DNL Page Builder]  zu einem Fehler führt.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: bb56c0c2-e094-4173-8260-da154df79748
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574: Das Hinzufügen einer [!UICONTROL Bundle Product]-Liste zu einem Block über [!DNL Page Builder] führt zu einem Fehler

Mit dem Patch ACSD-63574 wird das Problem behoben, dass das Hinzufügen von **[!UICONTROL Bundle Product]** mit `Checkbox`- oder `Multi Select`-Optionen zu einem Block über [!DNL Page Builder] zu einem Fehler führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 installiert ist. Die Patch-ID ist ACSD-63574. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p10

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Hinzufügen von **[!UICONTROL Bundle Product]** zu einem Block mithilfe von [!DNL Page Builder] funktioniert die Vorschau des Produkt-Widgets nicht mehr und zeigt die Fehlermeldung *Beim Generieren dieses Inhalts ist leider ein Fehler aufgetreten*. Dieses Problem tritt insbesondere dann auf, wenn das Produkt-Bundle `Checkbox` oder `Multi Select` Optionstypen enthält und `indexer dimension mode` auf `website_and_customer_group` gesetzt ist. Das Ausnahmenprotokoll zeigt den folgenden Fehler an:

    &quot;
    report.CRITICAL: PDOException: SQLSTATE[42S02]: Basistabelle oder Ansicht nicht gefunden: 1146 Tabelle &#39;db_name.catalog_product_index_price_cg0_ws0&#39; existiert nicht in /home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90
    &quot;

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]**.
1. Erweitern Sie im linken Bereich **[!UICONTROL Catalog]** und wählen Sie **[!UICONTROL Catalog]** aus den unten stehenden Optionen aus.
1. Scrollen Sie nach unten zum Abschnitt **[!UICONTROL Price]** und legen Sie **[!UICONTROL Catalog Price Scope]** auf **[!UICONTROL Global]** fest.
1. Legen Sie `Indexer dimension mode` mithilfe des folgenden Befehls auf `website_and_customer_group` fest:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. Erstellen Sie eine **[!UICONTROL Bundle Product]** mit dem Bundle-Optionstyp `Checkbox` oder `Multi Select` und weisen Sie das Produkt einer Kategorie zu.
1. Navigieren Sie zu **[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]**.
1. Wählen Sie die Kategorie aus, der das erstellte Produkt zugewiesen ist, und versuchen Sie, es zu **[!UICONTROL Save]**.

<u>Erwartete Ergebnisse</u>:

Produkt ohne Fehler hinzugefügt.

<u>Tatsächliche Ergebnisse</u>:

Ein Produkt kann nicht über [!DNL Page Builder] hinzugefügt werden, wenn der **[!UICONTROL Bundle Product]** Optionstyp `Checkbox` oder `Multi Select` ist und `indexer dimension mode` auf `website_and_customer_group` gesetzt ist. Es wird der Fehler ausgegeben *„Beim Generieren dieses Inhalts ist leider ein Fehler aufgetreten*.


## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
