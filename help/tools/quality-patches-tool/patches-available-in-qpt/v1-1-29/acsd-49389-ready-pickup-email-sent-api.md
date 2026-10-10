---
title: 'ACSD-49389: Abholbereitschafts-E-Mail, die von der API gesendet wird, wenn sie nicht abholbereit ist'
description: Wenden Sie den Patch von ACSD-49389 an, um das Problem zu beheben, dass die API eine E-Mail zur Abholung sendet, wenn die Bestellung nicht zur Abholung bereit ist.
feature: REST, Communications
role: Admin
exl-id: d1bc430a-3021-40d1-9091-db8ed9125619
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%
---
# ACSD-49389: Abholbereitschafts-E-Mail, die von der API gesendet wird, wenn sie nicht abholbereit ist

Der Patch von ACSD-49389 behebt das Problem, dass eine abholbereite E-Mail von der API gesendet wird, wenn die Bestellung nicht abholbereit ist. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29 installiert ist. Die Patch-ID ist ACSD-49389. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.7 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.0 - 2.4.6

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches`-Paket auf die neueste Version und überprüfen Sie die Kompatibilität auf der [QPT-Landingpage](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

Eine abholbereite E-Mail wird von der API gesendet, wenn die Bestellung nicht abholbereit ist.

<u>Schritte zur Reproduktion</u>:

1. Aktivieren Sie *[!UICONTROL In-Store Delivery]* Methode.
1. Erstellen Sie eine Lagerquelle mit aktiviertem Abholort.
1. Erstellen Sie einen neuen Bestand auf der Haupt-Website mit der oben erstellten Quelle.
1. Erstellen Sie ein Produkt, das dieselbe Quelle zuweist.
1. Lagermenge = 1 festlegen.
1. Sehen Sie sich das in Schritt 4 erstellte Produkt mit der *[!UICONTROL In-Store Delivery]* -Methode aus der Storefront an.
1. Rechnung für die Bestellung erstellen.
1. Stellen Sie die Menge des Produkts auf *0* ein und machen Sie es ausverkauft.
1. Posten Sie die folgende API-Anfrage:

```json
{
    "orderIds": [
        1
    ]
}
```

<u>Erwartete Ergebnisse</u>:

Abholbereitschafts-E-Mail wird nicht gesendet.

<u>Tatsächliche Ergebnisse</u>:

Die API gibt *Bestellung ist nicht abholbereit* aber die Abholbereitschafts-E-Mail wird gesendet.

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/de/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool] Veröffentlicht: Ein neues Tool zur Selbstbedienung hochwertiger Patches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) der Support-Wissensdatenbank.
* [Überprüfen Sie, ob für Ihr Adobe Commerce-Problem ein Patch verfügbar ist [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) mithilfe von im [!UICONTROL Quality Patches Tool].


Weitere Informationen zu anderen in QPT verfügbaren Patches finden Sie unter [Patches in QPT verfügbar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=de) im [!DNL Quality Patches Tool].
