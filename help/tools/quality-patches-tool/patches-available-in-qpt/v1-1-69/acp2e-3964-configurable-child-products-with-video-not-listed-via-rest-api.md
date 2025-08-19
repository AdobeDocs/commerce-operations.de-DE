---
title: 'ACP2E-3964: Konfigurierbare untergeordnete Produkte mit Video werden nicht über die REST-API aufgelistet'
description: Wenden Sie den ACP2E-3964-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem untergeordnete Produkte von konfigurierbaren Produkten mit einem -Video im -[!UICONTROL Media Gallery] nicht über die REST-API aufgeführt werden.
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f48ced28035c65db561f4700113652574d302ec9
workflow-type: tm+mt
source-wordcount: '348'
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

```
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
