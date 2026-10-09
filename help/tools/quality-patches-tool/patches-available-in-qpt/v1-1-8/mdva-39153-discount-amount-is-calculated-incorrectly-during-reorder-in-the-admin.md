---
title: 'MDVA-39153: Rabattbetrag wird bei der Neubestellung im Admin falsch berechnet'
description: Der Patch MDVA-39153 behebt das Problem, dass der Rabattbetrag bei der Neuanordnung in der Admin-Liste falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-39153. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
exl-id: e8fe58ca-1218-4e76-b5fb-c7f935029cd2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
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
source-wordcount: '511'
ht-degree: 0%
---
# MDVA-39153: Rabattbetrag wird bei der Neubestellung im Admin falsch berechnet

Der Patch MDVA-39153 behebt das Problem, dass der Rabattbetrag bei der Neuanordnung in der Admin-Liste falsch berechnet wird. Dieser Patch ist verfügbar, wenn das [Quality Patches Tool (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.8 installiert ist. Die Patch-ID lautet MDVA-39153. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.4 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>Der Patch könnte mit neuen Versionen des Quality Patches Tool auf andere Versionen anwendbar werden. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Der Rabattbetrag wird bei der Neubestellung in der Admin falsch berechnet.

<u>Schritte zur Reproduktion</u>:

1. Navigieren Sie zu **Admin** > **Stores** > **Konfiguration** > **Verkauf** > **Steuern**.
1. Aktivieren Sie die Steuer für den Versand, indem Sie die Steuer im Warenkorb anzeigen.
1. Aktivieren und konfigurieren Sie die Versandmethode „Tabellenrate“ ($15).
1. Erstellen Sie eine Steuerregel für den integrierten Steuersatz (für CA).
1. Erstellen Sie eine Warenkorb-Preisregel mit einem festen Rabatt von 5 USD, der auf den gesamten Warenkorb und den Versandbetrag angewendet wird.
1. Fügen Sie ein Produkt mit einem Preis von $12 in den Warenkorb und gehen Sie zur Seite Warenkorb .
1. Wenden Sie den Rabatt auf den Warenkorb an.
1. Die Versandmethode im Abschnitt „Schätzungen“ auf „Pauschale“ setzen.
1. Gehen Sie durch den Checkout bis zu den Überprüfungsschritten (geben Sie die Bestellung nicht auf).
1. Gehen Sie auf die Homepage und dann zurück zum Warenkorb.
1. Ändern Sie die Versandart im Abschnitt „Schätzungen“ in „Tabellensatz“.

<u>Erwartete Ergebnisse</u>:

Der Rabatt bleibt gleich - $5.

<u>Tatsächliche Ergebnisse</u>:

Der Rabatt beträgt $6,31.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zum Quality Patches Tool finden Sie unter:

* [Quality Patches Tool veröffentlicht: ein neues Tool zur Selbstbedienung hochwertiger Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in der Support-Wissensdatenbank.
* [Überprüfen Sie im [!DNL Quality Patches Tool]-Handbuch, ob für Ihr Adobe Commerce-Problem ein Patch ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) Quality Patches Tool verfügbar ist.

Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [[!DNL Quality Patches Tool]: Suchen nach Patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) im [!DNL Quality Patches Tool].
