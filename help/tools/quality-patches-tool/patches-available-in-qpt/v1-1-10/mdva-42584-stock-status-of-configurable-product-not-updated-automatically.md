---
title: 'MDVA-42584: Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert'
description: Der MDVA-42584 Patch löst das Problem, dass der Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert wird, wenn sein einfaches Produkt aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42584. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Configuration, Orders, Products
role: Admin
exl-id: 6311f069-f08f-4d58-9f4b-fa1246c02640
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
source-wordcount: '553'
ht-degree: 0%
---
# MDVA-42584: Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert

Der MDVA-42584 Patch löst das Problem, dass der Lagerstatus des konfigurierbaren Produkts nicht automatisch aktualisiert wird, wenn sein einfaches Produkt aktualisiert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-42584. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Lagerstatus des konfigurierbaren Produkts im Backend wird nicht automatisch aktualisiert, wenn sein einfaches Produkt über API oder Import auf **Auf Lager** eingestellt ist.

<u>Voraussetzungen</u>:

MSI installiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt, **InvCheck001**, mit zwei Optionen: **InvCheck001-M** und **InvCheck001-L**.
1. Beide einfachen Produkte sollten über „Menge“ verfügen und **„Auf Lager** sein, sodass das konfigurierbare Produkt auch **Auf Lager** im Backend ist.
1. Aktualisieren Sie jetzt sowohl die einfachen Produkte als auch die Menge auf **0** und den Lagerstatus auf **Nicht vorrätig**.
1. Aktualisieren Sie das konfigurierbare Produkt und überprüfen Sie, ob der Lagerstatus auf &quot;**&quot;**.
1. Verwenden Sie den folgenden API-Endpunkt und setzen Sie das einfache Produkt **InvCheck001-M** auf **Auf Lager** mit Menge > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Gehen Sie zum Backend und überprüfen Sie die Menge und den Lagerstatus des einfachen Produkts **InvCheck001-M**. Es wird auf &quot;**&quot;**.
1. Aktualisieren Sie das konfigurierbare Produkt und überprüfen Sie den Lagerstatus.

<u>Erwartete Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts **InvCheck001** im Backend wird automatisch auf &quot;**&quot;**.

<u>Tatsächliche Ergebnisse</u>:

Der Lagerstatus des konfigurierbaren Produkts ist weiterhin **Nicht vorrätig**.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
