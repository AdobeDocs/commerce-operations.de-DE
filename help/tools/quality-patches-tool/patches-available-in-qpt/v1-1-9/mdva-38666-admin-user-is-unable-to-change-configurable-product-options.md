---
title: 'MDVA-38666: Admin-Benutzer kann konfigurierbare Produktoptionen nicht ändern'
description: Der Patch MDVA-38666 löst das Problem, dass der Administrator bzw. die Administratorin nicht in der Lage ist, konfigurierbare Produktoptionen im Warenkorb des Kunden zu ändern. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-38666. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Admin Workspace, Configuration, Products
role: Admin
exl-id: 8e72f6a4-b36f-4fe4-bc01-2254984dd512
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '517'
ht-degree: 0%
---
# MDVA-38666: Admin-Benutzer kann konfigurierbare Produktoptionen nicht ändern

Der Patch MDVA-38666 löst das Problem, dass der Administrator bzw. die Administratorin nicht in der Lage ist, konfigurierbare Produktoptionen im Warenkorb des Kunden zu ändern. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.9 installiert ist. Die Patch-ID lautet MDVA-38666. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.4-p2

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Administrator bzw. die Administratorin kann die konfigurierbaren Produktoptionen im Warenkorb des Kunden nicht ändern.

<u>Schritte zur Reproduktion</u>:

1. Legen Sie den Kundenkontobereich auf „Global“ fest.
1. Erstellen Sie zwei Websites mit Stores.
1. Erstellen Sie zwei konfigurierbare Produkte und weisen Sie sie jeder Website zu.
1. Erstellen Sie ein Kundenkonto im Frontend und melden Sie sich an.
1. Fügen Sie ein Produkt zum Warenkorb hinzu und checken Sie es aus (dies erfolgt, um die Angebots-IDs auf jeder Website zu verändern).
1. Fügen Sie ein Produkt zum Warenkorb hinzu und lassen Sie es.
1. Wechseln Sie zur zweiten Website und fügen Sie das Produkt zum Warenkorb hinzu (die gleiche Anmeldung sollte funktionieren, da der Umfang des Kundenkontos auf „global“ festgelegt ist).
1. Öffnen Sie den Kunden über die Admin Console und navigieren Sie zur Registerkarte Warenkorb .
1. Wechseln Sie den Store aus der Dropdown-Liste und versuchen Sie, die Konfiguration zu ändern.

<u>Erwartete Ergebnisse</u>:

Der Benutzer erhält ein Popup mit konfigurierbaren Optionen.

<u>Tatsächliche Ergebnisse</u>:

Es wird kein Popup-Formular angezeigt. Der/die Benutzende kann die Konfiguration nicht ändern.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
