---
title: 'ACSD-48362: Die Standard-Versandadresse wird anstelle einer neuen verwendet.'
description: Wenden Sie den Patch ACSD-48362 an, um das Adobe Commerce-Problem zu beheben, bei dem bei einer Bestellung mit einem verhandelbaren Angebot die standardmäßige Versandadresse anstelle einer neuen verwendet wird.
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%
---
# ACSD-48362: Die Standard-Versandadresse wird anstelle einer neuen verwendet

Mit dem Patch ACSD-48362 wird das Problem behoben, dass bei einer Bestellung mit einem verhandelbaren Angebot die Standard-Versandadresse anstelle der neu hinzugefügten Adresse verwendet wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27 installiert ist. Die Patch-ID ist ACSD-48362. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die standardmäßige Lieferadresse wird anstelle der neu hinzugefügten Lieferadresse verwendet, wenn eine Bestellung mit einem verhandelbaren Angebot aufgegeben wird.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie das B2B-Angebot, indem Sie zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]** navigieren.
1. Melden Sie sich als Unternehmensbenutzer an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu.
1. Gehen Sie zur Warenkorbseite und fordern Sie ein Angebot an.
1. Gehen Sie zur Seite **[!UICONTROL My Quotes]** des Kunden und wählen Sie das soeben erstellte Angebot aus.
1. Rufen Sie den Abschnitt **[!UICONTROL Shipping Information]** der Angebotsseite des Kunden auf.
   * Klicken Sie auf **[!UICONTROL Add New Address]**, füllen Sie das Formular aus und speichern Sie die Adresse (wählen Sie weder **[!UICONTROL Use as my default billing address]** noch **[!UICONTROL Use as my default shipping address]** aus).
1. Klicken Sie auf der Angebotsseite des Kunden auf **[!UICONTROL Send for Review]**.
1. Wechseln Sie zum Adobe Commerce-Administrator als Admin-Benutzer, öffnen Sie das soeben erstellte Angebot und klicken Sie auf **[!UICONTROL Send]**.
1. Gehen Sie nun zur Angebotsseite des Kunden, aktualisieren Sie die Seite und klicken Sie auf **[!UICONTROL Proceed to Checkout]**.
1. Auf der Kaufbestätigungsseite wird in den Daten die Standard-Versandadresse angezeigt, selbst wenn die neue Versandadresse ausgewählt ist.
1. Klicken Sie auf **[!UICONTROL Continue]** und geben Sie die Bestellung auf.

<u>Erwartete Ergebnisse</u>:

Die Bestellung sollte die neue Adresse verwenden, ohne die Standardversandadresse auf der Kasse erneut auszuwählen.

<u>Tatsächliche Ergebnisse</u>:

Die Bestellung wird mit der Standard-Lieferadresse aufgegeben.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur. 

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
