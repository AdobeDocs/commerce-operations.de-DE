---
title: 'ACSD-48417: SQL-Fehler nach der Erstellung einer Zeitplanänderung'
description: Wenden Sie den Patch ACSD-48417 an, um das Adobe Commerce-Problem zu beheben, bei dem nach dem Erstellen einer Produktplanänderung und dem Speichern eines anderen Produkts ein SQL-Fehler angezeigt wird.
feature: Storage
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-48417: SQL-Fehler nach der Erstellung einer Zeitplanänderung

Der Patch ACSD-48417 behebt das Problem, dass nach dem Erstellen einer Zeitplanänderung für ein Produkt und dem Speichern eines anderen Produkts ein SQL-Fehler angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID lautet ACSD-48417. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben sein soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Nach dem Erstellen einer Planungsänderung für ein Produkt und dem Speichern eines anderen Produkts wird ein SQL-Fehler angezeigt.

<u>Zu reproduzierende Schritte</u>:

1. Installieren Sie Magento 2.4-develop EE + Sample Data.
1. Gehen Sie zum Admin-Bedienfeld > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Bearbeiten Sie ein beliebiges Produkt (z. B. Joust Duffle Bag [SKU: 24-MB01]).
1. Planen Sie eine neue Aktualisierung:
   * Wählen Sie **[!UICONTROL Save as a New Update]**
   * Aktualisierungsname: &quot;Update 1&quot;
   * Startdatum: aktuelle Zeit +1 Min.
   * Enddatum: aktuelle Zeit: +1 Stunde
   * Ändern Sie den Produktnamen in &quot;Joust Duffle Bag 2&quot;.
   * Speichern Sie das Produkt.
1. Gehen Sie zur CLI und führen Sie cron aus und warten Sie, bis der Zeitplan angewendet wird.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. Gehen Sie erneut zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und bearbeiten Sie jedes konfigurierbare Produkt (z. B. Chaz Kangeroo Hoodie [SKU: MH01]).

   * Deaktivieren Sie alle Varianten. Gehen Sie zur Spalte Aktionen > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Speichern Sie den konfigurierbaren.

<u>Erwartete Ergebnisse</u>:

Kein Fehler beim Speichern des Produkts.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt auf:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
