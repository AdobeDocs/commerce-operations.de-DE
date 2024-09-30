---
title: '"ACSD-56741: Fehlerbehebung bei Datenbanksetup-Fehlern mit benutzerdefinierten MySQL-Triggern'
description: Wenden Sie den Patch ACSD-56741 an, um das Adobe Commerce-Problem zu beheben, bei dem während des "setup:upgrade"-Vorgangs eine Fehlermeldung angezeigt wird *Versuchen, auf den Array-Offset vom Typ null zuzugreifen* aufgrund eines benutzerspezifischen MySQL-Triggers in der Datenbank, der nicht mit der Indizierung und  [!DNL MView] in Zusammenhang steht.
feature: Install
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56741: Fehlerbehebung bei Datenbanksetup-Fehlern mit benutzerdefinierten MySQL-Triggern

Der Patch ACSD-56741 behebt das Problem, dass während `setup:upgrade` aufgrund eines benutzerspezifischen MySQL-Triggers in der Datenbank, der nicht mit der Indizierung und dem [!DNL MView] in Zusammenhang steht, die Fehlermeldung &quot;*Versuchen, auf den Array-Offset vom Typ null* zuzugreifen&quot; angezeigt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.48 installiert ist. Die Patch-ID ist ACSD-56741. Bitte beachten Sie, dass das Problem in Adobe Commerce 2.5.0 behoben werden soll.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6 - p4

>[!NOTE]
>
>Der Patch kann für andere Versionen mit neuen [!DNL Quality Patches Tool] -Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das Paket `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchschlüsselwort, um den Patch zu finden.

## Problem

Während `setup:upgrade` wird eine Fehlermeldung *Versuchen, auf den Array-Offset vom Typ null zuzugreifen, angezeigt, da ein benutzerdefinierter MySQL-Trigger in der Datenbank nicht mit Indizierung und [!DNL MView] in Zusammenhang steht.*

<u>Zu reproduzierende Schritte</u>:

1. Führen Sie `php bin/magento indexer:set-mode schedule` aus.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Führen Sie `php bin/magento c:f` aus.
1. Führen Sie `php bin/magento setup:upgrade` aus.

<u>Erwartete Ergebnisse</u>:

Das Setup-Upgrade wird ohne Fehler beendet.

<u>Tatsächliche Ergebnisse</u>:

Das Setup-Upgrade wird mit einer Fehlermeldung beendet:

*Warnung: Versuchen Sie, auf den Array-Versatz für den Wert des Typs null* zuzugreifen.

## Wenden Sie den Patch an

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source vor Ort: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool]-Handbuch.
* Adobe Commerce auf Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch Commerce on Cloud Infrastructure.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] release: ein neues Tool zur Selbstbedienung von Qualitäts-Patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie mithilfe von  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) im [!UICONTROL Quality Patches Tool] -Handbuch, ob ein Patch für Ihr Adobe Commerce-Problem verfügbar ist.


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool] -Handbuch.
