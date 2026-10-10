---
title: 'ACSD-49502: Herunterladbarer Link wird nach [!DNL staging] Aktualisierung nicht korrekt aktualisiert'
description: Wenden Sie den ACSD-49502-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem der herunterladbare Link nach der Anwendung einer [!DNL staging] Aktualisierung auf das herunterladbare Produkt nicht korrekt aktualisiert wird.
feature: Staging
role: Admin
exl-id: 9bdc9a7e-4291-4438-9ba0-65fcab1f95bb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%
---
# ACSD-49502: Herunterladbarer Link wird nach [!DNL staging] Aktualisierung nicht korrekt aktualisiert

Mit dem Patch ACSD-49502 wird das Problem behoben, dass der herunterladbare Link nicht korrekt aktualisiert wird, nachdem eine [!DNL staging] Aktualisierung auf das herunterladbare Produkt angewendet wurde. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49502. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der herunterladbare Link wird nicht ordnungsgemäß aktualisiert, nachdem eine [!DNL staging] Aktualisierung auf das herunterladbare Produkt angewendet wurde.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein herunterladbares Produkt mit Link(s).
1. Kundenkonto erstellen und sich anmelden.
1. Fügen Sie das herunterladbare Produkt aus der Storefront zum Warenkorb hinzu.
1. Planen Sie im **[!UICONTROL Admin]** ein neues Update für das herunterladbare Produkt, und lassen Sie das geplante Update abschließen.
1. Schließe die Bestellung auf der Storefront ab.

<u>Erwartete Ergebnisse</u>:

Herunterladbare Links bleiben bei Verwendung geplanter Updates erhalten, während sich zuvor hinzugefügte Produkte im Warenkorb befinden.

<u>Tatsächliche Ergebnisse</u>:

Herunterladbare Links fehlen sowohl auf der *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) des Kunden als auch auf der Bestellansichtsseite im **[!UICONTROL Admin]**.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
