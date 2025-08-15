---
title: 'ACSD-51884: Cache-Pfad der Produktbilder ist bei dem Befehl zur Größenanpassung falsch'
description: Wenden Sie den Patch ACSD-51884 an, um das Adobe Commerce-Problem zu beheben, bei dem der Cache-Pfad für das Produktbild nach Ausführung des Befehls resize falsch wird.
feature: Products
role: Admin
exl-id: a3779e4b-2749-460e-a0a8-656b26bb06fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-51884: Cache-Pfad der Produktbilder ist bei dem Befehl zur Größenanpassung falsch

Der Patch ACSD-51884 behebt das Problem, dass ein interner Fehler auftritt, bei dem der Cache-Pfad für das Produktbild nach Ausführung des Befehls resize falsch wird. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.37 installiert ist. Die Patch-ID ist ACSD-51884. Beachten Sie, dass das Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.7

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Pfad des Produktbild-Caches wird beim Befehl zur Größenanpassung falsch.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Website/einen neuen Store/eine neue Storeview.
1. Erstellen Sie ein Produkt, weisen Sie es beiden Websites zu und laden Sie das Produktbild hoch.
1. Erstellen Sie ein neues Design (siehe angehängte Adobe.zip).
1. `app/design/Adobe/theme/etc/view.xml`:

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

nach

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. Wenden Sie das Design auf die zuvor erstellte Storeview an.
1. Überprüfen Sie die Produktseite auf der 2. Website. Das Produktbild wird korrekt angezeigt.
1. Flush-Cache verwenden:
   `bin/magento cache:flush`
1. Überprüfen Sie die Produktseite auf der 2. Website.

<u>Erwartete Ergebnisse</u>:

Das Produktbild wird korrekt angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Das Produktbild existiert nicht.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
