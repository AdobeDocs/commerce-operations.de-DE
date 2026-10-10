---
title: 'ACSD-45241: Lagermenge des virtuellen Produkts falsch berechnet'
description: Mit dem Patch ACSD-45241 wird das Problem behoben, dass die Lagermenge des virtuellen Produkts nach dem Erstellen einer Gutschrift falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 installiert ist. Die Patch-ID ist ACSD-45241. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.
feature: Orders, Products
role: Admin
exl-id: 447a84f0-aab4-4bb1-9f06-c056c006cd69
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%
---
# ACSD-45241: Lagermenge des virtuellen Produkts falsch berechnet

Mit dem Patch ACSD-45241 wird das Problem behoben, dass die Lagermenge des virtuellen Produkts nach dem Erstellen einer Gutschrift falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.17 installiert ist. Die Patch-ID ist ACSD-45241. Beachten Sie, dass das Problem in Adobe Commerce 2.4.4 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.4.4

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Lagermenge für ein virtuelles Produkt wird nach der Erstellung einer Gutschrift falsch berechnet.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit einem Virtual Product als untergeordnetes Produkt in Commerce Admin.
1. Stellen Sie sicher, dass beide in Schritt 1 erstellten Produkte vorrätig sind.
1. Markieren Sie die Menge für das in Schritt 1 erstellte virtuelle Produkt mit 100 und behalten Sie auch die verkaufsfähige Menge mit 100 bei.
1. Fügen Sie das Produkt zum Warenkorb hinzu.
1. Geben Sie eine Bestellung mit dem in Schritt 1 erstellten virtuellen Produkt auf.
1. Behalten Sie den Bestellstatus als „Ausstehend“ bei. Keine Notwendigkeit, die Zahlung zu bearbeiten.
1. `order_created` Datensatz in `inventory_reservation` erstellt. Die virtuelle Produktmenge zeigt 100 mit verkaufsfähiger Menge als 99.
1. Öffnen Sie die Bestellung und gehen Sie zu **Rechnung** > **Rechnung senden**.
1. `invoice_created` Datensatz in `inventory_reservation` erstellt. Die virtuelle Produktmenge beträgt nun 99, die verkaufsfähige Menge ebenfalls 99.
1. Erstellen Sie eine Gutschrift ohne Auswahl von **Zurück an Lager**.

<u>Erwartete Ergebnisse</u>:

In `inventory_reservation` wird kein neuer Datensatz erstellt und die Lagermenge für das virtuelle Produkt bleibt unverändert.

<u>Tatsächliche Ergebnisse</u>:

In `inventory_reservation` wird ein `creditmemo_created` Datensatz erstellt, und die virtuelle Produktlagermenge wird auf 98 angepasst, wobei die verkaufsfähige Menge 99 beträgt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
