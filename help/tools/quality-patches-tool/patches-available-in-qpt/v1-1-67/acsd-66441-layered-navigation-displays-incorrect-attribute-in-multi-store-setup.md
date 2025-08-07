---
title: 'ACSD-66441: Die mehrschichtige Navigation zeigt falsche Attributoptionen bei der Einrichtung mehrerer Stores an'
description: Wenden Sie den ACSD-66441-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem in der mehrschichtigen Navigation Attribute aus anderen Stores in einer Multi-Store-Einrichtung falsch angezeigt werden.
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
source-git-commit: 5a8b30d1fac953ff5d921b7a7d3f12619b03bc81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# ACSD-66441: Die mehrschichtige Navigation zeigt falsche Attributoptionen bei der Einrichtung mehrerer Stores an

Mit dem Patch ACSD-66441 wird das Problem behoben, dass bei der mehrschichtigen Navigation Attribute aus anderen Stores in einer Multi-Store-Einrichtung falsch angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 installiert ist. Die Patch-ID ist ACSD-66441. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die mehrschichtige Navigation in der Storefront enthält Attributwerte aus anderen Stores, auch wenn diese Produkte in der aktuellen Store-Ansicht nicht verfügbar sind.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine sekundäre Website-, Store- und Store-Ansicht.
1. Erstellen Sie ein konfigurierbares Produkt mit einem benutzerdefinierten Attribut (z. B. Größe).
1. Weisen Sie das konfigurierbare Produkt der Haupt-Website und einer Kategorie zu.
1. Alle Daten neu indizieren.
1. Navigieren Sie zur zugewiesenen Kategorie in der Storefront. Alle Größenoptionen werden in der mehrschichtigen Navigation korrekt angezeigt.
1. Heben Sie die Zuweisung von zwei einfachen Produkten zur Haupt-Website auf und weisen Sie sie der sekundären Website zu, oder entfernen Sie sie aus der Haupt-Website.
1. Alle Daten neu indizieren.
1. Rufen Sie erneut die Kategorieseite der Storefront auf und überprüfen Sie die mehrschichtige Navigation.

<u>Erwartete Ergebnisse</u>:

In der mehrschichtigen Navigation werden nur Attributoptionen aus Produkten angezeigt, die dem aktuellen Store oder der aktuellen Website zugewiesen sind.

<u>Tatsächliche Ergebnisse</u>:

Die mehrschichtige Navigation zeigt Attributoptionen (Größen) aus Produkten an, die anderen Stores oder Websites zugewiesen sind.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
