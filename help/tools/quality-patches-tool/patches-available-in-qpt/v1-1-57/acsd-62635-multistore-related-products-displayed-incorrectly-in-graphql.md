---
title: 'ACSD-62635: Multi-Store-bezogene Produkte werden in [!DNL GraphQL] falsch angezeigt'
description: Wenden Sie den Patch ACSD-62635 an, um das Adobe Commerce-Problem zu beheben, bei dem Produkte, die mit mehreren Stores in Verbindung stehen, in der [!DNL GraphQL] Produktabfrage nicht ordnungsgemäß angezeigt werden.
feature: B2B
role: Admin, Developer
exl-id: 540cd37b-4dc5-42d1-a968-2989262effdd
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '417'
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
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
