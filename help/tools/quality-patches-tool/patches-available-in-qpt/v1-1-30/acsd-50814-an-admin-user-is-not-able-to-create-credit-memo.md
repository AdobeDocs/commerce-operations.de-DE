---
title: 'ACSD-50814: Der Administrator kann keine Gutschrift erstellen'
description: Wenden Sie den ACSD-50814 Patch an, um das Adobe Commerce-Problem zu beheben, bei dem ein Administrator bzw. eine Administratorin keine Gutschrift erstellen kann.
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: 87ee7166-7492-4948-9a85-a183ecf54fa7
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 3%
---
# ACSD-50814: Der Administrator kann keine Gutschrift erstellen

Mit dem Patch ACSD-50814 wird das Problem behoben, dass ein Administrator bzw. eine Administratorin keine Gutschrift erstellen kann. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID ist ACSD-50814. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Ein Administrator bzw. eine Administratorin kann keine Gutschrift erstellen.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie im Adobe Commerce Admin zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping methods]** > **[!UICONTROL Free shipping]** und legen Sie **[!UICONTROL Enable free shipping]** auf *[!UICONTROL Yes]* fest
1. Wechseln Sie erneut zu **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]**, erweitern Sie die Berechnungseinstellungen und legen Sie Folgendes fest:
   * [!UICONTROL Shipping prices] = [!UICONTROL Including tax]
   * [!UICONTROL Enable cross border trade] = [!UICONTROL No]
1. Erweitern Sie die Einstellungen für die Preisanzeige und legen Sie die [!UICONTROL Display shipping prices] = [!UICONTROL Including tax] fest.
1. Erweitern Sie [!UICONTROL Orders], [!UICONTROL Invoices], [!UICONTROL Credit memo] Anzeigeeinstellungen und legen Sie [!UICONTROL Display shipping amount] = [!UICONTROL Including tax] fest.
1. Löschen von Caches.
1. Bestellen Sie in der Storefront.
1. Erstellen Sie eine Rechnung für die Bestellung im Administrator-Bereich.
1. Erstellen Sie eine Gutschrift.

<u>Erwartete Ergebnisse</u>:

Die Gutschrift wird erstellt.

<u>Tatsächliche Ergebnisse</u>:

Der folgende Fehler wird ausgelöst:

*Die Seite kann aufgrund des Fehlers nicht angezeigt werden*

```text
report.CRITICAL: DivisionByZeroError: Division by zero in vendor/magento/module-sales/Model/Order/Creditmemo/Total/Tax.php:139*
```

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
