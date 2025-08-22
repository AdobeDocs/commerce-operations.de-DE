---
title: 'ACSD-66889: Fehler bei der Neuindizierung des Bestands in CLI'
description: Wenden Sie den Patch ACSD-66889 an, um das Adobe Commerce-Problem zu beheben, das beim Ausführen des Inventar-Indexers einen Fehler Trigger.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9631e0864b2ad8fc09734aedd476e96852cd70fb
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# ACSD-66889: Fehler bei der Neuindizierung des Bestands in CLI

Der Patch ACSD-66889 behebt den Fehler, der beim Ausführen des Inventar-Indexers auftritt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 installiert ist. Die Patch-ID ist ACSD-66889.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p8

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.5-p13

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Ausführen des Inventarindexers gibt der Prozess eine Warnung aus, dass der Vorgang veraltet ist und aufgrund einer veralteten Zeichenfolgensyntax nicht abgeschlossen werden kann.

<u>Schritte zur Reproduktion</u>:

1. Führen Sie die Inventar-Neuindizierung mithilfe des CLI-Befehls aus:

   ```
   php bin/magento indexer:reindex inventory
   ```

<u>Erwartete Ergebnisse</u>:

Die CLI erstellt den Inventar-Indexer erfolgreich neu.

<u>Tatsächliche Ergebnisse</u>:

Die CLI gibt einen Fehler mit veralteter Funktionalität aus, und die Inventarindizes verbleiben im Status *Neuindizierung erforderlich*:

```
Deprecated Functionality: Using ${var} in strings is deprecated, use {$var} instead in /home/vendor/magento/module-elasticsearch-catalog-permissions/Model/Adapter/FieldMapper/Product/FieldProvider/FieldName/Resolver/CategoryPermission.php on line 24
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
