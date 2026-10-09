---
title: 'ACSD-48204: Die Katalogpreisregel, die auf dem Attribut *Ja/Nein* erstellt wurde, berücksichtigt den ausgewählten Umfang nicht.'
description: Wenden Sie den Patch ACSD-48204 an, um das Adobe Commerce-Problem zu beheben, bei dem die auf dem Attribut „Ja/Nein“ erstellte Katalogpreisregel den ausgewählten Bereich nicht berücksichtigt.
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
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
source-wordcount: '488'
ht-degree: 2%
---
# ACSD-48204: Katalogpreisregel, die auf dem Attribut *Ja/Nein* erstellt wurde, berücksichtigt den ausgewählten Umfang nicht.

Der Patch ACSD-48204 behebt das Problem, dass die auf der Grundlage des Attributs *Ja/Nein* erstellte Katalogpreisregel den ausgewählten Umfang nicht berücksichtigt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28 installiert ist. Die Patch-ID ist ACSD-48204. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Katalogpreisregel, die auf dem Attribut *Ja/Nein* erstellt wurde, berücksichtigt den ausgewählten Umfang nicht.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Websites (Standard und W2).
1. Erstellen Sie ein Produktattribut vom Typ *Ja/Nein*.
   * [!UICONTROL Default value] = [!UICONTROL No] festlegen
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Erstellen Sie ein konfigurierbares Produkt basierend auf einem beliebigen Attribut mit zwei Varianten (V1 und V2).
   * Fügen Sie das Attribut *Ja/Nein* zum konfigurierbaren Variantenattribut hinzu
   * Legen Sie für eine der Varianten (V1) den Wert auf der nicht standardmäßigen Website (W2) auf *[!UICONTROL Yes]* fest
1. Erstellen Sie eine Katalogregel:
   * Auf beide Websites angewendet
   * Bedingung: *Ja/Nein* Attributwert ist *[!UICONTROL Yes]*
   * Rabatt = 50 %
1. Öffnen Sie das konfigurierbare Produkt auf der nicht standardmäßigen -Website (W2).
1. Überprüfen Sie, ob auf die Variante V1 der Rabatt von 50 % angewendet wurde.
1. Öffnen Sie die V1-Variante in der Adobe Commerce Admin.
   * Zur Standard-Website wechseln
   * Keine Änderungen vornehmen und das Produkt speichern
1. Aktualisieren Sie die konfigurierbare Seite mit der Produkt-Storefront.

<u>Erwartete Ergebnisse</u>:

Für die Variante V1 gilt weiterhin der Rabatt von 50 %, da keine Änderungen vorgenommen wurden.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt verschwindet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
