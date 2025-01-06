---
title: 'ACSD-62635: Multi-Store-bezogene Produkte werden in falsch angezeigt [!DNL GraphQL]'
description: Wenden Sie den ACSD-62635-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte, die mit mehreren Stores verbunden sind, in der Produktabfrage nicht  [!DNL GraphQL]  angezeigt werden.
feature: B2B
role: Admin, Developer
source-git-commit: 8e6f6590dbed43eb8ce75b694a05ee951b538814
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-62635: Multi-Store-bezogene Produkte werden in [!DNL GraphQL] falsch angezeigt

Mit dem Patch ACSD-62635 wird das Problem behoben, dass Produkte, die sich auf mehrere Stores beziehen, in der [!DNL GraphQL] Produktabfrage nicht ordnungsgemäß angezeigt werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57 installiert ist. Die Patch-ID ist ACSD-62635. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Wenn B2B aktiviert ist, gibt [!DNL GraphQL] Anfrage alle zugehörigen Produkte von allen Websites zurück, auch wenn in der Anfrage ein Store-Ansichtsbereich verwendet wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Websites, Stores und Store-Ansichten.
1. Erstellen Sie die folgenden einfachen Produkte:
   * Eine Hauptversion mit SKU *product1*, die allen Websites zugewiesen ist
   * Eins nur zugewiesen zu *Website 1*
   * Eins nur zugewiesen zu *Website 2*
   * Eins zugewiesen sowohl *Website 1* als auch *Website 2*
1. Fügen Sie alle Produkte als mit „product1 *verbunden*.
1. Aktivieren Sie [!UICONTROL B2B] und [!UICONTROL Shared Catalog].
1. Fügen Sie alle Produkte zum standardmäßigen freigegebenen Katalog hinzu.
1. Senden Sie [!DNL GraphQL] Anfrage zum Abrufen von *product1* und den zugehörigen Produkten mit dem Store-Code *Website 1* in der Kopfzeile.

<u>Erwartete Ergebnisse</u>:

Die Antwort enthält nur verwandte Produkte von den Websites, die dem im Anfrage-Header gesendeten Store-Code entsprechen.

<u>Tatsächliche Ergebnisse</u>:

Die Antwort enthält alle zugehörigen Produkte von allen Websites, unabhängig vom in der Anfrage angegebenen Store-Code.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
