---
title: 'MDVA-42689: Beim Aktualisieren von Produktkategorien während des Imports wird Benutzern der Fehler „Verletzung der Integritätsbeschränkung“ angezeigt'
description: Mit dem Patch MDVA-42689 wird das Problem behoben, dass beim Aktualisieren von Produktkategorien während des Imports ein Fehler wegen Verletzung der Integritätsbedingung angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42689. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: 3f81f195-5a95-45f6-8970-403b8398e759
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-42689: Beim Aktualisieren von Produktkategorien während des Imports wird Benutzern der Fehler „Verletzung der Integritätsbeschränkung“ angezeigt

Mit dem Patch MDVA-42689 wird das Problem behoben, dass beim Aktualisieren von Produktkategorien während des Imports ein Fehler wegen Verletzung der Integritätsbedingung angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 installiert ist. Die Patch-ID lautet MDVA-42689. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Adobe Commerce gibt beim Aktualisieren von Produktkategorien während des Imports einen Fehler wegen Verletzung der Integritätsbedingung aus.

<u>Schritte zur Reproduktion</u>:

1. Richten Sie zwei Websites ein.
1. Erstellen Sie Unterkategorien unter der Stammkategorie mit bis zu zwei Ebenen auf der Kategorieseite. Beispiel: Stammkategorie > &quot;**&quot;** &quot;**Uhren**.
1. Erstellen Sie zwei einfache Produkte und weisen Sie beide Produkte derselben Kategorie **Zahnrad** > **Uhren** zu.
1. Weisen Sie beiden Websites ein einfaches Produkt zu.
1. Speichern Sie das Produkt.
1. Bereiten Sie eine CSV-Datei für den Import vor. Es sollte zwei Produktdatensätze mit verschiedenen Store-Ansichten geben. Eines der Produkte sollte zu diesen beiden Store-Ansichten gehören.
1. Importieren Sie jetzt die CSV-Datei, indem Sie zu **System** > **Import** > **Entitätstyp** (Produkte) navigieren.

<u>Erwartete Ergebnisse</u>:

CSV-Datei wird fehlerfrei importiert.

<u>Tatsächliche Ergebnisse</u>:

Adobe Commerce gibt den folgenden Fehler aus:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
