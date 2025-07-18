---
title: 'ACSD-46213: Anforderung für Kategoriestruktur auf 20 Kategorien beschränkt'
description: 'Mit dem Patch ACSD-46213 wird das Problem behoben, dass die Kategoriestrukturanforderung auf 20 Kategorien beschränkt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19 installiert ist. Die Patch-ID ist ACSD-46213. '
feature: Categories
role: Admin
exl-id: 2cd4b102-db52-424f-9a7f-d775cb2b2c49
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# ACSD-46213: Anforderung für Kategoriestruktur auf 20 Kategorien beschränkt

Mit dem Patch ACSD-46213 wird das Problem behoben, dass die Kategoriestrukturanforderung auf 20 Kategorien beschränkt ist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19 installiert ist. Die Patch-ID ist ACSD-46213.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.


## Problem

Die Kategoriestruktur-Anfrage ist auf 20 Kategorien beschränkt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine Kategorie unter der Stammkategorie .
1. Erstellen Sie unter der in Schritt 1 erstellten Stammkategorie 24 Unterkategorien.
1. Führen Sie die folgende GraphQL-Anfrage aus:

   <pre>
    <code class="language-graphql">
    &lbrace;
      categoryList(filters: { parent_id: { in: ["3"] } }) &lbrace;
        name
        level
        path
        url_path
        children &lbrace;
          id
          level
          name
          path
          url_path
          url_key
          children &lbrace;
            uid
            level
            name
            path
            url_path
            url_key
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

1. Überprüfen Sie die Ergebnisse.

<u>Erwartete Ergebnisse</u>:

Es umfasst 24 Kategorien.

<u>Tatsächliche Ergebnisse</u>:

Es werden nur 20 Kategorien angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
