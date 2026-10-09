---
title: 'ACSD-55566: [!UICONTROL mergeCart]-Mutation schlägt mit internem Server-Fehler in [!DNL GraphQL] Antwort fehl'
description: Wenden Sie den Patch ACSD-55566 an, um das Adobe Commerce-Problem zu beheben, bei dem die Mutation „mergeCart“ mit einem internen Server-Fehler in [!DNL GraphQL] Antwort fehlschlägt, wenn die Quell- und die Zielkarten zusammengeführt werden, die dieselben Bundle-Elemente aufweisen.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84c6fbb9-73b3-4197-aff3-49743f0ebb2c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
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
source-wordcount: '451'
ht-degree: 0%
---
# ACSD-55566: `mergeCart`-Mutation schlägt mit internem Server-Fehler in [!DNL GraphQL] Antwort fehl

Der Patch ACSD-55566 behebt das Problem, dass die `mergeCart`-Mutation mit einem internen Server-Fehler in [!DNL GraphQL] Antwort fehlschlägt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.48 installiert ist. Die Patch-ID ist ACSD-55566. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.5.0 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

`mergeCart` Mutation schlägt mit einem internen Server-Fehler in [!DNL GraphQL] Antwort fehl, wenn die Quell- und Zielkarten zusammengeführt werden, die dieselben Bundle-Elemente enthalten.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie eine benutzerdefinierte Quelle und ein benutzerdefiniertes Lager.
1. Weisen Sie den erstellten Bestand der Haupt-Website zu.
1. Erstellen Sie ein einfaches Produkt und weisen Sie ihm die erstellte Quelle zu (qty=2).
1. Erstellen Sie ein Bundle-Produkt mit einer Option und einem untergeordneten Produkt (Produkt erstellt in Schritt 3).
1. Erstellen Sie einen Gästekorb über [!DNL GraphQL].
1. Fügen Sie ein Produktpaket hinzu, für das beide Optionen ausgewählt sind.
1. Speichern Sie die *cartID*.
1. Erstellen Sie einen Kunden und generieren Sie ein Kunden-Token.
1. Erstellen Sie einen Kundenwagen.
1. Fügen Sie dasselbe Produktpaket mit derselben Konfiguration zum Warenkorb hinzu.
1. Versuchen Sie, den Gästekorb mit dem Kundenwagen zusammenzuführen.

<u>Erwartete Ergebnisse</u>:

Der Warenkorb des Kunden enthält Produkte aus beiden Warenkörben.

<u>Tatsächliche Ergebnisse</u>:

Es wird ein interner Fehler angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
