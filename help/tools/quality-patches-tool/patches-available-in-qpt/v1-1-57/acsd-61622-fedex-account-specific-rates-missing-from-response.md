---
title: 'ACSD-61622: In der REST-API-Antwort fehlen [!DNL FedEx] kontospezifische Raten'
description: Wenden Sie den Patch ACSD-61622 an, um das Adobe Commerce-Problem zu beheben, bei dem in der REST-API-Antwort [!DNL FedEx] kontospezifische Tarife fehlen.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 59e33dc4-3f9b-4590-95b6-e98c77e750ee
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
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
source-wordcount: '402'
ht-degree: 0%
---
# ACSD-61622: In der REST-API-Antwort fehlen [!DNL FedEx] kontospezifische Raten

Mit dem Patch ACSD-61622 wird das Problem behoben, dass in der REST-API-Antwort [!DNL FedEx's] kontospezifische Raten fehlen. Er fügt den Anfragetyp &quot;`ACCOUNT`&quot; zur REST-API-Anfrage hinzu, die von Adobe Commerce an [!DNL FedEx] gesendet wird und eine Antwort zurückgibt, die der SOAP-API-Antwort ähnelt. Dieser Patch ist verfügbar, wenn [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 installiert ist. Die Patch-ID ist ACSD-61622. Beachten Sie, dass das Problem voraussichtlich in Adobe Commerce 2.4.8 behoben wird.

## Betroffene Produkte und Versionen

**Der Patch wird für die Adobe Commerce-Version erstellt:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p5

**Kompatibel mit Adobe Commerce-Versionen:**

* Adobe Commerce (alle Bereitstellungsmethoden) 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>Der Patch könnte mit neuen [!DNL Quality Patches Tool]-Versionen auch für andere Versionen gelten. Um zu überprüfen, ob der Patch mit Ihrer Adobe Commerce-Version kompatibel ist, aktualisieren Sie das `magento/quality-patches` auf die neueste Version und überprüfen Sie die Kompatibilität auf der Seite [[!DNL Quality Patches Tool]: Nach Patches suchen](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Verwenden Sie die Patch-ID als Suchbegriff, um den Patch zu finden.

## Problem

[!DNL FedEx's] der REST-API-Antwort fehlen kontospezifische Raten.

<u>Schritte zur Reproduktion</u>:

1. Installieren Sie eine neue Adobe Commerce-Instanz.
1. Erstellen Sie ein einfaches Produkt mit einem Gewicht von 5 lbs.
1. Konfigurieren von [!DNL FedEx] für die REST-API.
1. Aktivieren Sie [!DNL FedEx] Versandmethode und löschen Sie den Cache.
1. Beobachten der Protokolldatei starten: `var/log/shipping.log`
1. Fügen Sie ein einfaches Produkt zum Warenkorb hinzu und gehen Sie an der Kasse zur Versandseite. Beispiel für Kundendaten:

   * Postleitzahl: 58601
   * Namen: John Doe
   * Anschrift: 196 Eulalia Burg
   * Land: USA
   * Bundesstaat: North Dakota
   * Telefonnummer: 187-563-3627

<u>Erwartete Ergebnisse</u>:

`PAYOR_ACCOUNT_PACKAGE` sind in der REST-API-Antwort verfügbar, ähnlich wie in SOAP-API-Antworten.

<u>Tatsächliche Ergebnisse</u>:

In der Antwort sind nur `PAYOR_LIST_PACKAGE` Tarife verfügbar, d. h. es gibt keine ausgehandelten (Konto-)Tarife von [!DNL FedEx].

## Patch anwenden

Verwenden Sie je nach Bereitstellungsmethode die folgenden Links, um einzelne Patches anzuwenden:

* Adobe Commerce oder Magento Open Source On-Premise: [[!DNL Quality Patches Tool] > Nutzung](/help/tools/quality-patches-tool/usage.md) im [!DNL Quality Patches Tool].
* Adobe Commerce in Cloud-Infrastruktur: [Upgrades und Patches > Patches anwenden](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) im Handbuch zu Commerce in Cloud-Infrastruktur.

## Verwandtes Lesen

Weitere Informationen zu [!DNL Quality Patches Tool] finden Sie unter:

* [[!DNL Quality Patches Tool]: Ein Self-Service-Tool für hochwertige Patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) im Tools-Handbuch.
