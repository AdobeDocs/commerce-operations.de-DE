---
title: 'MDVA-37234: Beim mehrmaligen Hinzufügen eines Artikels zum Warenkorb wird ein doppelter Zeileneintrag erstellt'
description: Der Patch MDVA-37234 behebt das Problem, dass beim mehrmaligen Hinzufügen eines Artikels zum Warenkorb (parallele Anfrage) für dieselbe SKU ein doppelter Zeileneintrag für dieselbe Warenkorb-ID erstellt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-37234. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Orders, Shopping Cart
role: Admin
exl-id: d4e9fca1-7fba-4a33-9c5e-c9695cbfc61c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '504'
ht-degree: 0%
---
# MDVA-37234: Beim mehrmaligen Hinzufügen eines Artikels zum Warenkorb wird ein doppelter Zeileneintrag erstellt

Der Patch MDVA-37234 behebt das Problem, dass beim mehrmaligen Hinzufügen eines Artikels zum Warenkorb (parallele Anfrage) für dieselbe SKU ein doppelter Zeileneintrag für dieselbe Warenkorb-ID erstellt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.3 installiert ist. Die Patch-ID lautet MDVA-37234. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.6, 2.4.1 und 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.3.5 - 2.3.7-p1 und 2.4.1 - 2.4.2-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn Sie einen Artikel mehrmals zum Warenkorb hinzufügen (parallele Anfrage), wird für dieselbe SKU ein doppelter Zeileneintrag für dieselbe Warenkorb-ID erstellt.

<u>Schritte zur Reproduktion</u>:

1. Einfaches Produkt mit SKU = simple1 erstellen.
1. Erstellen Sie einen Kunden.
1. Generieren Sie ein Kunden-Token für die GraphQL-Anfrage.

   <pre>
    <code class="language-graphql">
    mutation {
        generateCustomerToken(
            email: "customer email"
            password: "customer password"
        )
        {
            token
        }
    }
    </code>
    </pre>

1. Verwenden Sie das in Schritt 3 erwähnte Token, um einen leeren Warenkorb für den Kunden zu erstellen.

   <pre>
    <code class="language-graphql">
    mutation{
     createEmptyCart
    }
    </code>
    </pre>

1. Erstellen Sie ein Skript, um zwei `addSimpleProductsToCart` parallel auszuführen. Beispiel:

   <pre>
    <YOUR_ACCESS_TOKEN><YOUR_CART_ID><YOUR_ACCESS_TOKEN><YOUR_CART_ID>
    </pre>

1. Führen Sie das Skript aus.

<u>Erwartete Ergebnisse</u>:

Im Warenkorb wird nur eine Produktlinie mit einer Gesamtmenge (in diesem Fall drei) erstellt.

<u>Tatsächliche Ergebnisse</u>:

Im Warenkorb werden zwei separate Zeilen für dasselbe Produkt erstellt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu Qualitäts-Patches für Adobe Commerce finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
