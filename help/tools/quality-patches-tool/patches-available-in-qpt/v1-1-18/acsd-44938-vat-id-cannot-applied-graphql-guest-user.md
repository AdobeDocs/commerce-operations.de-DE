---
title: 'ACSD-44938: VAT_ID kann bei der Anfrage  [!DNL GraphQL]  Gastbenutzers nicht angewendet werden'
description: Der Patch ACSD-44938 behebt das Problem, dass „VAT_ID“ in einer Anfrage  [!DNL GraphQL]  Gastbenutzers nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID ist ACSD-44938. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.
feature: Admin Workspace, GraphQL
role: Admin
exl-id: 62d36c27-545a-4c32-be69-a92e4b3ca2ca
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-44938: VAT_ID kann in [!DNL GraphQL] Anfrage für Gastbenutzer nicht angewendet werden

Mit dem Patch ACSD-44938 wird das Problem behoben, dass die `VAT_ID` in einer [!DNL GraphQL]-Anfrage für einen Gastbenutzer nicht angewendet werden kann. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 installiert ist. Die Patch-ID ist ACSD-44938. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

`VAT_ID` kann nicht auf eine [!DNL GraphQL] für einen Gastbenutzer angewendet werden.

<u>Schritte zur Reproduktion</u>:

1. Befolgen Sie die Schritte, die im [[!DNL GraphQL] Tutorial](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in unserer Entwicklerdokumentation erwähnt werden, um einen Gästekarton zu erstellen.
1. Versuchen Sie, mithilfe von [!DNL GraphQL] `VAT_ID` für den Gastbenutzer anzuwenden.

<u>Erwartete Ergebnisse</u>:

`VAT_ID` kann auf dieselbe Weise angewendet werden wie für einen registrierten Kunden. Siehe [`createCustomerAddress` Mutation](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/create-address/)-Artikel in unserer Entwicklerdokumentation.

<u>Tatsächliche Ergebnisse</u>:

`VAT_ID` kann nicht auf einen Gastbenutzer angewendet werden, der [!DNL GraphQL] verwendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=de) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum [!DNL Quality Patches Tool] finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](https://experienceleague.adobe.com/de/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
