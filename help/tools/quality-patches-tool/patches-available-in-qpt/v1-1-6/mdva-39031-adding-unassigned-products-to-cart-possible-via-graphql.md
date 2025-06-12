---
title: 'MDVA-39031: Hinzufügen nicht zugewiesener Produkte zum Warenkorb über GraphQL möglich'
description: Der MDVA-39031 Patch löst das Problem, dass das Hinzufügen eines Produkts zum Warenkorb über GraphQL möglich ist, auch wenn es nicht der Ziel-Website zugewiesen ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-39031. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
exl-id: 6250c6f6-b74b-4713-a704-d252270693d4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-39031: Hinzufügen nicht zugewiesener Produkte zum Warenkorb über GraphQL möglich

Der MDVA-39031 Patch löst das Problem, dass das Hinzufügen eines Produkts zum Warenkorb über GraphQL möglich ist, auch wenn es nicht der Ziel-Website zugewiesen ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 installiert ist. Die Patch-ID lautet MDVA-39031. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Hinzufügen eines Produkts zum Warenkorb über GraphQL ist auch dann möglich, wenn es nicht der Ziel-Website zugewiesen ist.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine sekundäre Website.
1. Erstellen Sie ein Produkt und weisen Sie es der primären Website zu.
1. Erstellen Sie mit GraphQL einen leeren Warenkorb für die sekundäre Website.

   <pre>
    <code class="language-graphql">
    mutation&lbrace;
     createEmptyCart
    &rbrace;
    </code>
    </pre>

   Mit Kopfzeilen wie:

   <pre>
    <code class="language-graphql">
    &lbrace;
      "Store":"en_au"
    &rbrace;
    </code>
    </pre>

1. Fügen Sie das der primären Website zugewiesene Produkt zum Warenkorb auf der sekundären Website hinzu.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      addProductsToCart(
          cartId: "XHrUN2nJ37OqDByhtL0VC8OxYsEZs41c"
          cartItems: &lbrack;
            &lbrace;
              quantity: 1
              sku: "p1"
            &rbrace;
          &rbrack;
        ) &lbrace;
          cart &lbrace;
           items &lbrace;
            product &lbrace;
              name
              sku
            &rbrace;
            quantity
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

   Kopfzeilen

   <pre>
    <code class="language-graphql">
    &lbrace;
      "Store":"en_au"
    &rbrace;
    </code>
    </pre>

<u>Erwartete Ergebnisse</u>:

Das Produkt wird nicht zum Warenkorb hinzugefügt, da es nicht dem in der Kopfzeile definierten Store zugewiesen wurde.

<u>Tatsächliche Ergebnisse</u>:

Das Produkt wurde erfolgreich zum Warenkorb hinzugefügt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
