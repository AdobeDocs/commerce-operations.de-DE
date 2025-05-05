---
title: 'ACSD-48417: SQL-Fehler nach der Erstellung einer Zeitplanänderung'
description: Wenden Sie den Patch ACSD-48417 an, um das Adobe Commerce-Problem zu beheben, bei dem ein SQL-Fehler auftritt, nachdem eine Zeitplanänderung für ein Produkt erstellt und ein anderes Produkt gespeichert wurde.
feature: Storage
role: Admin
exl-id: c8e7c7aa-ac53-4218-8c3c-ea2240af17c9
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-48417: SQL-Fehler nach der Erstellung einer Zeitplanänderung

Der Patch ACSD-48417 behebt das Problem, dass ein SQL-Fehler auftritt, nachdem eine Zeitplanänderung für ein Produkt erstellt und ein anderes Produkt gespeichert wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26 installiert ist. Die Patch-ID ist ACSD-48417. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Nach dem Erstellen einer Zeitplanänderung für ein Produkt und dem Speichern eines anderen Produkts wird ein SQL-Fehler angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Installieren von Magento 2.4-develop EE + Beispieldaten.
1. Navigieren Sie zum Admin-Bedienfeld > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Bearbeiten eines beliebigen Produkts (z. B. Joust Duffle Bag [SKU: 24-MB01]).
1. Neue Aktualisierung planen:
   * **[!UICONTROL Save as a New Update]** auswählen
   * Name der Aktualisierung: „Update 1“
   * Startdatum: aktuelle Zeit +1 Min
   * Enddatum: aktuelle Zeit +1 Stunde
   * Ändern Sie den Produktnamen in: „Joust Duffle Bag 2“
   * Speichern Sie das Produkt.
1. Wechseln Sie zu CLI und führen Sie cron aus. Warten Sie, bis der Zeitplan angewendet wird.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. Wechseln Sie erneut zu **[!UICONTROL Catalog]** > **[!UICONTROL Products]** und bearbeiten Sie jedes konfigurierbare Produkt (z. B. Chaz Kangeroo Hoodie [SKU: MH01]).

   * Deaktivieren Sie alle Varianten. Gehen Sie zur Spalte Aktionen > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Speichern Sie die konfigurierbare Datei.

<u>Erwartete Ergebnisse</u>:

Kein Fehler beim Speichern des Produkts.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler tritt auf:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
