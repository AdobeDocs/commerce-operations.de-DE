---
title: 'MDVA-37115: Auf der Produktseite wird „Nur noch 0“ angezeigt'
description: Der MDVA-37115 Patch löst das Problem, dass der unnötige *Nur 0 verbleibende* Hinweis auf der konfigurierbaren Produktseite angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-37115. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.
feature: Configuration, Products, Orders
role: Admin
exl-id: ba94b2fd-6a7d-4194-afd8-798854431b57
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%
---
# MDVA-37115: Auf der Produktseite wird „Nur noch 0“ angezeigt

Der MDVA-37115 Patch löst das Problem, dass der unnötige *Nur 0* auf der konfigurierbaren Produktseite angezeigt wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2 installiert ist. Die Patch-ID lautet MDVA-37115. Beachten Sie, dass das Problem in Adobe Commerce 2.4.3 behoben wurde.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungstypen) 2.4.2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungstypen) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Auf der konfigurierbaren Produktseite wird ein unnötiger *Nur noch 0*-Hinweis angezeigt.

<u>Voraussetzungen</u>:

Inventarmodule sind installiert.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie ein konfigurierbares Produkt mit wenigen Optionen.
1. Zum Frontend gehen.
1. Öffnen Sie die konfigurierbare Produktseite und wählen Sie eine beliebige Option aus.

<u>Erwartete Ergebnisse</u>:

Auf *Produktseite wird* Hinweis „Nur noch 0“ angezeigt.

<u>Tatsächliche Ergebnisse</u>:

*Nur noch 0* Hinweis wird auf der Produktseite angezeigt.

## Patch anwenden

Verwenden Sie je nach Bereitstellungstyp die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [Überprüfen Sie mit dem Quality Patches Tool, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie im Abschnitt [Patches in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
