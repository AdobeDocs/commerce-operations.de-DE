---
title: 'MDVA-41399: Zugriff auf „Warenkorb verwalten“ nicht möglich, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt'
description: Der MDVA-41399 Patch löst das Problem, dass Admin-Benutzer nicht auf die Seite Warenkorb verwalten zugreifen können, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-41399. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%
---
# MDVA-41399: Zugriff auf „Warenkorb verwalten“ nicht möglich, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt

Der MDVA-41399 Patch löst das Problem, dass Admin-Benutzer nicht auf die Seite Warenkorb verwalten zugreifen können, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-41399. Beachten Sie, dass das Problem in Adobe Commerce 2.4.2 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Admin-Benutzende können nicht auf die Seite Warenkorb verwalten zugreifen, wenn ein Kunde ein Produkt zur Wunschliste hinzufügt.

<u>Voraussetzungen</u>:

1. Erstellen Sie zwei oder mehr Produkte.
1. Erstellen Sie einen Kunden.
1. Aktivieren Sie den Entwicklermodus.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Storefront und melden Sie sich von den Voraussetzungen aus als Kunde an.
1. Produkt zur Wunschliste hinzufügen.
1. Gehen Sie zum Admin-Bedienfeld, navigieren Sie zur erstellten Seite für die Kundenbearbeitung und klicken Sie auf die Schaltfläche **Warenkorb verwalten**.

<u>Erwartete Ergebnisse</u>:

Ein Administrator kann den Warenkorb verwalten.

<u>Tatsächliche Ergebnisse</u>:

Admin-Benutzer erhält eine Fehlermeldung: *Ein Fehler ist aufgetreten. Weitere Informationen finden Sie im Fehlerprotokoll.*

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
