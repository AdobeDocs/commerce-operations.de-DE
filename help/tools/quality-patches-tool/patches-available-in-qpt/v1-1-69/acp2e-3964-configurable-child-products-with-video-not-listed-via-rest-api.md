---
title: 'ACP2E-3964: Konfigurierbare untergeordnete Produkte mit Video werden nicht über die REST-API aufgelistet'
description: Wenden Sie den ACP2E-3964-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem untergeordnete Produkte von konfigurierbaren Produkten mit einem -Video im -[!UICONTROL Media Gallery] nicht über die REST-API aufgeführt werden.
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
exl-id: 61c5b97c-79aa-4ee7-96b3-70924d2c85a0
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
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
source-wordcount: '371'
ht-degree: 0%
---
# ACP2E-3964: Konfigurierbare untergeordnete Produkte mit Video werden nicht über die REST-API aufgelistet

Mit dem Patch ACP2E-3964 wird das Problem behoben, dass untergeordnete Produkte von konfigurierbaren Produkten mit einem Video im **[!UICONTROL Media Gallery]** nicht über die REST-API aufgelistet werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 installiert ist. Die Patch-ID lautet ACP2E-3964. Dieses Problem wird voraussichtlich in Adobe Commerce 2.4.9 behoben.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Untergeordnete Produkte von konfigurierbaren Produkten mit einem Video im **[!UICONTROL Media Gallery]** können nicht über die REST-API aufgelistet werden, was zu einer Fehlerantwort führt.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein neues konfigurierbares Produkt und fügen Sie ein einzelnes untergeordnetes Produkt hinzu.
1. Bearbeiten Sie das untergeordnete Produkt und fügen Sie unter **[!UICONTROL Images and Videos]** ein Video hinzu (z. B. [https://vimeo.com/1084537](https://vimeo.com/1084537)).
1. Speichern Sie das untergeordnete Produkt.
1. Senden Sie eine GET-Anfrage an den REST-API-Endpunkt, `rest/v1/configurable-products/%sku%/children` Sie ein Admin-Bearer-Token verwenden.

<u>Erwartete Ergebnisse</u>:

Die REST-API sollte die untergeordneten Produktdaten ohne Fehler zurückgeben, einschließlich der Videoinformationen im **[!UICONTROL Media Gallery]**.

<u>Tatsächliche Ergebnisse</u>:

Die REST-API gibt einen Fehler zurück:

```text
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
