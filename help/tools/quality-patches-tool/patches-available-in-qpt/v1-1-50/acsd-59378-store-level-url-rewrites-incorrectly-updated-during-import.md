---
title: 'ACSD-59378: Neuschreibungen von [!DNL URL] auf Speicherebene werden beim Import falsch aktualisiert'
description: Wenden Sie den Patch ACSD-59378 an, um das Adobe Commerce-Problem zu beheben, bei dem [!DNL URL] auf Store-Ebene beim Import fälschlicherweise aktualisiert werden.
feature: Data Import/Export
role: Admin, Developer
exl-id: dc54d810-dcc6-42c6-a877-d00d3cf4f9a5
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
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
source-wordcount: '394'
ht-degree: 0%
---
# ACSD-59378: Neuschreibungen von [!DNL URL] auf Speicherebene werden beim Import falsch aktualisiert

Mit dem Patch ACSD-59378 wird das Problem behoben, dass die [!DNL URL]-Neuschreibungen auf Speicherebene beim Import fälschlicherweise aktualisiert werden. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50 installiert ist. Die Patch-ID ist ACSD-59378. Beachten Sie, dass dieses Problem in Adobe Commerce 2.4.7 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p5

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5x (alle Versionen von 2.4.5)

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL URL] auf Speicherebene werden beim Import fälschlicherweise aktualisiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein Produkt mit `url_key = key_default` im Bereich **Alle Store-**&quot;.
1. Legen Sie `url_key = key_store` im Bereich **Standardspeicheransicht** fest.
1. Exportieren Sie das Produkt.
1. Importieren Sie eine [!DNL CSV] Datei für dieses Produkt mit den folgenden Daten:
   * `store_view_code` Spalte ist auf *leer“*, sodass sie für den Bereich **Alle Store-**&quot; gilt.
   * `url_key` ist auf den *`key_default`* festgelegt.

<u>Erwartete Ergebnisse</u>:

[!DNL URL]-Neuschreibungen werden nur für Store-Ansichten neu generiert, für die keine überschriebenen `url_key` vorhanden sind (für die die `url_key` gilt).

<u>Tatsächliche Ergebnisse</u>:

`key_store` [!DNL URL] Neuschreibungen werden gelöscht, aber die [!DNL URL] Neuschreibungen auf der Ebene **Standardspeicheransicht** für das Produkt sind weiterhin auf *`key_store`* festgelegt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
