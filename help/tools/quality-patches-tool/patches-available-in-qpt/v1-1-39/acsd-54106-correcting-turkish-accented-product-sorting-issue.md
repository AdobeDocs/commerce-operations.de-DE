---
title: 'ACSD-54106: Korrigieren der Schriftzeichensortierung mit türkischem Akzent in der Produktkategorie'
description: Wenden Sie den Patch ACSD-54106 an, um das Adobe Commerce-Problem zu beheben, bei dem die Sortierung von Kategorieprodukten nach Name für Zeichen mit türkischem Akzent falsch ist.
feature: Categories, Products, Search
role: Admin
exl-id: 45c8efbb-85d0-4d25-9d7e-9c41a97e80fa
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%
---
# ACSD-54106: Korrigieren der Schriftzeichensortierung mit türkischem Akzent in der Produktkategorie

Der Patch ACSD-54106 behebt das Problem, dass die Sortierung nach Produktname für Zeichen mit türkischem Akzent falsch ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.39 installiert ist. Die Patch-ID ist ACSD-54106. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4-p3

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Die Sortierung von Produkten innerhalb von Kategorien nach Namen ist bei Zeichen mit türkischem Akzent falsch.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich beim Admin Panel an.
1. Erstellen Sie einfache Produkte mit den folgenden Namen und weisen Sie sie einer beliebigen Kategorie zu:

* Benennen Sie
* Name ç
* Name D
* Name
* Name M
* Name Ö
* Name ü
* Name Y
* Z benennen

1. Navigieren Sie zur Storefront und rufen Sie die Kategorie auf, die die Produkte enthält.
1. Ändern Sie die Sortierreihenfolge in *[!UICONTROL By Name]*.

<u>Erwartete Ergebnisse</u>:

Die Produkte werden in der folgenden Reihenfolge korrekt sortiert:

* Benennen Sie
* Name ç
* Name D
* Name
* Name M
* Name Ö
* Name ü
* Name Y
* Z benennen

<u>Tatsächliche Ergebnisse</u>:

Produkte werden fälschlicherweise in der folgenden Reihenfolge sortiert:

* Benennen Sie
* Name D
* Name M
* Name Y
* Z benennen
* Name ç
* Name Ö
* Name ü
* Name

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
