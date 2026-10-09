---
title: 'MDVA-42341: GraphQL-Abfrage „categoryList“ filtert die Ergebnisse nicht'
description: Der Patch MDVA-42341 löst das Problem, dass die GraphQL-Abfrage „categoryList“ die Ergebnisse nicht filtert, wenn eine Anfrage die Store-Kopfzeile aufweist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42341. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: GraphQL, Categories
role: Admin
exl-id: 56b81385-6db0-4e62-8e2b-bccfc9e0a581
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%
---
# MDVA-42341: GraphQL-Abfrage „categoryList“ filtert die Ergebnisse nicht

Der Patch MDVA-42341 löst das Problem, dass die GraphQL-Abfrage „categoryList“ die Ergebnisse nicht filtert, wenn eine Anfrage die Store-Kopfzeile aufweist. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-42341. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die GraphQL-Abfrage „categoryList“ filtert die Ergebnisse nicht, wenn eine Anfrage die Store-Kopfzeile enthält.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Stammkategorie und benennen Sie sie **root2**.
1. Erstellen Sie eine zweite Website/Store/Storeview und weisen Sie **root2** dem neuen Store zu.
1. Erstellen Sie eine neue Kategorie unter Standardstammkategorie = Kategorie1.
1. Rufen Sie mithilfe einer GraphQL-Anfrage eine Kategorieliste für die zweite Website ab (verwenden Sie den Header-Store = Neu).

<pre>
<code class="language-graphql">
{
  categoryList(filters: {name: {match: "category1"}}) {
    uid
    level
    name
    breadcrumbs {
      category_uid
      category_name
      category_level
      category_url_key
    }
  }
}
</code>
</pre>

<u>Erwartete Ergebnisse</u>:

Kategorien aus der standardmäßigen Stammkategorie werden nicht als Antwort aufgelistet, da wir eine „neue“ Store-Kopfzeile verwenden.

<u>Tatsächliche Ergebnisse</u>:

Kategorien aus der Standardstammkategorie sind in den Ergebnissen verfügbar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
