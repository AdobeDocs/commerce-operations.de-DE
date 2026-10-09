---
title: 'ACSD-56741: Fehlerbehebung bei Datenbanksetup-Fehlern mit benutzerdefinierten MySQL-Triggern'
description: Wenden Sie den Patch ACSD-56741 an, um das Adobe Commerce-Problem zu beheben, bei dem während „setup:upgrade“ eine Fehlermeldung „Zugriff auf Array-Offset mit dem Wert null“ angezeigt wird, da ein benutzerdefinierter MySQL-Trigger in der Datenbank nicht mit der Indizierung und [!DNL MView] in Verbindung steht.
feature: Install
role: Admin, Developer
exl-id: 93a1c75f-8a45-49df-9fa4-6ba1234c822d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%
---
# ACSD-56741: Fehlerbehebung bei Datenbanksetup-Fehlern mit benutzerdefinierten MySQL-Triggern

Der Patch ACSD-56741 behebt das Problem, dass *Fehlermeldung „Zugriff auf Array-Offset bei Wert vom Typ null“* der `setup:upgrade` angezeigt wird, da ein benutzerdefinierter MySQL-Trigger in der Datenbank nicht mit der Indizierung und [!DNL MView] in Zusammenhang steht. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48 installiert ist. Die Patch-ID ist ACSD-56741. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei der `setup:upgrade` wird *Fehlermeldung „Zugriff auf den Array-Offset bei einem Wert vom Typ null* angezeigt, da ein benutzerdefinierter MySQL-Trigger in der Datenbank nicht mit der Indizierung und der [!DNL MView] in Zusammenhang steht.

<u>Schritte zur Reproduktion</u>:

1. `php bin/magento indexer:set-mode schedule` ausführen.

   ```text
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. `php bin/magento c:f` ausführen.
1. `php bin/magento setup:upgrade` ausführen.

<u>Erwartete Ergebnisse</u>:

Das Setup-Upgrade wird fehlerfrei abgeschlossen.

<u>Tatsächliche Ergebnisse</u>:

Das Setup-Upgrade wird mit einer Fehlermeldung beendet:

*Warnung: Versuch, auf den Array-Offset für einen Wert vom Typ null zuzugreifen*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
