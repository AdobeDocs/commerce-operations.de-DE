---
title: 'MDVA-37592: Sortierung nach Preis funktioniert nicht für Produkte mit Preis Null'
description: Der MDVA-37592 Adobe Commerce Patch löst das Problem, dass die Sortierung nach Preis bei Produkten mit einem Preis Null, der einem freigegebenen Katalog zugewiesen ist, nicht korrekt funktioniert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-37592. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-37592: Sortierung nach Preis funktioniert nicht für Produkte mit Preis Null

Der MDVA-37592 Adobe Commerce Patch löst das Problem, dass die Sortierung nach Preis bei Produkten mit einem Preis Null, der einem freigegebenen Katalog zugewiesen ist, nicht korrekt funktioniert. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 installiert ist. Die Patch-ID lautet MDVA-37592. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce auf unserer Cloud-Architektur 2.4.0-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungstypen) 2.3.6-2.4.2-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Sortierung nach Preis funktioniert bei Produkten mit einem Preis Null, der einem freigegebenen Katalog zugewiesen ist, nicht ordnungsgemäß.

<u>Voraussetzungen</u>:

B2B ist installiert.

<u>Schritte zur Reproduktion</u>:

1. Freigegebenen Katalog aktivieren.
1. Erstellen Sie vier Produkte mit den folgenden Preisen und weisen Sie sie einer Kategorie zu: 50 $, 60 $, 70 $ und 80 $.
1. Erstellen Sie einen freigegebenen Katalog mit den oben genannten Produkten.
1. Setzen Sie den benutzerdefinierten Preis für das Produkt mit einem Preis von 70 $ auf null.
1. Erstellen Sie nun einen Firmenbenutzer und weisen Sie ihn dem soeben erstellten freigegebenen Katalog zu.
1. Melden Sie sich mit dem Unternehmenskonto an und navigieren Sie zur Kategorie, der die Produkte zugewiesen sind.
1. Sortieren Sie nach Preis.

<u>Erwartete Ergebnisse</u>:

Das Produkt mit dem Preis Null wird korrekt sortiert.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt mit dem Preis Null wird NICHT korrekt sortiert. Stattdessen wird nach dem ursprünglichen Preis sortiert.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!DNL Quality Patches Tool].

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
