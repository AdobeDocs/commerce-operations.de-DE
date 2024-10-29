---
title: '"ACSD-59786: GraphQL gibt einen Fehler zurück, wenn "quote_id"für ein abgelaufenes Anführungszeichen abgerufen wird."'
description: Wenden Sie den Patch ACSD-59786 an, um das Adobe Commerce-Problem zu beheben, bei dem eine GraphQL-Abfrage einen Fehler zurückgibt, wenn ein "Anführungszeichen_ID"für ein abgelaufenes Anführungszeichen abgerufen wird.
feature: GraphQL, Quotes, Companies
role: Admin, Developer
source-git-commit: d3634071bbeed6e62e89c9d5c46c6635132c06cd
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786: GraphQL gibt beim Abrufen eines `quote_id` für ein abgelaufenes Anführungszeichen einen Fehler zurück

Der Patch ACSD-59786 behebt das Problem, bei dem eine GraphQL-Abfrage einen Fehler zurückgibt, wenn ein `quote_id` für ein abgelaufenes Anführungszeichen abgerufen wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 installiert ist. Die Patch-ID ist ACSD-59786. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.8 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Eine GraphQL-Abfrage gibt einen Fehler zurück, wenn ein `quote_id` für ein abgelaufenes Anführungszeichen abgerufen wird.

<u>Zu reproduzierende Schritte</u>:

1. Aktivieren Sie **[!UICONTROL Companies]** und **[!UICONTROL Purchase Orders]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** und setzen **[!UICONTROL Enable Company]** auf *Ja*.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]** und setzen **[!UICONTROL Enable Purchase Orders]** auf *Ja*.
1. Erstellen Sie ein neues Unternehmen und legen Sie **[!UICONTROL Enable Purchase Orders]** für dasselbe auf *Ja* fest.
1. Erstellen Sie ein einfaches Produkt und weisen Sie es einer Kategorie zu.
1. Melden Sie sich mit dem Unternehmensadministratorkonto bei Storefront an und erstellen Sie eine neue Bestellung mit **[!UICONTROL Purchase Order]** als Zahlungsmethode.
1. Ändern Sie die **[!UICONTROL Quote Lifetime (days)]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. Führen Sie den Befehl `bin/magento c:f` aus.
1. Wechseln Sie zur DB `quote_table` und ändern Sie die `created_at` - und `updated_at` -Werte mit einem Tag in der Vergangenheit.
1. Führen Sie den Befehl `bin/magento cron:run --group="sales_clean_quotes` aus.
1. Führen Sie die unten angegebene GraphQL-Anfrage mit einem autorisierten Token für den Administrator aus, der die **[!UICONTROL Purchase Order]** erstellt:

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>Erwartete Ergebnisse</u>:

Die GraphQL-Abfrage gibt die `quote_id` zurück.

<u>Tatsächliche Ergebnisse</u>:

Die GraphQL-Abfrage gibt einen internen Serverfehler zurück.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
