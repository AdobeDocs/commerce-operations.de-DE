---
title: 'ACSD-52815: Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle unterstützt nur bis zu 6 Stellen'
description: Wenden Sie den Patch ACSD-52815 an, um das Leistungsproblem von Adobe Commerce zu beheben, bei dem das Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu 6 Stellen unterstützt, im Gegensatz zu 8 für einen Standardbestand.
feature: Inventory, Products
role: Admin
exl-id: d863af1f-8a7f-4a43-893e-54525ab68cd7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-52815: Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle unterstützt nur bis zu 6 Stellen

Der Patch ACSD-52815 behebt das Problem, dass das Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle nur bis zu 6 Stellen unterstützt, im Gegensatz zu 8 für einen Standardbestand. Dieser Patch ist verfügbar, wenn [!DNL Quality Patches Tool (QPT)] 1.1.35 installiert ist. Die Patch-ID ist ACSD-52815. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Eingabefeld für das Mengenfeld einer nicht standardmäßigen Quelle unterstützt nur bis zu 6 Stellen, im Gegensatz zu 8 für einen Standardbestand.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein neues Lager und eine neue Quelle.
1. Erstellen Sie ein Produkt mit einem neuen Quellbestand von 123.
1. Überprüfen Sie die verkaufsfähige Menge (123).
1. Quellmenge auf 12345678 aktualisieren.
1. Die zu verkaufende Menge erneut überprüfen.

<u>Erwartete Ergebnisse</u>:

Die verkaufbare Menge zeigt die richtige Menge an.

<u>Tatsächliche Ergebnisse</u>:

Die verkaufsfähige Menge beträgt 999999.9999.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
