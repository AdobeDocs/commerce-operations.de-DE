---
title: 'ACSD-47520: Kunden verlieren Bonuspunkte, wenn eine Gutschrift erstellt wird'
description: Wenden Sie den ACSD-47520 Patch an, um das Problem in Adobe Commerce zu beheben, bei dem Kunden Prämienpunkte verlieren, wenn eine Gutschrift erstellt wird.
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
exl-id: 09104451-e9f0-4ddb-b019-8aa34630edb9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%
---
# ACSD-47520: Kunden verlieren Bonuspunkte, wenn eine Gutschrift erstellt wird

Der Patch von ACSD-47520 behebt das Problem, dass Kunden Prämienpunkte verlieren, wenn eine Gutschrift erstellt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25 installiert ist. Die Patch-ID ist ACSD-47520. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Kunden verlieren Bonuspunkte, wenn eine Gutschrift erstellt wird.

<u>Schritte zur Reproduktion</u>:

1. Gehen Sie zu Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Ändern Sie die Einstellung:
   * **[!UICONTROL Enable Reward Points Functionality]** = _Ja_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Ja_
   * **[!UICONTROL Customers May See Reward Points History]** = _Ja_
   * **[!UICONTROL Refund Reward Points Automatically]** = _Nein_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Ja_
1. Gehen Sie zu Admin > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** und klicken Sie auf **[!UICONTROL Add New Rate]**.
1. Fügen Sie eine neue Rate (1:1) hinzu und leeren Sie den Cache.
1. Erstellen Sie einen Kunden und fügen Sie diesem Konto 10 Prämienpunkte hinzu.
1. Gehen Sie zu Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** und wählen Sie den im vorherigen Schritt erstellten Kunden aus.
1. Wählen Sie ein Produkt aus, dessen Preis höher ist als die Prämienpunkte.
1. Bestellung über eine beliebige Zahlungsmethode und die Belohnungspunkte.
1. Rechnung für die Bestellung erstellen.
1. Erstellen Sie eine Gutschrift, erstatten Sie jedoch nicht die Belohnungspunkte.

<u>Erwartete Ergebnisse</u>:

* Der Administrator kann die Prämienpunkte zurückerstatten.

* Der Bestellstatus wird geschlossen.

<u>Tatsächliche Ergebnisse</u>:

* Es gibt keine Möglichkeit, die Belohnungspunkte zurückzuerstatten.

* Der Bestellstatus ist **[!UICONTROL Completed]**.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
