---
title: 'ACSD-55231: Fehler „SKU nicht gefunden“ bei Verwendung der Schnellbestellungsfunktion'
description: Wenden Sie den ACSD-55231-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem der Fehler *'Die SKU wurde nicht im Katalog gefunden'* auftritt, wenn Sie versuchen, mithilfe der Schnellbestellungsfunktion ein Produkt zum Warenkorb hinzuzufügen.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: f0a04773-7395-4945-a72b-5a6a018bc94e
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
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
source-wordcount: '519'
ht-degree: 0%
---
# ACSD-55231: Fehler „SKU nicht gefunden“ bei Verwendung der Schnellbestellungsfunktion

Mit dem Patch ACSD-55231 wird das Problem behoben, bei dem *Fehler „Die SKU wurde nicht im Katalog gefunden“*, wenn versucht wird, mithilfe der Schnellbestellungsfunktion ein Produkt zum Warenkorb hinzuzufügen. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.44 installiert ist. Die Patch-ID ist ACSD-55231. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Das *der SKU wurde beim Suchen nach Produkten, die mit der Schnellbestellungsfunktion zum Warenkorb hinzugefügt werden können, nicht im* gefunden.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie Adobe Commerce mit B2B-Modulen.
1. Navigieren Sie zu **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** und legen Sie Folgendes fest:
   * **[!UICONTROL Enable company]**: *Ja*
   * **[!UICONTROL Enable Shared Catalog]**: *Ja*
   * **[!UICONTROL Enable Quick Order]**: *Ja*
1. Speichern Sie die obige Konfiguration.
1. Gehen Sie zu **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** und erstellen Sie einen neuen freigegebenen Katalog.
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** und erstellen Sie einen neuen Kunden:
   * Wählen Sie im Feld Gruppe den kürzlich erstellten freigegebenen Katalog aus und setzen Sie *[!UICONTROL Allow remote shopping assistance]* auf *Ja*.
1. Generieren Sie ein einfaches Produkt mit SKU *p12*, verknüpfen Sie es mit der Kategorie *c1* und wählen Sie dann im [!UICONTROL Product in Shared Catalog] Abschnitt den neu erstellten freigegebenen Katalog aus.
1. Durchgang:

   ```shell
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Aktualisieren Sie die Administratorseite.
1. Navigieren Sie zu **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** und bearbeiten Sie den zuvor erstellten Kunden.
1. Klicken Sie auf **[!UICONTROL Login as customer]**.
1. Gehe zu **[!UICONTROL Quick order]**.
1. Suchen Sie die *p12* SKU und klicken Sie auf die **[!UICONTROL Product Suggestion]**.
1. Fügen Sie dieses Produkt in den Warenkorb und geben Sie die Bestellung auf.
1. Kehren Sie zu **[!UICONTROL Quick Order]** zurück, suchen Sie *SKU* p12 erneut und klicken Sie auf **[!UICONTROL Product Suggestion]**.

<u>Erwartete Ergebnisse</u>:

Sie können das Produkt mit der Funktion „Schnellbestellung“ zum Warenkorb hinzufügen.

<u>Tatsächliche Ergebnisse</u>:

Sie können das Produkt nicht mit der Schnellbestellungsfunktion zum Warenkorb hinzufügen und erhalten *Die SKU wurde bei der Suche nach der Produkt-SKU nicht* Katalogfehler gefunden.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
