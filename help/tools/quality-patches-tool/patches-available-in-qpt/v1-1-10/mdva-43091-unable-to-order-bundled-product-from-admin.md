---
title: 'MDVA-43091: Gebündeltes Produkt kann nicht vom Administrator bestellt werden'
description: Der Patch MDVA-43091 löst das Problem, dass Benutzende gebündelte Produkte nicht über Commerce Admin bestellen können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43091. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: d2812f97-107c-4db9-93cc-7004344fcc95
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-43091: Gebündeltes Produkt kann nicht vom Administrator bestellt werden

Der Patch MDVA-43091 löst das Problem, dass Benutzende gebündelte Produkte nicht über Commerce Admin bestellen können. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-43091. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Beim Versuch, ein gebündeltes Produkt vom Administrator zu bestellen, wird der folgende Fehler ausgegeben: *Sie können für dieses Produkt keine Dezimalmenge verwenden.*

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine saubere Adobe Commerce.
1. Erstellen Sie zwei einfache Produkte.
1. Erstellen Sie ein gebündeltes Produkt mit zwei Optionen.
1. Erstellen Sie ein Kundenkonto im Frontend.
1. Wechseln Sie **Admin** > **Verkauf** > **Bestellungen** > **Neuen Auftrag erstellen**.
   * Wählen Sie das soeben erstellte Kundenkonto aus.
   * Versuchen Sie, das gebündelte Produkt zum Warenkorb hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Der Administrator kann dem Warenkorb das Produkt mit einer Menge hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

Admin-Benutzende erhalten die folgende Fehlermeldung: *Sie können für dieses Produkt keine Dezimalzahl verwenden.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
