---
title: 'MDVA-40175: Optionsschaltflächen werden bei der Neuanordnung nicht angezeigt'
description: Der Patch MDVA-40175 löst das Problem, dass die Optionsschaltflächen nicht angezeigt werden, wenn Benutzende versuchen, eine Neuanordnung vorzunehmen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-40175. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: Admin Workspace, Orders
role: Admin
exl-id: e84ff581-13ba-4f9f-9247-519b0b54807a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '453'
ht-degree: 0%
---
# MDVA-40175: Optionsschaltflächen werden bei der Neuanordnung nicht angezeigt

Der Patch MDVA-40175 löst das Problem, dass die Optionsschaltflächen nicht angezeigt werden, wenn Benutzende versuchen, eine Neuanordnung vorzunehmen. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10 installiert ist. Die Patch-ID lautet MDVA-40175. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Optionsschaltflächen werden im Abschnitt Zahlungs- und Versandinformationen nicht angezeigt, wenn Benutzende versuchen, eine Neuanordnung vorzunehmen.

<u>Voraussetzungen</u>:

1. Es wird ein Kundenkonto mit einer Lieferadresse und einer Rechnungsadresse erstellt.
1. Ein einfaches Produkt wird erstellt.
1. Es sind mehrere Versandmethoden konfiguriert.
1. Mindestens eine Bestellung wird erstellt.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zum Admin-Bedienfeld > **Verkauf** > **Bestellungen**.
1. Wählen Sie die erstellte Bestellung aus.
1. Klicken Sie auf **Link** Anzeigen“.
1. Klicken Sie auf **Schaltfläche „Neu**&quot;.
1. Scrollen Sie auf der Seite nach unten zum Abschnitt **Zahlungs- und Versandinformationen**.
1. Klicken Sie auf **Klicken, um die Versandart zu**.

<u>Erwartete Ergebnisse</u>:

Die Liste der Versandmethoden mit Optionsschaltflächen wird angezeigt.

<u>Tatsächliche Ergebnisse</u>:

Die Liste der Versandmethoden ohne Optionsschaltflächen wird angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
