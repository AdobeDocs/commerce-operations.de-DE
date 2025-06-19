---
title: 'ACSD-65787: SchemaBuilder stürzt bei der Schemaerstellung oder -aktualisierung aufgrund des nicht definierten Array-Schlüssels „column“ in den Tabellendaten ab'
description: Wenden Sie den Patch ACSD-65787 an, um das Adobe Commerce-Problem zu beheben, bei dem die SchemaBuilder-Klasse bei der Schemaerstellung oder bei Aktualisierungen aufgrund einer nicht definierten Array-Schlüsselspalte bei der Verarbeitung von Tabellendaten abstürzt.
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-65787: `SchemaBuilder` stürzt bei der Schemaerstellung oder -aktualisierung aufgrund eines nicht definierten Array-Schlüssels „column“ in den Tabellendaten ab

Der Patch ACSD-65787 behebt das Problem, dass `SchemaBuilder` Klasse bei der Schemaerstellung oder bei Aktualisierungen aufgrund einer nicht definierten Array-Schlüssel-„Spalte“ bei der Verarbeitung von Tabellendaten abstürzt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 installiert ist. Die Patch-ID ist ACSD-65787. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die `SchemaBuilder`-Klasse stürzt bei der Erstellung eines Schemas ab oder wird aufgrund einer „Spalte“ des nicht definierten Array-Schlüssels bei der Verarbeitung von Tabellendaten aktualisiert.

<u>Schritte zur Reproduktion</u>:

1. Führen Sie den folgenden Befehl aus:

```
bin/magento setup:upgrade
```

<u>Erwartete Ergebnisse</u>:

Keine Fehler.

<u>Tatsächliche Ergebnisse</u>:

```
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
