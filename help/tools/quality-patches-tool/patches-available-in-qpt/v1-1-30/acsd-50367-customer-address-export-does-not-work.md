---
title: 'ACSD-50367: Der Export von Kundenadressen funktioniert nicht mit dem Attribut für Mehrfachauswahl'
description: Wenden Sie den ACSD-50367-Patch an, um das Adobe Commerce-Problem zu beheben, bei dem der Export der Kundenadresse nicht funktioniert, wenn ein Attribut mit mehreren ** „Kundenadresse“** ohne Werte erstellt wird.
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
exl-id: 3f33a590-e7c2-424e-aacd-2df7ab893c3e
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
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
source-wordcount: '414'
ht-degree: 0%
---
# ACSD-50367: Export der Kundenadresse funktioniert nicht

Mit dem Patch ACSD-50367 wird das Problem behoben, dass der Export von Kundenadressen nicht funktioniert, wenn ein Attribut mit mehreren **`Customer Address`** ohne Werte erstellt wird. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30 installiert ist. Die Patch-ID ist ACSD-50367. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Export von Kundenadressen funktioniert nicht, wenn ein Attribut mit mehreren **`Customer Address`** ohne Werte erstellt wird.

<u>Voraussetzungen</u>:

Erstellen Sie einen Kunden mit einer Adresse.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie unter **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]** ein **`Customer Address`** mit Mehrfachauswahl.
1. Wechseln Sie zu **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** und wählen Sie **`Customer Address`** Entitätstyp aus.
1. Exportieren Sie die Kundenadressen. Sie werden sehen, dass nichts exportiert wird.
1. Löschen Sie das Attribut **`Customer Address`** Mehrfachauswahl und exportieren Sie die Kundenadressen erneut. Dieses Mal wird die CSV-Datei der Adressen generiert.

<u>Erwartete Ergebnisse</u>:

Die Kundenadressen können als CSV-Datei exportiert werden, wenn ein Attribut für **`Customer Address`** mit mehreren Auswahlmöglichkeiten erstellt wird.

<u>Tatsächliche Ergebnisse</u>:

Die Kundenadressen können nicht als CSV-Datei exportiert werden, wenn ein **`Customer Address`** mit Mehrfachauswahl erstellt wird.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
