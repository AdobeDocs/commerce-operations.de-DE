---
title: 'ACSD-46618: Das Produktlisten-Widget zeigt falsche zwischengespeicherte Preise für angemeldete Kunden an'
description: Wenden Sie einen Patch an, um das Adobe Commerce-Problem zu beheben, bei dem das Produktlisten-Widget falsche zwischengespeicherte Preise für einen angemeldeten Kunden anzeigt.
feature: Cache, Orders, Products
role: Admin
exl-id: fa350f84-2fe5-474b-b4fd-d6c1e8bb0f95
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
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
source-wordcount: '474'
ht-degree: 0%
---
# ACSD-46618: Das Produktlisten-Widget zeigt falsche zwischengespeicherte Preise für einen angemeldeten Kunden an

Der Patch ACSD-46618 löst das Problem, dass das Produktlisten-Widget falsche zwischengespeicherte Preise für einen angemeldeten Kunden anzeigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21 installiert ist. Die Patch-ID ist ACSD-46618. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.6 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4

**Kompatibel mit Adobe Commerce-Versionen:**
* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Patch ACSD-46618 löst das Problem, dass das Produktlisten-Widget falsche zwischengespeicherte Preise für einen angemeldeten Kunden anzeigt.

<u>Schritte zur Reproduktion</u>:

1. Wählen Sie in Adobe Commerce Admin **[!UICONTROL Stores]** und dann **[!UICONTROL Configuration]** aus, erweitern Sie **[!UICONTROL Sales]** und wählen Sie **[!UICONTROL Tax]** aus. Aktualisieren Sie die Steuereinstellungen, um Preise mit und ohne Steuern anzuzeigen.
1. **[!UICONTROL Enable Cross Border Trade]** = _Ja_.
1. Erstellen Sie eine Steuerregel, die nur für die USA gilt.
1. Fügen Sie der Startseite ein Widget hinzu, das mehr als ein Produkt enthält.
1. Erstellen Sie zwei Kunden mit einer US-Adresse und einer Nicht-US-Adresse.
1. Melden Sie sich mit dem US-Kunden über die Storefront an. Stellen Sie sicher, dass die Seite zwischengespeichert wird.
1. Beobachten Sie den im Widget „Startseite“ angezeigten Preis.
1. Melden Sie sich ab und melden Sie sich mit dem nicht amerikanischen Kunden an.

<u>Erwartete Ergebnisse</u>:

Der im Widget Startseite angezeigte Preis entspricht der Kundenadresse.

<u>Tatsächliche Ergebnisse</u>:

Das Widget „Startseite“ zeigt Preise anhand der Steuer für Nicht-US-Kunden an.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
