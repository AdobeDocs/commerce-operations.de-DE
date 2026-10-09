---
title: 'MDVA-42520: Doppelter Steuersatz bei Verwendung von „Grenzüberschreitenden Handel ermöglichen“'
description: Der MDVA-42520 Patch behebt das Problem, dass der Steuersatz zweimal angewendet wird, wenn die **Grenzüberschreitenden Handel aktivieren** verwendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-42520. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.
feature: Catalog Management, Orders, Taxes
role: Admin
exl-id: 34c101fd-3a47-4877-8a41-ccaeaa010969
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 42e094d8-211b-5acf-b52f-d8979151ab30
    internal-label: Taxes
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%
---
# MDVA-42520: Doppelter Steuersatz bei Verwendung von „Grenzüberschreitenden Handel ermöglichen“

Der MDVA-42520 Patch behebt das Problem, dass der Steuersatz zweimal angewendet wird, wenn die **Grenzüberschreitenden Handel aktivieren** verwendet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.11 installiert ist. Die Patch-ID lautet MDVA-42520. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.5 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Steuersatz wird zweimal angewendet, wenn der **Grenzüberschreitenden Handel ermöglichen** verwendet wird.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren **Firma**, **Freigegebener Katalog** und **Zitat**
1. Konfigurieren Sie Steuern entsprechend dem Screenshot. Stellen Sie sicher, dass Sie **Grenzüberschreitenden Handel“**.

   ![Seite „Einstellungen für die Steuerkonfiguration“ mit Optionen für den grenzüberschreitenden Handel und Tarifberechnungen](/help/assets/tools/tax_settings_1.png){width="700"}

1. Erstellen Sie einen Steuersatz für Deutschland (10 %).
1. Erstellen Sie eine Steuerregel, um den Steuersatz anzuwenden.
1. Erstellen Sie eine Firma und einen benutzerdefinierten freigegebenen Katalog.
1. Erstellen Sie ein Produkt mit einem Preis von 100 und nehmen Sie es in den benutzerdefinierten freigegebenen Katalog mit einem Preisnachlass von 20 % auf.
1. Erstellen Sie einen Kunden mit einer deutschen Adresse und weisen Sie ihn dem Unternehmen zu.
1. Fügen Sie der Karte als Kunde 10 Produkte hinzu.
1. Gehen Sie zum Warenkorb und fordern Sie ein Angebot an.
1. Öffnen Sie dieses Angebot im Backend und versuchen Sie, einen zusätzlichen Rabatt von 10 % hinzuzufügen.

<u>Erwartete Ergebnisse</u>:

Zwischensumme des Angebots (einschließlich Steuern) und Gesamtsumme des Angebots (einschließlich Steuern) = 720 USD

<u>Tatsächliche Ergebnisse</u>:

Zwischensumme des Angebots (einschließlich Steuern) und Gesamtsumme des Angebots (einschließlich Steuern) = 649,50 US-Dollar.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
