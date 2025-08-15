---
title: 'ACSD-65750: [!DNL GraphQL] „route“-Abfrage gibt Produkte vom Inhaltstyp „in-products [!DNL Page Builder]  nicht in der richtigen Reihenfolge zurück'
description: Wenden Sie den ACSD-65750-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem die GraphQL-Routenabfrage Produkte zurückgibt, die nicht im Produktinhaltstyp  [!DNL Page Builder]  sind.
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 3aee28e1-1293-42d0-a62c-5021e8f75518
source-git-commit: 2d6debf4d426a0473eb77919c2307afdc77bf937
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-65750: [!DNL GraphQL] Abfrage „route“ gibt Produkte im Content-Typ „Produkte“ in [!DNL Page Builder] Reihenfolge zurück

Der Patch ACSD-65750 behebt das Problem, dass die [!DNL GraphQL] Abfrage „route“ Produkte im Inhaltstyp „Produkte“ nicht in [!DNL Page Builder] Reihenfolge zurückgibt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 installiert ist. Die Patch-ID ist ACSD-65750. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die [!DNL GraphQL] „route“-Abfrage gibt bei Verwendung des Inhaltstyps „Produkte [!DNL Page Builder]&quot; Produkte nicht in der richtigen Sortierreihenfolge zurück.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine neue Kategorie und einige Produkte im Katalog und verknüpfen Sie die Produkte mit dieser Kategorie.
1. Navigieren Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**, bearbeiten Sie die erstellte Kategorie und öffnen Sie die Registerkarte **[!UICONTROL Products in Category]** .
1. Legen Sie benutzerdefinierte **[!UICONTROL Position]** für jedes Produkt in dieser Kategorie fest.
1. Speichern Sie die Kategorie und führen Sie eine Neuindizierung aus.
1. Navigieren Sie zu **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]** und klicken Sie auf **[!UICONTROL Add New Page]**.
1. Erweitern Sie die Registerkarte **[!UICONTROL Content]** und klicken Sie dann auf **[!UICONTROL Edit with Page Builder]**.
1. Ziehen Sie ein **[!UICONTROL Row]** Element in den Inhaltsbereich und ziehen Sie dann ein **[!UICONTROL Products]** Element in die Zeile.
1. Konfigurieren Sie das Element Produkte wie folgt:
   * **[!UICONTROL Select Products By]**: *category*
   * **[!UICONTROL Category]**: *Wählen Sie die neu erstellte Kategorie aus*
   * **[!UICONTROL Sort By]**: *Position*
1. Wechseln Sie zur Registerkarte **[!UICONTROL Search Engine Optimization]** und legen Sie die **[!UICONTROL URL Key]** auf *test-widget* fest.
1. Speichern Sie die Seite.
1. Stellen Sie die folgende [!DNL GraphQL]:

```
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u>Erwartete Ergebnisse</u>:

Das System gibt Produkte in der Reihenfolge zurück, die durch ihre Kategorieposition definiert ist.

<u>Tatsächliche Ergebnisse</u>:

Das System gibt Produkte in einer Reihenfolge zurück, die nicht mit ihrer Kategorieposition in der GraphQL-Antwort übereinstimmt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
