---
title: 'MDVA-43983: Produkte, die als „Nicht einzeln sichtbar“ festgelegt sind, werden in den Suchergebnissen angezeigt'
description: Der MDVA-43983 Patch löst das Problem, dass die Produkte, die als „Nicht einzeln sichtbar“ festgelegt sind, weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43983. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43983: Produkte, die als „Nicht einzeln sichtbar“ festgelegt sind, werden in den Suchergebnissen angezeigt

Der MDVA-43983 Patch löst das Problem, dass die Produkte, die als „Nicht einzeln sichtbar“ festgelegt sind, weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt werden. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 installiert ist. Die Patch-ID lautet MDVA-43983. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Produkte, die als „Nicht einzeln sichtbar“ festgelegt sind, werden weiterhin in den erweiterten Suchergebnissen des Katalogs angezeigt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Attribut mit **Katalogeingabetyp für Store** Inhaber als **Dropdown** oder **Visual Swatch** (z. B. Color).
1. Legen **In der Suche verwenden** als **Ja** und **Sichtbar in der erweiterten Suche** als **Ja** fest.
1. Einige Attributoptionen hinzufügen.
1. Erstellen Sie Produkte mit **Sichtbarkeit** als **Nicht einzeln sichtbar**.
1. Zuweisen von Farbattributoptionen.
1. Navigieren Sie zur Seite **Erweiterte** im Schaufenster.
1. Wählen Sie nur die Option Farbattribut aus dem Feld Farbattribut und lassen Sie den Rest der Felder leer oder so, wie er ist.
1. Senden Sie ein Formular für die erweiterte Suche.
1. Beobachten Sie die Suchergebnisse.

<u>Erwartete Ergebnisse</u>:

Produkte, die als „Nicht einzeln sichtbar“ festgelegt sind, werden nicht in den erweiterten Suchergebnissen des Katalogs angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Produkte, die als „Nicht einzeln sichtbar“ festgelegt sind, werden in den erweiterten Suchergebnissen des Katalogs angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
