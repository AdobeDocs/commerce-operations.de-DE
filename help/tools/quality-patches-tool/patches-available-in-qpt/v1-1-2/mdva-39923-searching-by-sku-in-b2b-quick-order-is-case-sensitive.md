---
title: 'MDVA-39923: Bei der Suche nach SKU in der B2B-Schnellbestellungsfunktion wird zwischen Groß- und Kleinschreibung unterschieden'
description: Der Patch MDVA-39923 behebt das Problem, dass Kunden einen Fehler erhalten, wenn sie die Bestellung nach SKU in der B2B-Schnellbestellungsfunktion mit einer anderen Groß-/Kleinschreibung als der durchsuchen, mit der der Name gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39923. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: B2B, Catalog Management, Orders, Search
role: Admin
exl-id: 9bed5615-b398-42f5-8313-ae2acca59155
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '514'
ht-degree: 0%
---
# MDVA-39923: Bei der Suche nach SKU in der B2B-Schnellbestellungsfunktion wird zwischen Groß- und Kleinschreibung unterschieden

Der Patch MDVA-39923 behebt das Problem, dass Kunden einen Fehler erhalten, wenn sie die Bestellung nach SKU in der B2B-Schnellbestellungsfunktion mit einer anderen Groß-/Kleinschreibung als der durchsuchen, mit der der Name gespeichert wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-39923. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1-p1

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Bei der Suche nach SKU in der B2B-Schnellbestellungsfunktion wird zwischen Groß- und Kleinschreibung unterschieden und ein Fehler angezeigt, wenn eine andere Groß-/Kleinschreibung als die verwendet wird, mit der die SKU gespeichert wird.

<u>Voraussetzungen</u>:

B2B-Module werden installiert.

<u>Schritte zur Reproduktion</u>:

1. Melden Sie sich bei Admin an und gehen Sie zu **Stores** > **Konfiguration** > **B2B**.
1. Aktivieren Sie **Freigegebener Katalog** und **Schnellbestellung**.
1. Erstellen eines Produkts mit SKU in Großbuchstaben, z. B. TEST20-1234
1. Zuweisen eines erstellten Produkts zum **freigegebenen Katalog**.
1. Melden Sie sich als Kunde an und klicken Sie auf **Schnellbestellung**.
1. Geben Sie die SKU in Kleinbuchstaben ein, z. B. test20-1234.

<u>Erwartete Ergebnisse</u>:

Das Produkt sollte unabhängig vom verwendeten Fall gefunden werden.

<u>Tatsächliche Ergebnisse</u>:

Die folgende Fehlermeldung wird empfangen: *1 Produkt(e) erfordern Ihre Aufmerksamkeit*.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
