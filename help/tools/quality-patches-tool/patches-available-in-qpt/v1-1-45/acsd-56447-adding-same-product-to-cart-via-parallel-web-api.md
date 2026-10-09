---
title: 'ACSD-56447: Das Hinzufügen desselben Produkts zum Warenkorb über die parallele Web-REST-API führt zu zwei separaten Artikeln im Warenkorb'
description: Wenden Sie den Patch ACSD-56447 an, um das Adobe Commerce-Problem zu beheben, bei dem das Hinzufügen desselben Produkts zum Warenkorb über parallele Web-REST-API-Anfragen zu zwei separaten Artikeln im Warenkorb führt.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: ef0b2ce7-74f5-47b6-a44c-bda898c444b2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '443'
ht-degree: 0%
---
# ACSD-56447: Das Hinzufügen desselben Produkts zum Warenkorb über die parallele Web-REST-API führt zu zwei separaten Artikeln im Warenkorb

Der Patch ACSD-56447 behebt das Problem, dass das Hinzufügen desselben Produkts zum Warenkorb über parallele Web-REST-API-Anfragen zu zwei separaten Artikeln im Warenkorb führt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.45 installiert ist. Die Patch-ID ist ACSD-56447. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das Hinzufügen desselben Produkts zum Warenkorb über parallele Web-REST-API-Anfragen führt zu zwei separaten Artikeln im Warenkorb.

<u>Schritte zur Reproduktion</u>:

1. Generieren Sie ein Kunden-Token für die REST-API-Aufrufanforderung mit [!DNL Postman].
1. Erstellen Sie einen Warenkorb für den Kunden.
1. Verwenden Sie das oben generierte Token, um einen leeren Warenkorb für den Kunden zu erstellen.
1. Verwenden Sie CURL, um zwei `AddProductsToCart` parallel auszuführen. Befolgen Sie die Anweisungen im Tutorial [Bestellabwicklung](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) in der Entwicklerdokumentation.

<u>Erwartete Ergebnisse</u>:

Artikel mit mehreren Mengen werden in einer Zeile angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Dieselben SKUs werden in mehreren Zeileneinträgen angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
