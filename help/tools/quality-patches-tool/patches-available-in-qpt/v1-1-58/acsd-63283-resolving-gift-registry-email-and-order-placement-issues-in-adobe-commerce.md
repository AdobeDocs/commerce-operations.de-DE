---
title: 'ACSD-63283: Beheben [!UICONTROL Gift Registry] Probleme bei E-Mail- und Bestellplatzierungen in Adobe Commerce'
description: Wenden Sie den Patch ACSD-63283 an, um das Adobe Commerce-Problem zu beheben, bei dem die Bestellung von Elementen aus dem [!UICONTROL Gift Registry] einen Ausnahmefehler verursacht und sicherstellt, [!UICONTROL Gift Registry Updates] nur die richtigen Elemente enthalten sind.
feature: Gift, Shopping Cart
role: Admin, Developer
exl-id: cff5b9e6-56ee-4df2-961a-6d90ec83c0c2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
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
source-wordcount: '455'
ht-degree: 0%
---
# ACSD-63283: Beheben [!UICONTROL Gift Registry] Probleme bei E-Mail- und Bestellplatzierungen in Adobe Commerce

Der Patch ACSD-63283 behebt das Problem, dass das Sortieren von Elementen aus dem [!UICONTROL Gift Registry] eine Ausnahme verursacht und sicherstellt, [!UICONTROL Gift Registry Updates] nur die richtigen Elemente enthalten sind. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 installiert ist. Die Patch-ID ist ACSD-63283. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

>[!NOTE]
>Dieser Patch ersetzt und erweitert den [ACSD-56280](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed.md) QPT-Patch.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p3

**Kompatibel mit Adobe Commerce-Versionen:**

Adobe Commerce (alle Bereitstellungsmethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Zwei wichtige Probleme wirken sich auf die [!UICONTROL Gift Registry] in Adobe Commerce aus:

* Wenn ein Kunde eine Bestellung für Artikel aus seinem [!UICONTROL Gift Registry] aufgibt, schlägt der Prozess aufgrund einer ausgelösten Ausnahme fehl.
* Außerdem enthält die [!UICONTROL Gift Registry Updates]-E-Mail, die an den Registrierungsbesitzer gesendet wird, fälschlicherweise Elemente aus allen Geschenkregistrierungen, anstatt die Aktualisierungen auf Elemente in der spezifischen Registrierung zu beschränken, die aktualisiert wird.

<u>Schritte zur Reproduktion</u>:

1. Erstellen Sie zwei Produkte: Produkt A und Produkt B.
1. Erstellen Sie zwei Kunden: Kunde A und Kunde B.
1. Melden Sie sich als Kunde A an und erstellen Sie ein neues [!UICONTROL Gift Registry].
1. Navigieren Sie zur Produktseite von Produkt A und fügen Sie sie zum [!UICONTROL Wishlist] hinzu. Öffnen Sie die [!UICONTROL Wishlist Page] und verschieben Sie Produkt A mithilfe von [!UICONTROL Add to Gift Registry] in die [!UICONTROL Gift Registry].
1. Melden Sie sich als Kunde B an, erstellen Sie ein neues [!UICONTROL Gift Registry] und fügen Sie Produkt B hinzu.
1. Geben Sie als Kunde B die [!UICONTROL Gift Registry] per E-Mail frei: **[!UICONTROL My Account]> [!UICONTROL Gift Registry] >[!UICONTROL Share]**.
1. Melden Sie sich als Kunde B ab.
1. Klicken Sie auf den in der E-Mail empfangenen Link. Fügen Sie Produkt B zur [!UICONTROL Cart] hinzu und geben Sie eine Bestellung auf.

<u>Erwartete Ergebnisse</u>:

Kunde B erhält die E-Mail mit aktualisierten Artikeln nur aus der Geschenkregistrierung.

<u>Tatsächliche Ergebnisse</u>:

Kunde B erhält die E-Mail mit Artikeln aus allen Geschenkregistern.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.


## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
